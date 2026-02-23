## Transformer-এর Basic Architecture (Core Understanding)

Transformer হলো একটি **attention-based deep learning architecture**, যা মূলত sequence modeling-এর জন্য ডিজাইন করা। এটি প্রথম প্রস্তাব করা হয় ২০১৭ সালে গবেষণা পেপার **Attention Is All You Need**-এ, যা প্রকাশ করে **Google**-এর গবেষকরা।

---

# 1️⃣ High-Level Structure

Transformer সাধারণত দুইটি প্রধান অংশ নিয়ে গঠিত:

```
Input → Encoder Stack → Decoder Stack → Output
```

* **Encoder** → Input sequence encode করে contextual representation বানায়
* **Decoder** → Encoded representation ব্যবহার করে output generate করে

---

# 2️⃣ Full Architecture Overview

![Image](https://images.openai.com/static-rsc-3/qyST1BvXioVvfdlU_Y0__cebbHhTT1QHG_r-VuPnIgPJIUON59tjhtXt_8nOt7mwG3evsShmeU0MKiaSq3o5-Xu_wlFH-yzR-lxuT7wqX3I?purpose=fullsize\&v=1)

![Image](https://images.openai.com/static-rsc-3/WDuHb64OVwEt0Dbfie7hNwtoCGvOKHFlgQCPeYn5XL78wA6oR2HOoPJP_2-FVdzTrlBXi7-DRySEQO2LP6p8F9BpETqN0Dl_i9A27o8jZOM?purpose=fullsize\&v=1)

![Image](https://uvadlc-notebooks.readthedocs.io/en/latest/_images/transformer_architecture.svg)

![Image](https://www.researchgate.net/publication/378365908/figure/fig1/AS%3A11431281225093278%401708544494273/Multi-Head-Attention-block-Central-to-transformer-models-It-segments-the-input-into.jpg)

---

# 3️⃣ Encoder Architecture Breakdown

একটি Transformer-এ সাধারণত **N identical encoder layers** থাকে (প্রায় 6 টি)।

প্রতিটি Encoder Layer এ থাকে:

### 🔹 (A) Multi-Head Self-Attention

* প্রতিটি token অন্য সব token-এর সাথে সম্পর্ক হিসাব করে
* Long-range dependency capture করে

### 🔹 (B) Add & Layer Normalization

* Residual connection
* Training stable রাখে

### 🔹 (C) Feed Forward Neural Network (FFN)

* Fully connected network
* প্রতিটি token independently transform হয়

---

## Encoder Layer Flow

```
Input Embedding
      ↓
Self Attention
      ↓
Add & Norm
      ↓
Feed Forward
      ↓
Add & Norm
```

---

# 4️⃣ Decoder Architecture Breakdown

Decoder-এও multiple layers থাকে। তবে এখানে ৩টি প্রধান ব্লক থাকে:

### 🔹 (A) Masked Multi-Head Attention

* Future token দেখতে পারে না
* Auto-regressive generation

### 🔹 (B) Encoder-Decoder Attention

* Encoder output-এর উপর attention দেয়

### 🔹 (C) Feed Forward Network

---

# 5️⃣ Core Mathematical Component

## 🔹 Self-Attention Formula

$$
\mathrm{Attention}(Q, K, V) = \mathrm{softmax}\!\left(\frac{Q K^{\top}}{\sqrt{d_k}}\right) V
$$

যেখানে:

* $Q$ = Query
* $K$ = Key
* $V$ = Value
* $d_k$ = scaling dimension (often $d_{\text{model}} / \text{#heads}$)

---

# 6️⃣ Multi-Head Attention

একটা attention না, বরং multiple attention parallel run করে।

কারণ:

* Model একাধিক semantic relation ধরতে পারে
* Representation richer হয়

---

# 7️⃣ Positional Encoding

Transformer sequence order নিজে বুঝতে পারে না। তাই positional encoding যোগ করা হয়:

[
PE(pos,2i)=\sin(pos/10000^{2i/d})
]

[
PE(pos,2i+1)=\cos(pos/10000^{2i/d})
]

এটি model-কে token order বুঝতে সাহায্য করে।

---

# 8️⃣ কেন Transformer দ্রুত?

| RNN                    | Transformer    |
| ---------------------- | -------------- |
| Sequential computation | Fully parallel |
| Long dependency weak   | Strong         |
| Training slow          | Faster         |

Transformer GPU-তে efficiently parallel computation করতে পারে।

---

# 9️⃣ Variants of Transformer

* Encoder-only → BERT
* Decoder-only → GPT
* Encoder-Decoder → T5

যেমন:

* OpenAI GPT model
* Google BERT

---

# 🔟 Practical Insight

Transformer এখন ব্যবহৃত হয়:

* NLP
* Vision (ViT)
* Audio
* Multimodal systems

---

# Final Conceptual Summary

Transformer =

* Attention mechanism
* Parallel architecture
* Scalable deep learning model
* Long context understanding

---

