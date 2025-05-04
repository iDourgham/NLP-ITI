# Summary: Efficient Estimation of Word Representations in Vector Space

## Overview

This seminal paper introduces **Word2Vec**, an efficient framework for learning distributed vector representations (embeddings) of words from large datasets. The proposed models capture both **syntactic** and **semantic** relationships between words, allowing meaningful vector arithmetic like:
 vector("king") - vector("man") + vector("woman") ≈ vector("queen")

## Proposed Models

The authors propose two lightweight and scalable neural network architectures:

### 1. Continuous Bag-of-Words (CBOW)
- Predicts the current word based on the context (surrounding words).
- Ignores the order of context words.
- Faster and works well with large datasets.

### 2. Skip-Gram
- Predicts the surrounding context words given the current word.
- Works better for infrequent or rare words.
- Provides more accurate word representations for downstream tasks.

## Applications

- Natural Language Processing (NLP)
- Sentiment analysis
- Machine translation
- Semantic search
- Question answering

  ## Impact

The Word2Vec models set the foundation for a wide range of embedding-based NLP models and influenced future work like GloVe, fastText, and transformers (e.g., BERT). It remains a cornerstone of modern NLP pipelines.
