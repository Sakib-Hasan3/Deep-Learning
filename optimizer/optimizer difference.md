---

# 🔥 Gradient Descent Optimizers — Complete Comparison

---

## 1️⃣ Batch Gradient Descent (BGD)

**Idea:**
পুরো dataset ব্যবহার করে একবার update

**Update:**
সব data → এক gradient → এক update

**Pros**

* Stable convergence
* Exact gradient

**Cons**

* Slow
* Large dataset-এ impractical
* Memory heavy

---

## 2️⃣ Stochastic Gradient Descent (SGD)

**Idea:**
একটা data point → এক update

**Pros**

* Fast updates
* Memory efficient
* Escapes local minima

**Cons**

* Noisy
* Zig-zag path
* Slow convergence

---

## 3️⃣ Mini-Batch SGD

**Idea:**
ছোট batch (32, 64, 128) ব্যবহার করে update

**Pros**

* Stable + fast
* GPU friendly
* Most practical

**Cons**

* Batch size tune করতে হয়

👉 **Industry standard base method**

---

## 4️⃣ SGD with Momentum

**Idea:**
আগের gradient মনে রাখে (velocity)

**Key Point:**
Direction + speed

**Pros**

* Zig-zag কমে
* Faster convergence
* Stable

**Cons**

* Extra hyperparameter (β)

---

## 5️⃣ Adagrad

**Idea:**
Per-parameter adaptive learning rate
(All past squared gradients জমা)

**Pros**

* Sparse data-তে excellent
* Rare feature fast learns

**Cons**

* Learning rate খুব দ্রুত 0 হয়ে যায়
* Long training-এ থেমে যায়

---

## 6️⃣ RMSProp

**Idea:**
Adagrad কিন্তু **recent gradients** ব্যবহার করে

**Key Fix:**
Old gradients ভুলে যায়

**Pros**

* Stable learning
* Non-stationary problems-এ ভালো
* Deep learning-এ effective

**Cons**

* Momentum নেই
* Adam-এর তুলনায় slow

---

## 7️⃣ Adam (Adaptive Moment Estimation)

**Idea:**
Momentum + RMSProp

* First moment → mean (m)
* Second moment → variance (v)

**Pros**

* Very fast convergence
* Adaptive learning rate
* Sparse + deep networks-এ excellent
* Default choice

**Cons**

* Sometimes poor generalization
* Over-adaptive

---

## 8️⃣ AdamW

**Idea:**
Adam + **True Weight Decay**

**Key Fix:**
Regularization gradient থেকে আলাদা

**Pros**

* Better generalization
* Correct weight decay
* Transformer models-এ standard

**Cons**

* Slightly more complex

---

# 📊 One-Shot Comparison Table (Very Important)

| Optimizer      | Adaptive LR | Momentum | Sparse Data | Stability | Used Today |
| -------------- | ----------- | -------- | ----------- | --------- | ---------- |
| Batch GD       | ❌           | ❌        | ❌           | ✅         | ❌          |
| SGD            | ❌           | ❌        | ❌           | ❌         | ⚠️         |
| Mini-Batch SGD | ❌           | ❌        | ❌           | ✅         | ✅          |
| SGD + Momentum | ❌           | ✅        | ❌           | ✅         | ✅          |
| Adagrad        | ✅           | ❌        | ✅           | ❌         | ❌          |
| RMSProp        | ✅           | ❌        | ✅           | ✅         | ⚠️         |
| Adam           | ✅           | ✅        | ✅           | ⭐         | ✅          |
| AdamW          | ✅           | ✅        | ✅           | ⭐⭐        | ⭐⭐⭐        |

---

## 🧠 Memory Trick (Golden)

* **SGD** → noisy walker
* **Momentum** → rolling ball
* **Adagrad** → runs out of fuel
* **RMSProp** → forgets old mistakes
* **Adam** → smart + fast
* **AdamW** → smart + disciplined

---

## ✍️ Exam-Ready Final Lines

* **Best default optimizer:** Adam
* **Best for Transformers:** AdamW
* **Best generalization:** SGD + Momentum
* **Best for sparse data:** Adagrad / Adam

---

