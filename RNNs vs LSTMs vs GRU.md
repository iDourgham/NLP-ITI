# Understanding RNNs, LSTMs, and GRUs

## Recurrent Neural Networks (RNNs)

A **Recurrent Neural Network (RNN)** is an extension of a conventional feedforward neural network, designed to handle **variable-length sequence inputs**. It achieves this by maintaining a **recurrent hidden state** whose activation at each time step depends on the previous state.

### Generative RNNs

A **generative RNN** outputs a **probability distribution** over the next element in a sequence, given its current state $h_t$. This allows it to **generate variable-length sequences** by using a special output symbol to represent the end of the sequence.

### Challenges with RNNs

Despite their effectiveness, RNNs are difficult to train, especially in capturing **long-term dependencies**, due to:

* **Vanishing Gradients**: Gradients become very small during backpropagation, impeding learning.
* **Exploding Gradients**: Gradients grow excessively large, destabilizing training.

These issues arise from the repeated multiplication of gradients through time steps.

### Mitigation Strategies

1. **Better Optimization Algorithms**:

   * **Gradient Clipping**: Clipping the norm of the gradient vector to prevent explosion.
   * **Second-order Methods**: May be less sensitive to gradient growth patterns.

2. **Smarter Architectures**:

   * Introducing **gating mechanisms** in recurrent units for better memory control.
   * Leads to the development of **LSTM** and **GRU** units.

---

## Long Short-Term Memory (LSTM)

Introduced in **1997**, the **LSTM** is a type of recurrent unit designed to mitigate the limitations of standard RNNs. It features **gating mechanisms** that regulate the flow of information:

* **Forget Gate**: Decides what to discard.
* **Input Gate**: Controls what new information to store.
* **Output Gate**: Regulates what part of the memory is exposed.

### Key Strengths

* LSTM units can **retain important information** over long distances.
* By preserving memory rather than overwriting it, LSTMs can **capture long-term dependencies**.

---

## Gated Recurrent Unit (GRU)

Proposed by **Cho et al. (2014)**, the **GRU** is a simpler alternative to the LSTM. It combines the forget and input gates into a single **update gate**, and uses a **reset gate** to control the influence of the previous hidden state.

### Key Characteristics

* Lacks an **output gate**, thus exposes **the full memory state** at every time step.
* Uses fewer parameters and is **computationally more efficient** than LSTM.

---

## LSTM vs GRU

| Feature             | LSTM                    | GRU                                       |
| ------------------- | ----------------------- | ----------------------------------------- |
| Gates               | Input, Forget, Output   | Update, Reset                             |
| Controlled Exposure | Yes (Output Gate)       | No (Full Exposure)                        |
| Memory Cell         | Separate cell state     | Merged with hidden state                  |
| Computational Cost  | Higher                  | Lower                                     |
| Performance         | Strong long-term memory | Comparable or better in some tasks        |
| Training Efficiency | Slower                  | Faster (in terms of CPU time and updates) |

### Shared Advantages Over Traditional RNNs

* **Additive Memory Updates**: Both LSTM and GRU use additive updates, which help preserve features across many time steps.
* **Better Long-Term Dependency Handling**: Gating mechanisms allow these units to **retain relevant information** and **discard irrelevant inputs**.

---

## Applications

LSTM and GRU units have shown strong performance in tasks requiring long-term memory, such as:

* **Speech Recognition** (e.g., Graves et al., 2013)
* **Machine Translation**
* **Sentiment Analysis**
* **Named Entity Recognition**
* **Image Captioning**

---

## Summary

Advanced recurrent units like **LSTM** and **GRU** significantly improve upon traditional RNNs by enabling better training dynamics and memory retention. GRUs often outperform LSTMs in terms of **convergence speed** and **generalization**, while LSTMs may be better suited for tasks requiring **fine-grained memory control**.
