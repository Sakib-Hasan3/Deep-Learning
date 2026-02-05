## **Mini-Batch SGD (Stochastic Gradient Descent) — Basic Theory**

![Image](https://miro.medium.com/1%2AI2BkYWA_OJzHWFo6kc0fmQ.jpeg)

![Image](https://miro.medium.com/1%2A9A0u4eeU_75bPgEuEwnwVQ.png)

![Image](https://www.researchgate.net/publication/261499993/figure/fig3/AS%3A613849782837261%401523364601324/flowchart-of-GPU-based-mini-batch-learning-algorithm.png)

---

### 🔹 1) Mini-Batch SGD কী?

**Mini-Batch Stochastic Gradient Descent** হলো Gradient Descent-এর এমন একটি পদ্ধতি যেখানে
👉 **পুরো dataset একসাথে নয়**,
👉 আবার **একটা sample দিয়েও নয়**,
👉 বরং **ছোট ছোট batch (subset)** নিয়ে parameter update করা হয়।

**One-line definition:**

> *Mini-Batch SGD updates model parameters using the average gradient computed from a small batch of training samples.*

---

### 🔹 2) কেন Mini-Batch দরকার?

Gradient Descent-এর তিনটা ধরন তুলনা করলে বিষয়টা পরিষ্কার হয়:

| Method             | কীভাবে কাজ করে | সমস্যা               |
| ------------------ | -------------- | -------------------- |
| **Batch GD**       | সব data একসাথে | খুব ধীর, বেশি memory |
| **SGD**            | ১টা sample     | খুব noisy, unstable  |
| **Mini-Batch SGD** | 32–256 sample  | ✅ Speed + stability  |

👉 Mini-Batch SGD **দুই দুনিয়ার সেরা সমাধান**।

---

### 🔹 3) Mini-Batch SGD কীভাবে কাজ করে? (Concept Flow)

1. পুরো training dataset নাও
2. Dataset কে **ছোট batch** এ ভাগ করো (যেমন 32, 64)
3. প্রতিটা batch-এর জন্য:

   * Forward pass
   * Batch loss (average)
   * Gradient calculation
   * Weight update
4. সব batch শেষ হলে = **1 epoch**

---

### 🔹 4) Mathematical Idea (সহজভাবে)

ধরি,

* Batch size = (m)
* প্রতিটা sample-এর loss = (\ell_i)

**Batch cost:**
[
J_{\text{batch}}=\frac{1}{m}\sum_{i=1}^{m}\ell_i
]

**Gradient:**
[
\nabla J_{\text{batch}}=\frac{1}{m}\sum_{i=1}^{m}\nabla \ell_i
]

**Update rule:**
[
\theta \leftarrow \theta - \eta \nabla J_{\text{batch}}
]

👉 অর্থাৎ, **batch-এর গড় gradient** দিয়ে update।

---

### 🔹 5) Important Terms (Exam Favourite)

* **Batch size:** একবারে কয়টা sample
* **Iteration:** এক batch → এক update
* **Epoch:** পুরো dataset একবার complete

---

### 🔹 6) Mini-Batch SGD কেন Deep Learning-এ Default?

✔ GPU-friendly (matrix operations)
✔ SGD-এর চেয়ে stable
✔ Batch GD-এর চেয়ে fast
✔ Large dataset-এ scalable

---

### 🧠 Memory Trick

> **SGD = 1 sample**
> **Mini-Batch = few samples**
> **Batch = all samples**

---

### ✍️ Exam-Ready One Line

> **Mini-Batch SGD updates model parameters using the average gradient of a small subset of data, providing a balance between fast convergence and stable learning.**

