---
id: 2026-04-10-the-batch-research-googles-alphagenome-interprets-dna-that-regulate-10f4dd41
kind: blog-post
title: Google’s AlphaGenome Interprets DNA That Regulates Genetic Expression
source_url: https://www.deeplearning.ai/the-batch/googles-alphagenome-interprets-dna-that-regulates-genetic-expression
source_name: The Batch Research
authors:
- None
published_at: '2026-04-10T10:55:56-07:00'
ingested_at: '2026-04-13T18:33:24.446041Z'
content_hash: 9f5b519ed32354cbdf6201adb1d20eccb48caf57e9c98b901fd2eefb2d570051
identity_hash: d76e338782d13ce2cb44b0c6b9d6571c5bd3b0a61d0fe3ccdd2e8eb9a8826c5a
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- dna
- genomics
- alphagenome
- gene_expression
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/googles-alphagenome-interprets-dna-that-regulates-genetic-expression
canonical_url: https://www.deeplearning.ai/the-batch/googles-alphagenome-interprets-dna-that-regulates-genetic-expression
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-13T18:33:24.446043Z'
short_summary: AlphaGenome is an open-weights model that interprets the 98 percent of the human and mouse genomes that regulate gene expression. It uses a combination of CNNs, transformers, and CNN decoders to find properties like gene boundaries and RNA production rates.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:18.143360Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: a154e0dba841cd282385acbf3eb374a90482c0bd588aa3e48b31f4de19a7ac66
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: fc85d78c2797e6ae6ef372d3a3cd016a2ab737cda5e0691af6af712fe29f6321
lightweight_score:
  relevance_score: 0.16
  source_fit_score: 0.36
  topic_fit_score: 0.16
  author_fit_score: 0.0
  evidence_fit_score: 0.36
  confidence_score: 0.8
  bucket_hint: archive
  reason: The document is highly technical and focuses on genomics, which has weak direct overlap with the user's core LLM research topics, although it involves model architecture.
  evidence_quotes:
  - AlphaGenome is an open-weights model that interprets the 98 percent of the human and mouse genomes that regulate gene expression.
  - 'Architecture: convolutional neural network (CNN) encoder, transformer, CNN decoder'
  - Across 50 evaluations, AlphaGenome matched or exceeded earlier models in 47 of them
---
An open-weights model could help scientists compare the impact of genetic variations, identify mutations that cause diseases, and develop treatments.
What’s new: [AlphaGenome](https://www.nature.com/articles/s41586-025-10014-0?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6) interprets the 98 percent of the human and mouse genomes that don’t code for proteins but regulate gene expression and other functions. It finds properties such as where in a DNA sequence a gene begins and ends; how much RNA it directs a cell to produce; and where, as a cell reads a gene, it skips over parts of the gene sequence, a process in which errors can cause a variety of diseases.
- Input/output: 1 million DNA base pairs and organism type (human or mouse) in, roughly 6,000 human gene properties and 1,000 mouse gene properties out
- Architecture: convolutional neural network (CNN) encoder, transformer, CNN decoder
- Performance: Across 50 evaluations, AlphaGenome matched or exceeded earlier models in 47 of them
- Availability:
[API](https://deepmind.google.com/science/alphagenome/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6),[weights](https://huggingface.co/collections/google/alphagenome?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6), and[inference code](https://github.com/google-deepmind/alphagenome_research?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6)freely[licensed](https://deepmind.google.com/science/alphagenome/model-terms?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6)for noncommercial uses
How it works: The authors pretrained 64 models of identical architecture on gene sequences and their properties, and then distilled their knowledge into a single model. Thus AlphaGenome learned the aggregate performance of all 64 models. They pretrained the models on mouse and human DNA and gene properties in [four](http://encodeproject.org/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6) [large](https://www.gtexportal.org/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6) [public](https://4dnucleome.org/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6) [datasets](https://fantom.gsc.riken.jp/5/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9YEAhfwU9tvGXZx9DP70Gu2s8iB1c9CA6EGtUzUaDTQZ5rjjvwCq1Z9RkKukzCkWlrB-I6).
- For all 64 models, given a DNA sequence of up to 1 million base pairs, a CNN produced an embedding of every 128 base pairs. A transformer processed the embeddings, enabling the model to learn relationships between base pairs in distant parts of the sequence, and a CNN decoder took the transformer’s output and generated various properties.
- The models learned to generate the properties of genes within the input sequence via 19 loss terms. For instance, one term encouraged the model to match its predicted distribution of the amount of RNA produced with the ground-truth distribution, while another encouraged the model to classify each base pair based on whether a cell, while reading the sequence, would skip over it starting at that base pair.
- In the distillation stage, AlphaGenome learned to generate the gene properties generated by the 64 models, using the same loss terms as before.
Results: The authors compared AlphaGenome to nine earlier models across two broad evaluations: finding properties of a gene sequence and predicting the effect of mutation (an alteration in the sequence) on those properties.
- When finding gene properties, AlphaGenome outperformed previous models in 22 out of 24 cases.
- When predicting the effect of mutations, it matched or exceeded previous models in 24 of 26 cases.
- The authors also assessed AlphaGenome’s performance in a real-world situation. They took normal DNA and modified it to match the changes caused by the illness known as T-cell acute lymphoblastic leukemia (T-ALL). They fed the unmodified and modified sequences to AlphaGenome and compared its outputs. The model’s predicted changes in protein expression fit the known mechanism of T-ALL’s effect on cells.
Why it matters: As recently as 15 years ago, non-coding DNA was widely believed to have no function at all. Since then, probing its functions has required painstaking experimentation. AlphaGenome puts that research into a model that anyone can use to find connections between this genomic netherworld and biological processes. For instance, the model makes it practical to compare functional differences between normal and mutated genes, revealing information that could be valuable in medicine and other biological disciplines.
We’re thinking: The notion that most of the human genome was “junk DNA” was curious, and scientists have discovered that it does essential things. We may be about to learn just how much it can do.
