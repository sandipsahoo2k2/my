<!-- Draft -->
## How to build a multihead attention ?

Multi head attnetion is nothing but multiplying weights to different layers of a network.

```
from einops import rearrange
class MultiHeadAttn(nn.Module):
    def __init__(self, embed_dim: int, num_heads: int):
        super().__init__()
        self.in_proj_k = nn.Linear(embed_dim, embed_dim)
        self.in_proj_v = nn.Linear(embed_dim, embed_dim)
        self.in_proj_q = nn.Linear(embed_dim, embed_dim)
        self.out_proj = nn.Linear(embed_dim, embed_dim)
        self.n_heads = num_heads

    def forward(self, q, k, v) -> torch.Tensor:
        p_q, p_k, p_v = self.in_proj_q(q), self.in_proj_k(k), self.in_proj_v(v)
        r_q = rearrange(p_q, "b m (h d) -> b h m d", h=self.n_heads)
        r_k = rearrange(p_k, "b n (h d) -> b h n d", h=self.n_heads)
        r_v = rearrange(p_v, "b n (h d) -> b h n d", h=self.n_heads)

        scores = torch.einsum("b h m d, b h n d -> b h m n", r_q, r_k)
        attn = torch.softmax(scores, dim=-1)
        result = torch.einsum("b h m n, b h n d -> b h m d", attn, r_v)
        result = rearrange(result, "b h m d -> b m (h d)")
        return self.out_proj(result)
```

- Positional embedings are used to break permutations invariance
- They encode location related information
- Advantage of using sinusoidal positional embeddings over absolute positional embeddings are because they more interpretable. There are many variants but rotary embedding is the goto embeddings that is most popular in llm because They extrapolate well to longer sequences. They are mix of sinusoidal and absolute .

Below is an example for sinosoidal embeddings.

```
class PositionalEmbedding(nn.Module):
    def __init__(self, embed_dim: int):
        super().__init__()
        self.freq = torch.exp(torch.arange(0, embed_dim, 2).float() / 2)

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        x = x[..., None:] * self.freq[None, None, :].to(x.device)
        
        return torch.cat([torch.sin(x), torch.cos(x)], dim=-1).view(x.shape[:-2], -1)

```

Vanila Multi layer perceptron can use Identity as an encoder and series of linear and relu but to predict the x, y, coordinate color we should use a better encoder which is sinosoidal e.g

```
class Rose(nn.Module):
    def __init__(self):
        super().__init__()
        self.enc = PositionalEmbedding(12) # we replaced the torch.nn.Identity() with positional embedding to better predict
        self.net = torch.nn.Sequential(
            nn.Linear(2, 256),
            nn.ReLU(),
            nn.Linear(256, 128),
            nn.ReLU(),
            nn.Linear(128, 64),
            nn.ReLU(),
            nn.Linear(64, 3),
        )

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        return self.net(self.enc(x))
    
    """
    rose tensor is input, x, y cordinate is our data to predict the color of pixel at that location
    """

```

### What is a Transformer ?
Transformer is nothing but a MultiHeadAttn with a Positional embedding with a multi layer perceptron ( MLP ) 
MLP = LinearLayer + Relu + LinearLayer

<img width="600" alt="image" src="https://github.com/user-attachments/assets/1998ca6a-2780-4f90-8897-bcc0b1336394" />

<img width="500" alt="image" src="https://github.com/user-attachments/assets/22c44677-a073-4d81-8ae1-c9580016f472" />

```
class TransformerLayer(nn.Module):
    def __init__(self, embed_dim: int, num_heads: int):
        super().__init__()
        self.attn = MultiHeadAttn(embed_dim, num_heads, batch_first=True)

        self.mlp = nn.Sequential(
            nn.Linear(embed_dim, embed_dim * 4),
            nn.ReLU(),
            nn.Linear(embed_dim * 4, embed_dim),
        )
        self.in_norm = nn.LayerNorm(embed_dim)
        self.mlp_norm = nn.LayerNorm(embed_dim)

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        x_norm = self.in_norm(x)
        x = x + self.attn(x_norm, x_norm, x_norm)[0]
        x = x + self.mlp(self.mlp_norm(x))
        return x
    
class Transformer(torch.nn.Module):
    def __init__(
        self,
        embed_dim: int = 128,
        num_heads: int = 8,
        num_layers: int = 4
    ):
        super().__init__()
        self.network = nn.Sequential(
            *[TransformerLayer(embed_dim, num_heads) for _ in range(num_layers)]
        )

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        return self.network(x)
```
