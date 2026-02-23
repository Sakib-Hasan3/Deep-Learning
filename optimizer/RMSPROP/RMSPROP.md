## **RMSProp (Root Mean Square Propagation) — Graph সহ বিস্তারিত ব্যাখ্যা**

![Image](https://miro.medium.com/1%2Aklmbvjq7PSj6tmuDoyTGaA.png)

![Image](https://ml-explained.com/articles/rmsprop-explained/rmsprop_example.PNG)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1240/1%2AY2KPVGrVX9MQkeI8Yjy59Q.gif)

![Image](https://d2l.ai/_images/output_rmsprop_251805_15_1.svg)

---

## 1️⃣ RMSProp কী?

**RMSProp** হলো একটি **adaptive gradient descent optimizer**, যা **Adagrad-এর মূল সমস্যাটা ঠিক করার জন্য** তৈরি করা হয়েছে।

👉 Adagrad-এ learning rate সময়ের সাথে খুব ছোট হয়ে যায়
👉 RMSProp-এ **সাম্প্রতিক gradient-এর moving average** ব্যবহার করা হয়
👉 ফলে learning rate **পুরোপুরি মরে যায় না**

---

## 2️⃣ কেন RMSProp দরকার হয়েছিল?

### Adagrad-এর সমস্যা:

* Squared gradient সবসময় জমতে থাকে
* Denominator ক্রমাগত বড় হয়
* Learning rate → প্রায় 0
* Training আগেই থেমে যায়

### RMSProp সমাধান:

* সব gradient জমায় না
* **Exponential Moving Average (EMA)** নেয়
* পুরোনো gradient ধীরে ধীরে ভুলে যায়

---

## 3️⃣ Mathematical Formulation (Core)

ধরি,

* ( \theta ) = parameter
* ( g_t = \nabla J(\theta_t) ) = current gradient
* ( \eta ) = learning rate
* ( \rho ) = decay rate (সাধারণত 0.9)
* ( \epsilon ) = small constant (যেমন (10^{-8}))

### Step–1: Squared gradient-এর moving average


$$
s_t = \rho s_{t-1} + (1-\rho) g_t^2
$$

### Step–2: Parameter update


$$
	heta_{t+1} = \theta_t - \frac{\eta}{\sqrt{s_t} + \epsilon} \cdot g_t
$$

---

## 4️⃣ Intuition (সহজ ভাষায়)

* (s_t) ≈ recent gradient magnitude
* Gradient বড় হলে → learning rate ছোট
* Gradient ছোট হলে → learning rate বড়

👉 **Per-parameter adaptive step**, কিন্তু Adagrad-এর মতো জমে থাকে না।

Graph-এ:

* SGD → zig-zag
* Adagrad → slow হয়ে থেমে যায়
* RMSProp → smooth + stable descent

---

## 5️⃣ RMSProp-এ ε (epsilon) কেন দরকার?

* Division by zero এড়াতে
* Numerical stability রাখতে
* Very small denominator prevent করতে

👉 ε সাধারণত **(10^{-8})**

---

## 6️⃣ Hyperparameters ও তাদের ভূমিকা

| Parameter | Meaning            | Typical value |
| --------- | ------------------ | ------------- |
| η         | Learning rate      | 0.001         |
| ρ         | Decay rate         | 0.9           |
| ε         | Stability constant | 1e−8          |

---

## 7️⃣ Advantages (সুবিধা)

✔ Adagrad-এর learning-rate-decay সমস্যা সমাধান
✔ Non-stationary problems-এ ভালো
✔ Zig-zag কমায়
✔ Deep learning-এ ভালো কাজ করে

---

## 8️⃣ Disadvantages (অসুবিধা)

❌ Momentum explicitly নেই
❌ Adam-এর তুলনায় একটু slow
❌ Learning rate এখনো tune করা লাগে

---

## 9️⃣ RMSProp vs Adagrad vs SGD (Concept)

* **SGD:**
  Fixed learning rate, noisy path

* **Adagrad:**
  Learning rate কমতে কমতে থেমে যায়

* **RMSProp:**
  Recent gradient দেখে adaptive, stable learning

---

## 10️⃣ কোথায় RMSProp ভালো?

✅ RNN / LSTM
✅ Non-stationary loss landscape
✅ Deep neural networks

---

## 🧠 মনে রাখার ট্রিক

> **RMSProp = Adagrad but with memory loss**

(পুরোনো gradient ভুলে যায়)

---

## ✍️ Exam-Ready One-Line

**RMSProp is an adaptive optimization algorithm that maintains an exponentially decaying average of squared gradients to stabilize learning and prevent aggressive learning rate decay.**

---

চাও তো আমি পরের ধাপে

* **RMSProp numerical example (step-by-step)**
* **RMSProp vs Adam (graph + math)**
* **Why Adam = Momentum + RMSProp**

যেকোনোটা বুঝিয়ে দিতে পারি।
