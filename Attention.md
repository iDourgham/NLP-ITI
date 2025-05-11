# Attention Mechanism in Neural Machine Translation (NMT)

## Introduction

An **attentional mechanism** has recently been introduced to **improve Neural Machine Translation (NMT)** by allowing the model to **selectively focus on parts of the source sentence** during translation. This selective focus enables better handling of long and complex sentences.

---

## Benefits of NMT

* **Word-by-word generation**: NMT emits one **target word at a time**, typically using an autoregressive decoder architecture.
* **End-to-end training**: The entire system is trained jointly to optimize translation quality.
* **Generalization to long sequences**: Unlike traditional machine translation, NMT can generalize better to long sequences without explicitly storing:

  * Phrase tables
  * External language models
* **Lightweight**: The memory footprint of NMT models is **significantly smaller** than traditional MT systems.
* **Simplicity**: Implementing an NMT decoder is much easier compared to the **highly intricate decoders** used in phrase-based systems.

---

## Attention in NMT

In their influential paper, **Bahdanau et al. (2015)** introduced an **attention mechanism** to jointly **translate and align words** in a sentence. This marked a significant step in the evolution of NMT by moving away from the rigid fixed-length context vectors used in earlier encoder–decoder models.

> As of their publication, this was the first major work exploring **attention-based architectures for NMT**.

---

## Global vs. Local Attention

Two main variants of attention-based models are commonly used in NMT:

### 1. Global Attention

* **Focus**: Considers **all source words** when generating each target word.
* **Mechanism**:

  * At each decoding time step *t*, compute **alignment scores** between the decoder’s current state `h_t` and each encoder hidden state `h̄_s`.
  * Normalize the scores into **attention weights** `α_t`.
  * Compute the **context vector `c_t`** as a **weighted average** of all source hidden states:

    $$
    c_t = \sum_s \alpha_{t,s} \cdot \bar{h}_s
    $$
* **Advantage**: Allows the model to attend to any part of the source sentence, regardless of its length.

### 2. Local Attention

* **Focus**: Considers only a **subset of source words** at each time step.
* **Mechanism**:

  * Predicts a position `p_t` to center attention around.
  * Uses a fixed-size window (e.g., `p_t ± D`) to compute attention.
  * The model is more computationally efficient due to fewer attention calculations.
* **Advantage**: Reduces computational cost and may improve alignment by focusing on more probable regions.

---

## Common Architecture Steps

Despite their differences, both global and local attention models **share key architecture steps** during decoding:

1. At each decoder time step `t`, take the top-layer decoder hidden state `h_t`.
2. Compute a **context vector `c_t`**:

   * Global: via attention over **all** encoder states.
   * Local: via attention over a **subset**.
3. **Concatenate `h_t` and `c_t`** to form the **attentional hidden state**.
4. Use this state to predict the **target word `y_t`**.

---

### Paper Link: https://arxiv.org/abs/1508.04025
