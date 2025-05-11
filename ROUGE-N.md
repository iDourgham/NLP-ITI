Here's your comprehensive explanation of ROUGE converted into clean, structured **Markdown** format, ideal for technical documentation, blog posts, or study notes:

---

# ROUGE: Recall-Oriented Understudy for Gisting Evaluation

**ROUGE** is a set of metrics and a software package designed for evaluating **automatic summarization**. It can also be applied to **machine translation** by comparing an automatically produced summary or translation against high-quality, **human-produced references**.

---

## 📏 ROUGE Metrics Overview

In this article, we cover the main metrics used in the ROUGE package:

---

## 🔹 ROUGE-N

Measures the number of overlapping **n-grams** between the candidate (model output) and the reference text.

### Example:

* **Reference (R)**: `The cat is on the mat.`
* **Candidate (C)**: `The cat and the dog.`

### ROUGE-1 (Unigrams)

* **Matching unigrams**: "the", "cat", "the"
* **Precision** = 3/5 = **0.6**
* **Recall** = 3/6 = **0.5**
* **F1-score** = 2 × (0.6 × 0.5) / (0.6 + 0.5) = **0.54**

### ROUGE-2 (Bigrams)

* **Matching bigrams**: "the cat"
* **Precision** = 1/4 = **0.25**
* **Recall** = 1/5 = **0.20**
* **F1-score** = 2 × (0.25 × 0.20) / (0.25 + 0.20) = **0.22**

---

## 🔹 ROUGE-L (Longest Common Subsequence)

Measures the length of the **Longest Common Subsequence (LCS)** — the longest sequence of words that appear in both reference and candidate in the same order (not necessarily consecutively).

* **LCS**: "the cat the"
* **Precision** = 3/5 = **0.6**
* **Recall** = 3/6 = **0.5**
* **F1-score** = 2 × (0.6 × 0.5) / (0.6 + 0.5) = **0.55**

---

## 🔹 ROUGE-S (Skip-bigram)

Allows for matching of **non-consecutive word pairs** (skip-grams), offering leniency in word order or intervening words.

### Example:

* **Reference (R)**: `The cat is on the mat.`
* **Candidate (C)**: `The gray cat and the dog.`
* The skip-gram “the cat” matches even if “gray” separates the words in the candidate.

**Note**: ROUGE-S is less frequently used today and may not be supported in all modern libraries.

---

## ✅ Pros and ❌ Cons of ROUGE

### ✅ Pros:

* Correlates well with human judgment
* Inexpensive to compute
* Language-independent

### ❌ Cons:

* Ignores **semantics** (e.g., synonyms or paraphrasing)
* Focuses on **exact syntactic matches**

---

## 🔄 ROUGE vs. BLEU

| Metric    | Focus     | Measures                                           |
| --------- | --------- | -------------------------------------------------- |
| **BLEU**  | Precision | How much of the candidate appears in the reference |
| **ROUGE** | Recall    | How much of the reference appears in the candidate |

> These two metrics **complement** each other — useful in evaluating the **precision-recall tradeoff**.

---

### Article Link: https://medium.com/nlplanet/two-minutes-nlp-learn-the-rouge-metric-by-examples-f179cc285499
