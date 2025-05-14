Here's a Markdown-formatted summary of the **"Attention Is All You Need"** paper:

---

# 📄 Summary of *Attention Is All You Need*

### 🔗 Paper Reference

*Vaswani et al., 2017*
[Link to paper](https://arxiv.org/abs/1706.03762)

---

## 🚀 Introduction

Traditional sequence transduction models (like machine translation) relied on **Recurrent Neural Networks (RNNs)** or **Convolutional Neural Networks (CNNs)**, often augmented with attention mechanisms. However, these models are inherently sequential, limiting their parallelization and training efficiency.

### 🔄 Limitation of RNNs

* Sequential processing: each output depends on the previous step.
* Slow training due to lack of parallelism.
* Long sequences are harder to manage due to memory and time constraints.

---

## 🧠 Key Idea: The Transformer

The **Transformer** is a novel architecture that **dispenses with recurrence and convolutions entirely**, relying **solely on attention mechanisms**.

* Faster training through full parallelization.
* Outperforms existing models on translation tasks (BLEU scores).

---

## 🏆 Results

* **English–German translation (WMT 2014):** 28.4 BLEU (best single model at the time).
* **English–French translation (WMT 2014):** 41.8 BLEU (after 3.5 days of training on 8 GPUs).

---

## 🧱 Transformer Architecture

### 📤 Encoder

* Stack of **N = 6 identical layers**.
* Each layer has:

  * Multi-head **self-attention** sub-layer.
  * **Feed-forward neural network** sub-layer.
  * **Residual connections** + **Layer Normalization**.
* Embedding and all sub-layers have **d\_model = 512**.

### 📥 Decoder

* Also a stack of **N = 6 layers**.
* Each layer includes:

  * Masked multi-head **self-attention** (to prevent attending to future tokens).
  * Multi-head **encoder-decoder attention**.
  * Feed-forward layer.
  * Residual connections + LayerNorm.

---

## 🎯 Attention Mechanism

### 🔹 Scaled Dot-Product Attention

Given queries (Q), keys (K), and values (V):

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
$$

* Computes similarity between Q and K.
* Scales dot products by √dk for stability.
* Softmax is applied to obtain attention weights on V.

### 🔹 Multi-Head Attention

* Instead of one attention function, **multiple heads** run in parallel.
* Each head learns different representations.
* Outputs are concatenated and projected.

---

## 🧠 Self-Attention Advantages

* Models relationships regardless of distance in sequence.
* Computationally efficient and **fully parallelizable**.
* Scales better to long sequences than RNNs.

---

## 📌 Conclusion

The Transformer:

* Is the **first model to rely entirely on self-attention** for sequence transduction.
* Offers **state-of-the-art performance** on key machine translation benchmarks.
* Opens the door for new research in fully attention-based architectures.
