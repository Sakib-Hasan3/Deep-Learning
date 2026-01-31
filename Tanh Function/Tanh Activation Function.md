![Image](https://miro.medium.com/v2/resize%3Afit%3A756/1%2AtOc--h-QU9_bHqWLPY9YLA.png)

![Image](https://ronny.rest/media/blog/2017/2017_08_16_tanh/tanh_and_gradient.jpg)

![Image](https://www.researchgate.net/publication/341958919/figure/fig2/AS%3A903383875600391%401592394908731/Sigmoid-versus-tanh-functions-on-MNIST-Dataset-using-two-classic-functions.ppm)

![Image](https://i.sstatic.net/o0JA0.png)

---

## 🔹 1) Tanh কী?

**Tanh (Hyperbolic Tangent)** হলো একটি **non-linear activation function** যা ইনপুটকে **−1 থেকে +1** রেঞ্জে ম্যাপ করে।

গাণিতিকভাবে:
[
\tanh(x)=\frac{e^x-e^{-x}}{e^x+e^{-x}}
]

---

## 🔹 2) Output Range

[
-1 \le \tanh(x) \le +1
]

👉 Output **zero-centered** (0-এর চারপাশে), যা gradient descent-কে বেশি stable করে।

---

## 🔹 3) Graph দেখে Intuition (খুব গুরুত্বপূর্ণ)

### (a) Left Saturation (x ≪ 0)

* Output ≈ −1
* Derivative ≈ 0
* ❌ Learning ধীর/বন্ধ

### (b) Active / Linear Zone (x ≈ 0)

* Output ≈ 0
* Slope সবচেয়ে বেশি
* ✅ Learning fastest

### (c) Right Saturation (x ≫ 0)

* Output ≈ +1
* Derivative ≈ 0
* ❌ Learning ধীর

👉 মাঝখানের steep অংশে শেখা সবচেয়ে ভালো হয়।

---

## 🔹 4) Derivative (Backpropagation-এর জন্য)

[
\frac{d}{dx}[\tanh(x)] = 1-\tanh^2(x)
]

* (x=0) এ derivative সর্বোচ্চ (=1)
* |x| বড় হলে derivative → 0 (saturation)

---

## 🔹 5) কেন Tanh, Sigmoid-এর চেয়ে ভালো?

* **Zero-centered output** → weight update balanced
* **Stronger gradient near 0** → faster convergence
* Sigmoid-এর মতো হলেও **learning সাধারণত দ্রুত**

---

## 🔹 6) Vanishing Gradient আছে কি?

⚠️ হ্যাঁ, আছে—কিন্তু **sigmoid-এর চেয়ে কম**।
কারণ saturation region-এ derivative ছোট হয়ে যায়।

---

## 🔹 7) Numerical Example

ধরি (x=1):

[
\tanh(1)\approx 0.761
]
[
\text{Derivative}=1-(0.761)^2\approx 0.42
]

👉 Sigmoid-এর তুলনায় এখানে gradient বেশি।

---

## 🔹 8) কোথায় ব্যবহার করা হয়?

✅ **Hidden layers** (shallow/medium networks)
❌ খুব deep network হলে ReLU-family ভালো

---

## 🔹 9) Tanh vs Sigmoid (Graph-based তুলনা)

| Feature            | Sigmoid | Tanh   |
| ------------------ | ------- | ------ |
| Output range       | (0,1)   | (−1,1) |
| Zero-centered      | ❌       | ✅      |
| Learning speed     | Slower  | Faster |
| Vanishing gradient | High    | Medium |

---

## 🧠 Memory Trick

> **Tanh = Sigmoid but centered at zero → faster learning**

---

## ✍️ Exam-Ready One Line

> **Tanh is a zero-centered activation function with output range (−1, +1), offering faster convergence than sigmoid but still susceptible to vanishing gradients in deep networks.**
