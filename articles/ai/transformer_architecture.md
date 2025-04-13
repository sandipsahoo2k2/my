<!-- Draft -->
## How to build a multihead attention ?

Multi head attnetion is nothing but multiplying weights to different layers of a network.

```
class MultiHeadAttn(nn.Module):
    def __init__(self, embed_dim: int, num_heads: int):
        super().__init__()
        self.in_proj_k = nn.Linear(embed_dim, embed_dim)
        self.in_proj_v = nn.Linear(embed_dim, embed_dim)
        self.in_proj_q = nn.Linear(embed_dim, embed_dim)
        self.out_proj = nn.Linear(embed_dim, embed_dim)
        self.n_heads = num_heads

    def forward(self, q, k, v) -> torch.Tensor:
        from einops import rearrange
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

### What is a Transformer ?
Transformer is nothing but a MultiHeadAttn with a Positional embedding with a multi layer perceptron ( MLP ) 
MLP = LinearLayer + Relu + LinearLayer
