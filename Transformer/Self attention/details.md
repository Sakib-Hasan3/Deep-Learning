# Self-Attention Layer — Deep Detailed Working (Concept → Math → Intuition)

Self-Attention হলো এমন একটি mechanism যেখানে **প্রতিটি token বাক্যের অন্য সব token-কে weighted ভাবে দেখে** এবং নিজের নতুন contextual representation তৈরি করে।

---

# 1️⃣ Full Computational Flow

```text
Input Embeddings (X)
        ↓
Linear Projection → Q, K, V
        ↓
Score = QKᵀ
        ↓
Scale by √d_k
        ↓
Softmax
        ↓
Weighted Sum with V
        ↓
Output (Contextual Embedding)
```

---

# 2️⃣ Matrix-Level View

ধরি:

- Sequence length = $n$
- Model dimension = $d_{model}$
- Head dimension = $d_k$

$$
X \in \mathbb{R}^{n \times d_{model}}
$$

Projection:

$$
Q = XW_Q
$$
$$
K = XW_K
$$
$$
V = XW_V
$$

$$
W_Q, W_K, W_V \in \mathbb{R}^{d_{model} \times d_k}
$$

---

# 3️⃣ Attention Score Matrix

$$
S = QK^{\top}
$$

Shape:

$$
(n \times d_k)(d_k \times n) = n \times n
$$

এটা একটি **token-to-token interaction matrix**।

---

# 4️⃣ Scaling

$$
S' = \frac{QK^{\top}}{\sqrt{d_k}}
$$

### কেন?

Dot product-এর variance \approx $d_k$ proportional।
Scaling করলে variance \approx 1 থাকে → stable softmax।

---

# 5️⃣ Softmax

$$
A = \mathrm{softmax}(S')
$$

Row-wise normalize:

- প্রতিটি row sum = 1
- প্রতিটি token অন্য token-কে কত weight দিচ্ছে সেটার probability

---

# 6️⃣ Final Output

$$
Z = AV
$$

Shape:

$$
(n \times n)(n \times d_k) = n \times d_k
$$

---

# 🔷 Graphical Conceptual View

## Token Interaction Graph

![Image](https://ars.els-cdn.com/content/image/1-s2.0-S0031320319303851-gr1.jpg)

![Image](https://www.researchgate.net/publication/344485949/figure/fig2/AS%3A943478821371906%401601954288398/Heatmap-of-the-self-attention-weight-matrix-Each-row-shows-the-attention-distribution-a.ppm)

![Image](https://i.sstatic.net/TBpsF.png)

![Image](https://i.sstatic.net/jWduk.png)

---

# 7️⃣ Attention Heatmap Interpretation

ধরো sentence:

> “The animal didn’t cross the street because it was tired”

Attention matrix-এর একটি heatmap দেখতে এমন হতে পারে:

| From \ To | animal | street | it   |
| --------- | ------ | ------ | ---- |
| it        | 0.65   | 0.10   | 0.25 |

মানে:

- "it" → "animal"-এ বেশি weight দিচ্ছে
- Coreference resolve হচ্ছে

---

# 8️⃣ Geometric Interpretation

Dot product:

$$
q_i \cdot k_j
$$

- Angle ছোট হলে similarity বেশি
- Angle বড় হলে similarity কম

Attention essentially vector similarity measure।

---

# 9️⃣ Probabilistic View

Softmax করার পরে:

$$
a_{ij} = \frac{e^{\mathrm{score}_{ij}}}{\sum_j e^{\mathrm{score}_{ij}}}
$$

এটা conditional distribution:

> "Given token i, how important is token j?"

---

# 🔟 Why It Is Powerful

Self-Attention:

✔ Long-range dependency capture
✔ Fully parallel
✔ No recurrence
✔ Context-aware embedding

---

# 11️⃣ Multi-Head Extension

Instead of single:

$$
\mathrm{Attention}(Q,K,V)
$$

We use:

$$
\mathrm{head}_i = \mathrm{Attention}(QW_i^Q, KW_i^K, VW_i^V)
$$

$$
\mathrm{MultiHead} = \mathrm{Concat}(\mathrm{head}_1,\dots,\mathrm{head}_h)W_O
$$

Different heads learn:

- Syntax relation
- Coreference
- Position-based pattern
- Semantic similarity

---

# 12️⃣ Complexity Analysis

Time complexity:

$$
O(n^2 d_k)
$$

Problem:

- Long sequence → quadratic memory

Solution variants:

- Sparse attention
- Linear attention
- Flash attention

---

# 13️⃣ Variance Insight (Why Scaling Works)

If:

$$
\mathrm{Var}(q_i)=1,\quad \mathrm{Var}(k_i)=1
$$

Then:

$$
\mathrm{Var}(q\cdot k) = d_k
$$

Divide by $\sqrt{d_k}$:

$$
\mathrm{Var} \approx 1
$$

Softmax stable থাকে।

---

# 14️⃣ Full Formula (Compact Form)

$$
Z = \mathrm{softmax}\left(\frac{QK^{\top}}{\sqrt{d_k}}\right)V
$$

---

# 15️⃣ Conceptual Summary

Self-Attention =

- Similarity computation
- Probability distribution
- Weighted aggregation
- Context fusion

---
