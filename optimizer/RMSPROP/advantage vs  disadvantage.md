<<<<<<< HEAD
## **RMSProp — Advantage vs Disadvantage (সংক্ষেপে, Exam-Ready)**

---

## ✅ **Advantages of RMSProp**

1. **Adaptive Learning Rate (per-parameter)**
   প্রতিটি parameter-এর জন্য আলাদা learning rate adjust হয়।

2. **Adagrad-এর সমস্যা সমাধান করে**
   Learning rate আর একদম 0 হয়ে যায় না—training থেমে যায় না।

3. **Non-stationary problems-এ ভালো**
   Loss landscape সময়ের সাথে বদলালেও ভালো কাজ করে।

4. **Zig-zag কমায়**
   Steep + narrow valley-তে movement smoother হয়।

5. **Deep Learning-এ কার্যকর**
   বিশেষ করে **RNN / LSTM**-এ খুব জনপ্রিয়।

---

## ❌ **Disadvantages of RMSProp**

1. **Momentum আলাদা করে নেই**
   Directional acceleration নেই (Adam-এ এটা আছে)।

2. **Hyperparameter tune করতে হয়**
   Learning rate (η), decay rate (ρ) ঠিক করা লাগে।

3. **Adam-এর তুলনায় ধীর**
   Adam সাধারণত আরও দ্রুত ও stable converge করে।

4. **Theoretical guarantee দুর্বল**
   Strong convergence proof নেই (SGD-এর মতো নয়)।

---

## 📊 **Quick Comparison**

| Feature          | RMSProp       |
| ---------------- | ------------- |
| Learning rate    | Adaptive      |
| Sparse data      | ✅ Good        |
| Long training    | ✅ Stable      |
| Momentum         | ❌ No          |
| Used in practice | RNN, DL       |
| Replaced by      | Adam (mostly) |

---

## 🧠 **Memory Trick**

> **RMSProp = Adagrad with memory loss (but no momentum)**

---

## ✍️ **Exam-Ready One-Liners**

* **Advantage:**
  *RMSProp stabilizes learning by using an exponentially decaying average of squared gradients.*

* **Disadvantage:**
  *RMSProp lacks momentum and is often outperformed by Adam in practice.*

=======
## **RMSProp — Advantage vs Disadvantage (সংক্ষেপে, Exam-Ready)**

---

## ✅ **Advantages of RMSProp**

1. **Adaptive Learning Rate (per-parameter)**
   প্রতিটি parameter-এর জন্য আলাদা learning rate adjust হয়।

2. **Adagrad-এর সমস্যা সমাধান করে**
   Learning rate আর একদম 0 হয়ে যায় না—training থেমে যায় না।

3. **Non-stationary problems-এ ভালো**
   Loss landscape সময়ের সাথে বদলালেও ভালো কাজ করে।

4. **Zig-zag কমায়**
   Steep + narrow valley-তে movement smoother হয়।

5. **Deep Learning-এ কার্যকর**
   বিশেষ করে **RNN / LSTM**-এ খুব জনপ্রিয়।

---

## ❌ **Disadvantages of RMSProp**

1. **Momentum আলাদা করে নেই**
   Directional acceleration নেই (Adam-এ এটা আছে)।

2. **Hyperparameter tune করতে হয়**
   Learning rate (η), decay rate (ρ) ঠিক করা লাগে।

3. **Adam-এর তুলনায় ধীর**
   Adam সাধারণত আরও দ্রুত ও stable converge করে।

4. **Theoretical guarantee দুর্বল**
   Strong convergence proof নেই (SGD-এর মতো নয়)।

---

## 📊 **Quick Comparison**

| Feature          | RMSProp       |
| ---------------- | ------------- |
| Learning rate    | Adaptive      |
| Sparse data      | ✅ Good        |
| Long training    | ✅ Stable      |
| Momentum         | ❌ No          |
| Used in practice | RNN, DL       |
| Replaced by      | Adam (mostly) |

---

## 🧠 **Memory Trick**

> **RMSProp = Adagrad with memory loss (but no momentum)**

---

## ✍️ **Exam-Ready One-Liners**

* **Advantage:**
  *RMSProp stabilizes learning by using an exponentially decaying average of squared gradients.*

* **Disadvantage:**
  *RMSProp lacks momentum and is often outperformed by Adam in practice.*

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
