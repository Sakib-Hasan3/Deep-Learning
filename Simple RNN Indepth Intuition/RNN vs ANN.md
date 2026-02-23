<<<<<<< HEAD
---

## 1️⃣ ANN (Artificial Neural Network) কী?

### 🧱 ANN Architecture

ANN সাধারণত **Feedforward Network**:

```
Input → Hidden Layer → Output
```

📌 বৈশিষ্ট্য

* একবারে পুরো input নেয়
* কোনো **memory নেই**
* আগের input মনে রাখে না

### 🔍 ANN কীভাবে কাজ করে?

ধরো ইনপুট:

```
[5, 7, 3]
```

ANN একসাথে সব ইনপুট প্রসেস করে
👉 Output দেয়
👉 এরপর সব ভুলে যায় 😄

---

## ANN কোথায় ভালো?

✔ Image classification
✔ Tabular data
✔ Fixed-size input

❌ Sequence data (text, speech)

---

## 2️⃣ RNN (Recurrent Neural Network) কী?

### 🔄 RNN Architecture

RNN এর ভিতরে একটা **loop** থাকে 🔁

```
x₁ → [RNN] → h₁
x₂ → [RNN] → h₂
x₃ → [RNN] → h₃
```

📌 এখানে

* hₜ = hidden state (memory)
* hₜ আগের hₜ₋₁ মনে রাখে

---

## RNN Architecture (Inside View)

একটা time step এ:

```
      h(t-1)
        ↑
x(t) → [RNN Cell] → h(t)
```

👉 বর্তমান input + আগের memory
👉 নতুন memory তৈরি

---

## RNN এর Core Equation

[
h_t = \tanh(W_x x_t + W_h h_{t-1} + b)
]

👉 এটাকেই RNN “memory” বলা হয়

---

## Real-life Example 🧠

### Sentence:

```
"আজ আকাশ খুব সুন্দর"
```

### ANN হলে:

* "আজ", "আকাশ", "খুব", "সুন্দর" একসাথে দেখে
* word order বুঝতে পারে না

### RNN হলে:

* আজ → আকাশ → খুব → সুন্দর
* sequence ধরে ধরে বুঝে
* "খুব সুন্দর" context ধরে রাখে

---

## 3️⃣ RNN vs ANN (Side-by-Side)

| Feature       | ANN        | RNN           |
| ------------- | ---------- | ------------- |
| Input type    | Fixed size | Sequence      |
| Memory        | ❌ নেই      | ✅ আছে         |
| Order matters | ❌ না       | ✅ হ্যাঁ       |
| Same weights  | ❌          | ✅ (time-wise) |
| Text / Speech | ❌ দুর্বল   | ✅ ভালো        |

---

## Architecture Difference (Conceptually)

### ANN

```
x1   x2   x3
 |    |    |
 v    v    v
[  Hidden Layer ]
        |
      Output
```

### RNN (Unrolled)

```
x1 → h1 → y1
x2 → h2 → y2
x3 → h3 → y3
```

👉 এখানে **same RNN cell বারবার reuse হয়**

---

## Key Concept: Weight Sharing

RNN–এ:

* একই weight প্রতিটা time step এ ব্যবহার হয়
* ANN–এ প্রতিটা layer আলাদা weight

---

## কেন ANN sequence এ fail করে?

Sentence:

```
"সে আমাকে মারেনি"
```

ANN শুধু শব্দ দেখে
❌ context + order miss করে

RNN জানে:

* "মারেনি" শেষে এসেছে
* negation বুঝতে পারে

---

## RNN এর Limitation

* Long sentence → memory fade
* Vanishing gradient

👉 Solution:

* **LSTM**
* **GRU**
* **Transformer**

---

## Quick Intuition Summary 🧩

* ANN = “একবারে দেখে বিচার”
* RNN = “একটার পর একটা দেখে মনে রেখে বিচার”

---


=======
---

## 1️⃣ ANN (Artificial Neural Network) কী?

### 🧱 ANN Architecture

ANN সাধারণত **Feedforward Network**:

```
Input → Hidden Layer → Output
```

📌 বৈশিষ্ট্য

* একবারে পুরো input নেয়
* কোনো **memory নেই**
* আগের input মনে রাখে না

### 🔍 ANN কীভাবে কাজ করে?

ধরো ইনপুট:

```
[5, 7, 3]
```

ANN একসাথে সব ইনপুট প্রসেস করে
👉 Output দেয়
👉 এরপর সব ভুলে যায় 😄

---

## ANN কোথায় ভালো?

✔ Image classification
✔ Tabular data
✔ Fixed-size input

❌ Sequence data (text, speech)

---

## 2️⃣ RNN (Recurrent Neural Network) কী?

### 🔄 RNN Architecture

RNN এর ভিতরে একটা **loop** থাকে 🔁

```
x₁ → [RNN] → h₁
x₂ → [RNN] → h₂
x₃ → [RNN] → h₃
```

📌 এখানে

* hₜ = hidden state (memory)
* hₜ আগের hₜ₋₁ মনে রাখে

---

## RNN Architecture (Inside View)

একটা time step এ:

```
      h(t-1)
        ↑
x(t) → [RNN Cell] → h(t)
```

👉 বর্তমান input + আগের memory
👉 নতুন memory তৈরি

---

## RNN এর Core Equation

[
h_t = \tanh(W_x x_t + W_h h_{t-1} + b)
]

👉 এটাকেই RNN “memory” বলা হয়

---

## Real-life Example 🧠

### Sentence:

```
"আজ আকাশ খুব সুন্দর"
```

### ANN হলে:

* "আজ", "আকাশ", "খুব", "সুন্দর" একসাথে দেখে
* word order বুঝতে পারে না

### RNN হলে:

* আজ → আকাশ → খুব → সুন্দর
* sequence ধরে ধরে বুঝে
* "খুব সুন্দর" context ধরে রাখে

---

## 3️⃣ RNN vs ANN (Side-by-Side)

| Feature       | ANN        | RNN           |
| ------------- | ---------- | ------------- |
| Input type    | Fixed size | Sequence      |
| Memory        | ❌ নেই      | ✅ আছে         |
| Order matters | ❌ না       | ✅ হ্যাঁ       |
| Same weights  | ❌          | ✅ (time-wise) |
| Text / Speech | ❌ দুর্বল   | ✅ ভালো        |

---

## Architecture Difference (Conceptually)

### ANN

```
x1   x2   x3
 |    |    |
 v    v    v
[  Hidden Layer ]
        |
      Output
```

### RNN (Unrolled)

```
x1 → h1 → y1
x2 → h2 → y2
x3 → h3 → y3
```

👉 এখানে **same RNN cell বারবার reuse হয়**

---

## Key Concept: Weight Sharing

RNN–এ:

* একই weight প্রতিটা time step এ ব্যবহার হয়
* ANN–এ প্রতিটা layer আলাদা weight

---

## কেন ANN sequence এ fail করে?

Sentence:

```
"সে আমাকে মারেনি"
```

ANN শুধু শব্দ দেখে
❌ context + order miss করে

RNN জানে:

* "মারেনি" শেষে এসেছে
* negation বুঝতে পারে

---

## RNN এর Limitation

* Long sentence → memory fade
* Vanishing gradient

👉 Solution:

* **LSTM**
* **GRU**
* **Transformer**

---

## Quick Intuition Summary 🧩

* ANN = “একবারে দেখে বিচার”
* RNN = “একটার পর একটা দেখে মনে রেখে বিচার”

---


>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
