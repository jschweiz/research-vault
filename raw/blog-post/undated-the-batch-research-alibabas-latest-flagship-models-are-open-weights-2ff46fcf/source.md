---
id: undated-the-batch-research-alibabas-latest-flagship-models-are-open-weights-2ff46fcf
kind: blog-post
title: Alibaba’s Latest Flagship Qwen3.5 Models Are Open-Weights MoE Performers In Sizes from Less than 1B Parameters
source_url: https://www.deeplearning.ai/the-batch/alibabas-latest-flagship-models-are-open-weights-moe-performers-in-sizes-from-less-than-1b-parameters
source_name: The Batch Research
authors: []
published_at: '2026-03-20T08:46:15-07:00'
ingested_at: '2026-04-09T20:53:49.338651Z'
content_hash: fbb5fce8e90969cd6a6339c13a6f7f22492a2881103491692e3a50f41ab46ac8
identity_hash: f72ba81bee6f4e741565d9f07cab6e802b44d9bde5d83e0ec31e33b1bca0fd08
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- alibaba
- models
- open weights
- ai
- deep learning
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/alibabas-latest-flagship-models-are-open-weights-moe-performers-in-sizes-from-less-than-1b-parameters
canonical_url: https://www.deeplearning.ai/the-batch/alibabas-latest-flagship-models-are-open-weights-moe-performers-in-sizes-from-less-than-1b-parameters
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-13T18:33:45.930216Z'
short_summary: Alibaba released the Qwen3.5 family of open-weights vision-language models, featuring models ranging from 0.8B to 397B parameters. These models demonstrate excellent vision performance and can run on consumer hardware, offering new possibilities for vision-language applications.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:09:48.937808Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: f6c58a7278194e36116e802e3b5f25cc5372d5ec653309fb5f5b761756293200
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 3976e4a87e9907fca7ac789f009e3c80fbd5b9e93dc51188ffa00808d05ea567
lightweight_score:
  relevance_score: 0.8244
  source_fit_score: 0.24
  topic_fit_score: 1.0
  author_fit_score: 0.12
  evidence_fit_score: 0.93
  confidence_score: 0.84
  bucket_hint: must_read
  reason: 'Heuristic fallback based on rubric matches: post-training techniques, rl for llms, 2 favorite-topic matches.'
  evidence_quotes:
  - Alibaba released the Qwen3.5 family of open-weights vision-language models, featuring models ranging from 0.8B to 397B parameters. These models demonstrate exce
---
The Qwen3.5 family of open-weights vision-language models includes impressive larger models as well as a smaller one that outperforms an OpenAI open-weights model 10 times its size.
What’s new: Alibaba released the [Qwen3.5](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrV83qgz0W69sMD-6lZ3m4N6ZPm-lCQzzJW41wLD42f7dcGW58ZMPJ40ftmrW7XFk3w6ZzDj3W6ZBkPr6QGgkFN2LLc9vmRT92W4P0sp26RLFlZW5yfsDl5L__JsW7pZFhC3gb_NfW5JhL0g44XKQPW7rZZB95mft7fW2DYXlS4j_8KlW1pVFnZ6rnDkvN5p3yDNvJc43W2j8_YF891JvBW1G5dQ777LCsyW7SgK_J877rgsW3lxFKB4byh66W5-l5PP17SW7dW1ckPTh2f7Ymyf8B9pPM04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152693723%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=er1%2F5Wy6Ngi84OQdOwkvSW%2F5kV5m%2Fuh7hv6gVSn%2F9jY%3D&reserved=0) family of eight open weights vision-language models. The largest are Qwen3.5-397B-A17B (397 billion parameters, 17 billion active per token), which offers open weights, and Qwen3.5-Plus, a hosted version of Qwen3.5-397B-A17B that supports agentic applications by providing a larger input context and built-in tools that it can select autonomously. Four medium-size models include the open-weights Qwen3.5-122B-A10B, Qwen3.5-35B-A3B, and Qwen3.5-27B, plus Qwen3.5-Flash, a hosted version of Qwen3.5-53B-A3B that’s outfitted for agentic applications. Among the smaller Qwen3.5 members of the family — Qwen3.5-9B, Qwen3.5-4B, Qwen3.5-2B, and Qwen3.5-0.8B — the 9-billion and 4-billion parameter variations rival the performance of much larger models.
- Input/output: Text, image, video in (open-weights models 254,000 tokens extensible to 1 million tokens, hosted models up to 1 million tokens by default), text out (up to 64,000 tokens)
- Architecture: Mixture-of-experts or dense transformer with mixed attention and Gated DeltaNet layers, unspecified vision encoder
- Performance: Excellent vision performance overall; Qwen3.5-9B (9 billion parameters) outperforms gpt-oss-120B (120 billion parameters) on many language tasks.
- Availability: Open weights are freely
[available](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrVs3qgz0W6N1vHY6lZ3nQW11-hLB3CfH6bN8rCWCTBmxWjW4hxYqq24g0bnW8qk0WM4TSdq8W5LxLmY8lycxQW1FF6jb1BtVHNW5l8h-47HyBzYW11z1mK4T17xlW4Yns7K2RTDT-W4kGn1Y780n5gW12k5sM6JgFhVW1Vw8kM427n52W4MPd-B5W9SKTW3pbR4x3Zfds0W3TPTH38Y4hDlW6xY-Ng1t_D4SVr9hfl4h92R2W8Xn0sl4y-0hJN3jYGH_6Mm-QW29Xgsr3XtHKJW1B_PHK5JgJmYVPjNZQ2Tl8ZJdk2vBg04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152704851%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=6DQAq7%2BLtpMvyTuSxyzjQ3PciztIaU%2Bnx4BzIdsN%2FC4%3D&reserved=0)under the Apache 2.0 license; API for hosted open-weights models via Alibaba Cloud Model Studio (prices vary according to the specific model, $0.20-$0.60/$2-$3.6 per 1 million input/output tokens); API for Qwen3.5-Plus $0.4/$0.04/$2.4; API for Qwen3.5-Flash $0.1/$0.01/$0.4 per 1 million input/cached/output tokens. - Features: 201 languages, tool use, web search, chain-of-thought reasoning
- Undisclosed: Vision encoder, training data, and methods
How it works: Alibaba shared little information about how it built the Qwen3.5 family.
- Qwen3.5 is built on the
[Qwen3-Next architecture](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrTT5nR3bW5BWr2F6lZ3p_W2dsRR15t1ZQnW2G8S4P45QjytW7JrShC8-tGYgW50hWdm7h_BVSVsZGG-5htqTpN14x1qYwkmFBW6NmPl77mxkxtW8FSLCy20xtyzW6qnJHT1zcTyKW5prv3B4f4lk7W2sFcl98yKtk5W2XdtWN7KZm6XW778rrb13jtKLW9cLQzc3VWHhKW8hr1yX7nVyZMW6xsk7d1BlwCBW4t_NVy3LG7hhN5TrwRdVV9qtW93xRvk5kqxWCW48kcgy648mTRW7722g53clQMxV2lKD57cwtwRMjZgvn8csLSW7kHGmS8GFRXZN6DXm_4QhrslW1lXfyM8SG1xsN4VyLblRm5CMW7m2_Mz6spcDdW6SB1cn1bKtwJN86GR0V3jVj_W2SljBS1B6hnrW5ShbXp957wG-W7MTSWM8mWYbrW8C7ppK29n1LZf5Fk2MW04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152715343%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=jL%2BvLQbQ5BFSeLlrIpjKlfcy8liTZjASe7KmJJZCDxs%3D&reserved=0), a variation on the Qwen3-30B-A3B architecture and training method that’s modified to increase training efficiency and stability. - Qwen3.5 was trained on a “significantly larger scale of visual-text tokens” than Qwen3.
Results: Tested by Alibaba, all Qwen3.5 models excelled at vision tasks, outperforming much larger models, and some turned in competitive results in language tasks as well. Qwen3.5-9B and Qwen3.5-4B showed the most impressive performance overall, shining in both vision and language tasks, even compared to much larger models. The two smallest variations lack comparative metrics.
- On 28 of 44 vision benchmarks, Qwen3.5-397B-A17B outperformed GPT-5.2, Claude 4.5 Opus, and Gemini-3 Pro, whose parameter counts are undisclosed but almost certainly much larger. In a variety of language tasks, Qwen3.5-397B-A17B outperformed either GPT-5.2, Claude 4.5 Opus, or Gemini-3 Pro, but generally it did not outperform all three.
- On most language and vision benchmarks tested, Qwen3.5-122B-A10B and Qwen3.5-27B exceeded GPT-5-mini (parameter count undisclosed). Generally, Qwen3.5-122B-A10B, a mixture-of-experts architecture that activates 10 billion parameters per token, outperformed Qwen3.5-27B, a dense architecture of 27 billion parameters. Qwen3.5-35B-A3B generally underperformed the smaller Qwen3.5-27B and Qwen3.5-122B-A10B, but nonetheless it outperformed GPT-5-mini in 58 of 74 benchmarks tested.
- Qwen3.5-9B outdistanced OpenAI’s language model gpt-oss-120b — more than 10 times bigger — on most of the language benchmarks tested except reasoning and coding tasks. Similarly, Qwen3.5-4B outperformed OpenAI’s language model gpt-oss-20b on most language benchmarks tested except reasoning and coding tasks. On most of the vision benchmarks tested, both Qwen3.5-9B and Qwen3.5-4B outperformed the vision-language models GPT-5-nano and Gemini-2.5-Flash-Lite.
Behind the news: Shortly after rolling out the Qwen3 family, Lin Junyang, the team’s technical lead and a key architect of the models, abruptly resigned with a [post](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrVM3qgz0W7lCdLW6lZ3pQW4nj_Yf8zRCHjW62Xd5d5dTzb4W393GPg59M-1vW6cfGkS6y3rc8W9jrkBh3-ZKR1W3dT7d03kz1cWVVQkjY8JM_3QW6_mhD67bMjYJW3TC0vk2Fh8ZkW8q41FD1fs8QlW6YDVZn6rJwkgW5Fqvg-87mdNZW2Cg-bT498NXSW8P9N928ZWwFmW1JhQdQ3FvDY8N4ZvNj6yqfLxW3Fdf7t3QbjzQW153mkQ5vrPSNW8BK0hk2xZ6DSVyfSc21wctYHW3D6LDl88NzRZW1Yw9yZ7-27QzW6FG_BF1kcdn9W1g0fjS8c4Dzlf44MNcP04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152726814%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=MYbR%2Fsyz1ArCO%2BQDTa5swawrO78eOxVZOTUi6ckVNDU%3D&reserved=0) on the X social network that read, “Bye my beloved qwen.” The Chinese tech-news outlet [36kr.com](https://na01.safelinks.protection.outlook.com/?url=http%3A%2F%2F36kr.com%2F&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152742988%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=kFYrQzfWNsdAHueNE7QUBl8NtKY3eeZGhs9lZpniZbA%3D&reserved=0) subsequently [reported](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrVs3qgz0W6N1vHY6lZ3mDN6ZJf9z2q2mTW4ZD64H32j5zJW9kYNfc1qF58XW9g45Gt7lg2jxMdkHWwZb3CdW69ZsTk6m5HnQW97XlPn2Q2V9dW19Vs275LcwykVdpksH2F9JFCW4r4N2p1SpXBVN39rbvgSZDJjVJDszC99CdhgW5pMWg75F7NtDW5lJ-kK8GdnL2W8jTTVB3RrnRFN1b9r6BQqfm4W987RhB6Wg5D2N6xMNlngCsDWW4TQLSN8Y4hnpW5zY99G7wk1MWW2BWhvH8X4qRkW7wksnk3MB6Ynf8Dlsln04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152757511%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=gPsLWR%2BJfKP%2BG0fYYHDeBsg0HgF96oSrb3VKuAgybLk%3D&reserved=0) that four other members of the team resigned in his wake. In a January public appearance, Lin had said, “We are stretched thin — just meeting delivery demands consumes most of our resources,” Bloomberg [reported](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrWF3qgz0W95jsWP6lZ3q0VWW6bT484VGZN2c_h0NjNWvcMC7R1PfxVxgW3SwSWr52dlrDW3vDzPD2_KWXxW5zJ3t23gSB2ZW3s6zMf1gQB1kW8VPTf-5F0sKcW64lF_W5vps8CVGNQt172CMMVW8PlpQh2bBWW2W6ZBx5z6df91hW5tcP6c29m_93W2kb_lS7Lj_9bW1PZCqs4pgWCdW54jBcT27R-42W6kCP102YPLgPN3-Bhs823zx1W69jd_v7p1ryfW4KpH414CHrKrW8PVdl07yNSkcW900c_r6yFQv_W2__dSm4j54ptW1PbX1p572Z80W2TDbtf6nv6d3W7p3B7l5ZWb4GVh4xsK4nSG9GW6kfVJX314m-0W7lZWhv4J0vGlW4mv1QY4t5vzFf8gjTYx04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152772779%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=0%2FaCOgzf3WoqRjK%2Fve5PrJhNZOYOlX%2FUKWXMLAadp0A%3D&reserved=0). Alibaba responded by putting the Qwen project under tighter supervision by senior leadership and promising to [invest](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrWF3qgz0W95jsWP6lZ3kyW5GZJ_f5GcgYpW38zzJ14BjsGNV7Vk_J3PgQ02W4NDnwh4VHMwRN6lBQzTlpy1qW3ZbN0L12gWkWW3klLR_87Qh6zW20C4Vn726pBnW83Tzd596tTMmW56NWsB1qyG9_V-Y2rq7xR9pSW548KLd4zbdKkW8JNz0W63gWF4N8Cyjwd2H6S5W8wk-Dg2JF1XpW6mwV4Y5fWKFLW82zF4X4qJ2FtW8ByCvl10frkNW5cDckZ52nstHW1GMzfJ64HKmtW7xv_Mv8gGW8xW3_3JYX1CVqXCW1Wrg6F3VRzNZW3ylYXS3qB_fbW3dC4cr2YBD1BW1SCb8F7FCChYW2JJD-93bVfT1W58TRJ19dDRK-W40xdj66yb6gmW3kMhY72zwV97f6mg72s04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152784002%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=gCXKiAcsqW8SRolivje3LjU13MYAwU%2BO59ca5YKMq70%3D&reserved=0) further in AI development.
Why it matters: All Qwen3.5 models deliver stellar vision performance for their sizes, but the smaller models — especially Qwen3.5-9B — are small enough to run on consumer laptops while delivering performance that previously required an 80GB GPU like a Nvidia H100.
We’re thinking: Vision-language models with reasoning capability that are small enough to run locally means reduced cost, better privacy, and new vistas for vision-language applications.
