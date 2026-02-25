
# Multi-Head Attention (MHA) — Introduction

**Multi-Head Attention** হলো Self-Attention-এর একটি বিস্তৃত রূপ, যেখানে একটিমাত্র attention না চালিয়ে একাধিক attention “head” সমান্তরালভাবে চালানো হয়।
প্রতিটি head আলাদা projection (ভিন্ন $(W_Q, W_K, W_V)$) ব্যবহার করে ভিন্ন ধরনের সম্পর্ক শিখতে পারে—যেমন syntax, coreference, semantic similarity ইত্যাদি।

---

## কেন “Multi-Head”?

একটি single attention সাধারণত এক ধরনের similarity pattern-এ ফোকাস করে।
Multi-Head Attention:

- একই input থেকে **ভিন্ন subspace-এ** project করে
- প্রতিটি head আলাদা relation capture করে
- শেষে সব head-এর output **concat** করে richer representation তৈরি করে

---

## High-Level Data Flow

```text
Input (X)
   │
   ├── Head 1:  Attention(Q1,K1,V1)
   ├── Head 2:  Attention(Q2,K2,V2)
   ├── ...
   └── Head h:  Attention(Qh,Kh,Vh)
         │
      Concat
         │
      Linear (W_O)
         │
       Output
```

---

## Graphical Representation (Block View)

![Image](https://www.researchgate.net/publication/358939132/figure/fig4/AS%3A11431281092205080%401666750872566/Multi-head-attention-structure.png)

![Image](https://uvadlc-notebooks.readthedocs.io/en/latest/_images/transformer_architecture.svg)

![Image](https://d2l.ai/_images/multi-head-attention.svg)

![Image](https://www.researchgate.net/publication/372074536/figure/fig2/AS%3A11431281172082742%401688440507863/Multi-head-attention-mechanism-In-the-encoder-and-decoder-multiple-attention-heads-are.png)

---

## Mathematical Overview

ধরি:

- $d_{model}$ = model dimension
- $h$ = number of heads
- $d_k = \dfrac{d_{model}}{h}$

প্রতিটি head:

$$
\mathrm{head}_i = \mathrm{Attention}(QW_i^Q,\; KW_i^K,\; VW_i^V)
$$

তারপর:

$$
\mathrm{MultiHead}(Q,K,V) = \mathrm{Concat}(\mathrm{head}_1,\dots,\mathrm{head}_h)W_O
$$

এখানে:

- $W_i^Q, W_i^K, W_i^V$ আলাদা projection matrix
- $W_O$ final output projection

---

## Intuitive Example

ধরো বাক্য:

> "The animal didn’t cross the street because it was tired"

- Head 1 → grammar relation ধরছে
- Head 2 → pronoun resolution ধরছে
- Head 3 → semantic similarity ধরছে

সব মিলিয়ে final embedding হয় context-rich।

---

## Key Insight

| Single Head            | Multi-Head         |
| ---------------------- | ------------------ |
| এক ধরনের relation      | একাধিক relation    |
| Limited expressiveness | Rich feature space |
| কম flexibility         | High flexibility   |

---

