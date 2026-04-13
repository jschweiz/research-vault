---
id: 2026-04-10-the-batch-research-a-dynamic-fluids-model-appears-to-solve-transfor-c42a94ac
kind: blog-post
title: A Dynamic Fluids Model Appears To Solve Transformers’ Pixellation Problem
source_url: https://www.deeplearning.ai/the-batch/a-dynamic-fluids-model-appears-to-solve-transformers-pixellation-problem
source_name: The Batch Research
authors: []
published_at: '2026-04-10T10:57:22-07:00'
ingested_at: '2026-04-13T18:33:23.551531Z'
content_hash: 085081cceef68f12c99ee5aa58481b7526c37fe02d1bab9efaa147c3cd0e6e87
identity_hash: 532e7a8fc314cb6e446b0f05e95af3fcdb7168bf907587b842e47e39b1527e75
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/a-dynamic-fluids-model-appears-to-solve-transformers-pixellation-problem
canonical_url: https://www.deeplearning.ai/the-batch/a-dynamic-fluids-model-appears-to-solve-transformers-pixellation-problem
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-13T18:33:23.551537Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
Simulating complex physical systems through traditional numerical methods is slow and expensive, and simulations based on machine learning are usually specialized for a specific type of system, such as water in a pipe or atmosphere surrounding a planet. Researchers built a general, transformer-based model for liquids, gases, and plasmas.
What’s new: Michael McCabe and colleagues at Polymathic AI Collaboration, a multi-institution, multi-disciplinary lab for scientific AI, released [Walrus](https://arxiv.org/abs/2511.15684?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6), a 1.3 billion-parameter model that simulates how fluids move, interact, and change over time. The model is freely [available](https://github.com/PolymathicAI/walrus?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6) under an MIT license.
Key insight: Models often fail to simulate chaotic systems, which are highly sensitive to initial conditions, over long time periods because errors compound over time. In transformers, these failures also stem from [aliasing](https://arxiv.org/abs/2302.01178?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6), in which errors compound in specific locations over multiple time steps. (The resulting artifacts resemble pixelation in image processing.) Randomly jittering, or time-shifting, the data at each time step before feeding it back into the model reduces these artifacts.
How it works: Walrus predicts the next state of a physical system given a sequence of previous states. It comprises (i) two encoders, one for 2D data like velocity and one for 3D data like volume, that compress previous snapshots of the physical system, or frames, into tokens; (ii) a split attention block that generates tokens that represent the next frame; and (iii) two decoders (2D and 3D) that turn those tokens into the next frame.
- The authors pretrained the system to predict 63 physical properties (like density, pressure, and velocity) in the next frame of fluid motion. The training data included roughly 8 million 2D examples and 4 million 3D samples from
[two](https://arxiv.org/abs/2412.00568?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6)[datasets](https://arxiv.org/abs/2409.18032?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6)that cover 19 physical domains like acoustics, astrophysics, and[non-Newtonian fluids](https://www.ebsco.com/research-starters/science/non-newtonian-fluid?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6), which change their viscosity under pressure. - They fine-tuned the pretrained model using an additional 500,000 examples from three
[fluid](https://arxiv.org/abs/2210.07182?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6)[dynamics](https://arxiv.org/abs/2209.15616?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6)[datasets](https://arxiv.org/abs/2405.19101?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6)as well as data held out from the pre-training datasets. - To handle both 2D and 3D data, the system projects each 2D input into 3D space, treating 2D inputs as volume with a depth of one.
- To prevent the accumulation of aliasing errors, it shifts input data by random amounts before encoding it and applies the inverse shift after it generates each token. This technique distributed errors during each time step instead of allowing them to pile up at particular locations.
Results: The authors compared Walrus to earlier physics models including [MPP-AViT](https://arxiv.org/abs/2310.02994?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6), [Poseidon](https://arxiv.org/abs/2405.19101?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6), and [DPOT](https://arxiv.org/abs/2403.03542?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6).
- Walrus achieved the lowest variance-scaled root mean squared error (VRMSE) in 18 of the 19 domains for one-step predictions, such as the state of the velocity and temperature of a fluid that is heated from the bottom and cooled from the top.
- Walrus reduced one-step error by an average of 63.6 percent compared to the best of the competing models.
- Over 20 to 60 steps, Walrus achieved the lowest VRMSE in 12 out of 19 domains.
- Jittering reduced long-term error in 89 percent of scenarios.
Why it matters: Walrus potentially accelerates simulations in fields like climate science, aerospace, and materials. Moreover, the authors’ jittering technique may improve vision and video generation models by suppressing artifacts that are common to transformer architectures. In fact, the pixel-like artifacts common to vision transformers led them to take this approach.
We’re thinking: Physics’ shift from specialized numerical solvers and special-purpose models to general-purpose transformers mirrors natural language processing’s evolution from task-specific models to LLMs. Just as LLMs learn to read and predict the most likely next words across a wide range of tasks and languages, transformers trained on diverse data appear to be able to predict the behavior of diverse materials in a wide array of domains.
