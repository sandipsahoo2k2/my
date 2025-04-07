## Take a Peek at my new product DeePeek

As you all know, demo day is basically a scheduled nightmare — and true to it's tradition, yesterday night was no different for me. DeepPeek 🚀 was crushing it on a 2gb-vcpu-docker-ubuntu image. I got excited to write about it but before publishing, thought to give a boost to it's core, memory and moved to a brand new cloud 4gb-dual-core-vcpu. Composed myself to see the docker fireworks and boom 🎆 in few minutes everything was up and running. I did a little smoke test with the simple deeppeek ux playground to check all facets of this RAG. Omg what went wrong ? Spent my deep nights in figuring out why the ... now sentence-transformers are failing to load ! Spent the night chasing ghosts in the system, And then — just like that — out of the blue, a tiny lib `accelerate` came for rescue - like a sign from the tech gods who inspire those who wander the nights :)

Ok let me stop my story here and share the beauty of DeepPeek. If you have not yet seen her go check this link. deeppage sounds better ? Let me know if you like this name.

What is this DeepPeek ? ([Also published at Linkedin](https://www.linkedin.com/pulse/take-deepeek-my-publichomepagechat-sandeep-sahoo-nxrme))

 - **_DeepPeek turns every web page into an interactive experience_** — help users by doing deepsearch and find what they need with AI-powered answers. 

You want to hear how did I build this ? Ok here are the nuts and bolts of DeepPeek.
![image](https://github.com/user-attachments/assets/2a53d35e-600d-4de1-9203-088b06eb101b)

1. My main goal was to use lightweight text transformers for the vector embeddings instead of using openai embeddings ( It will save some money from unnecessary extra api calls ). If you are wondering what is this embeddings ? It's simply sequence of numbers in vector format a representation for your input objects, which helps in similarity search which is the backbone of all ai/ml/rag applications.
2. Chroma db though is called the goto vector db, I found love with Redis vector store, as they found to be little faster and also easy for expiring lru indexes for the web pages. ( deeppeek gives both options to try - that's how I made smoketesting easy)
3. deepseek llm for chat completion, wanted to leverage their utc 16:30-00:30 discounted price ( gpt-4o-mini is almost equally cheap fyi ). Know that my deeppeek is free for every publichome.page users, I pay when you use :)
4. Containerize DeepPeek with Docker to simplify scaling and easier deployments.

Ok let's now see where can we use deeppeek ? 

* Every webpage right ?
* Most interesting use-case can be our confluence pages :)
* Especially news sites, linkedin pages, wikipedia's where lots of information are there in a single page.
* Can be a very very useful product for recruiting and educational institutions.
* Yesterday I was browsing the timesofindia news and looking for the trump tarifs for a specific country and my chrome plugin literally got the exact information from the highly cluttered site. ( Yes I have also published the chrome plugin, will share once approved )

![image](https://github.com/user-attachments/assets/7970a714-482c-49b0-83d5-38a50488af3c)

Do you know that deepseek doesn't provide an embeddings api yet - this was the main opportunity for me to build my own layer to use local embeddings like MiniLM-L6-v2 / MiniLM-L12-v2. jfyi you need to use the exact same embedding format for saving and retrievals. Embeddings and Chat completions ( llm integration ) are two different things hence you can use openai embeddings or any other embeddings with a llm like deepseek.

Applications :

 - Currently it's integrated with my own publichome.page web framework. 

 - Hopefully DeepPeek chrome extn will be approved and can reach everyone.

 - Look at this poem written by my father, how deeppeek is interacting with it.

![image](https://github.com/user-attachments/assets/c6e4a91c-49b7-4d61-a70a-bca906dce099)
