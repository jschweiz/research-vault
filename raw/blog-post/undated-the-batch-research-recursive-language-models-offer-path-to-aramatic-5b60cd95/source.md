---
id: undated-the-batch-research-recursive-language-models-offer-path-to-aramatic-5b60cd95
kind: blog-post
title: Recursive Language Models Offer Path To Dramatically Expand Beyond the Context Window
source_url: https://www.deeplearning.ai/the-batch/recursive-language-models-offer-path-to-aramatically-expand-beyond-the-context-window
source_name: The Batch Research
authors: []
published_at: '2026-03-27T07:07:03-07:00'
ingested_at: '2026-04-09T20:53:00.098900Z'
content_hash: 6ec43a1122bc3c04ce225dd20277e353f3f93f90954c2850fbf85f4616344ce7
identity_hash: 4a6e2fdd748e0efcb53cf248c4bec94cc6f840550649a8d6629f4ddbfb167ba1
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- language models
- context window
- recursive models
- deep learning
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/recursive-language-models-offer-path-to-aramatically-expand-beyond-the-context-window
canonical_url: https://www.deeplearning.ai/the-batch/recursive-language-models-offer-path-to-aramatically-expand-beyond-the-context-window
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T21:10:48.908356Z'
short_summary: Recursive Language Models provide a method to significantly expand beyond the limitations of the context window in language models.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
When processing long contexts, large language models often lose track of details or devolve into nonsense. Researchers reduced these effects by managing context externally.
What’s new: MIT’s Alex L. Zhang, Tim Kraska, and Omar Khattab developed [Recursive Language Models](https://arxiv.org/abs/2512.24601?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz) (RLMs) that process long prompts encountered in books, web searches, and codebases by offloading prompts to an external environment and managing them programmatically.
Key insight: A language model can process long inputs, including inputs larger than its context window, by treating input text as a persistent variable in an external programming environment. The model can write code to fetch only the necessary chunks of text. For example, it can look for keywords and retrieve the paragraphs that surround them. Writing code Iteratively enables the model to break down long-context tasks into sub-tasks before approaching the tasks as a whole.
How it works: RLMs read and manipulate tasks (a user’s prompt and associated documents) using Python code execution in a simple read-evaluate-print loop (REPL) environment. The tasks involved analyzing, understanding, or retrieving details from long documents. The model generated a program that invoked new instances of itself, or submodels, to handle each subtask and fed each instance’s output back into the root model.
- The authors built RLM systems based on Qwen3-8B (which has a 32,768-token context window), GPT-5 (400,000-token context window), and Qwen3-Coder-480B (256,000-token context window). Each system comprised a model and a custom agentic framework that read and wrote to a Python environment and called submodels.
- The RLM systems loaded task data into a Python interpreter as a variable rather than feeding it directly into the model.
- A system prompt instructed the root model to generate Python code to interact with the REPL environment and address stored tasks. For example, the model inspected the length of a prompt, found keywords, split it into logical chunks (like chapters or sections), and called a different submodel to answer questions about each chunk.
- Each submodel processed its chunk according to the root model’s instructions or questions and passed its results back to the root model.
- The system stored the submodels’ outputs as variables. The root model used these intermediate results to construct its final output.
Results: The authors compared RLMs based on Qwen3-8B, GPT-5 with medium reasoning, and Qwen3-Coder-480B to the original models using using benchmarks that involve retrieval and reasoning over documents up to 1 million tokens long. They also compared the RLMs to CodeAct agents with retrieval tools and custom agents that compacted or summarized context. The RLMs significantly outperformed both the stock models and other agentic strategies on tasks that require understanding of multiple documents, up to 11 million tokens total.
- On
[BrowseComp+](https://arxiv.org/abs/2508.06600?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz), a question-answering benchmark that requires reasoning over multiple documents, the RLM-GPT-5 (91.3 percent accuracy) outperformed GPT-5, which ran into context length limitations and was unable to produce an answer. It also outperformed the summary agent that used GPT-5 (70.5 percent accuracy). Similarly, RLM-Qwen3-Coder-480B (44.7 percent accuracy) outperformed Qwen3-Coder-480B with a summary agent (38.0 percent accuracy). RLM-Qwen3-8B (14 percent accuracy) outperformed Qwen3-8B (0 percent accuracy.) - The authors tested the models on OOLONG-PAIRS, a version of the
[OOLONG](https://arxiv.org/abs/2511.02817?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz)long-context reasoning benchmark. OOLONG-PAIRS requires aggregating paired chunks to construct a final output (for instance, “list all pairs of user IDs […] where both users have at least [a value or location]”). RLM-GPT-5 (58 percent accuracy) outperformed GPT-5 (nearly 0 percent accuracy) and retrieval and summary agents (about 0.3 percent accuracy) at 32,000 tokens of context. RLM-GPT-5 maintained approximately 50 percent accuracy even at 1 million tokens of context. RLM-Qwen3-8B (5.2 percent accuracy) outperformed Qwen3-8B (0 percent accuracy) at 32,000 tokens of context.
Why it matters: Earlier approaches often handle long contexts by using retrieval or summarization, which can lose critical details. By decomposing tasks into recursive sub-calls, a model can maintain high precision across more tokens. This method provides a blueprint for building agents that can reason coherently over numbers of tokens that far exceed a model’s input limit.
We’re thinking: An RLM pays attention only to the parts of the context it needs at any given moment. This approach seems akin to the human method of processing long documents one section at a time.
