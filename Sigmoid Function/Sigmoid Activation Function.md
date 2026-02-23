<<<<<<< HEAD
### **Sigmoid Activation Function**

---

## 🔹 1. Definition

**Sigmoid activation function** একটি non-linear function যা neural network-এ neuron-এর output কে **0 এবং 1 এর মধ্যে** সীমাবদ্ধ করে।

গাণিতিকভাবে,

[
\sigma(x) = \frac{1}{1 + e^{-x}}
]

---

## 🔹 2. Output Range

[
0 < \sigma(x) < 1
]

👉 তাই sigmoid বিশেষভাবে **probability output** (যেমন binary classification) এর জন্য ব্যবহার করা হয়।

---

## 🔹 3. Graph Behavior (বোঝার জন্য)

* (x \rightarrow +\infty \Rightarrow \sigma(x) \approx 1)
* (x \rightarrow -\infty \Rightarrow \sigma(x) \approx 0)
* (x = 0 \Rightarrow \sigma(0) = 0.5)

👉 S-shaped curve (smooth & continuous)

---

## 🔹 4. Derivative (Backpropagation-এ ব্যবহৃত)

[
\frac{d}{dx}[\sigma(x)] = \sigma(x),(1 - \sigma(x))
]

Maximum value:

[
\max(\sigma'(x)) = 0.25
]

---

## 🔹 5. Why Sigmoid is Used?

✔ Non-linear mapping
✔ Smooth gradient
✔ Output can be interpreted as probability
✔ Suitable for **binary classification output layer**

---

## 🔹 6. Sigmoid in ANN Learning (Intuition)

* Input weighted sum → sigmoid
* Output বলে দেয় **“হ্যাঁ না হওয়ার সম্ভাবনা”**
* Backpropagation-এ derivative দিয়ে weight update হয়

👉 Example:
[
y = 0.87 \Rightarrow 87% \text{ probability}
]

---

## 🔹 7. Advantages

✔ Simple and smooth
✔ Differentiable everywhere
✔ Probabilistic output
✔ Historically important

---

## 🔹 8. Disadvantages

❌ **Vanishing Gradient Problem**
❌ Not zero-centered
❌ Slow convergence
❌ Saturation at extreme values

---

## 🔹 9. Where Sigmoid is Used Today?

✅ Output layer (Binary classification)
❌ Hidden layers (deep networks)

---

## 🔹 10. Small Numerical Example

ধরি,
[
x = 2
]

[
\sigma(2) = \frac{1}{1+e^{-2}} \approx 0.88
]

Derivative:
[
\sigma'(2) = 0.88(1-0.88) = 0.1056
]

---

## 🔑 Exam-Ready One Line

> **Sigmoid is a smooth, non-linear activation function with output range (0,1), commonly used in the output layer for binary classification but prone to vanishing gradient in deep networks.**

---

## 🧠 One-Line Memory Trick

> **Sigmoid = Probability output + Vanishing gradient risk**


=======
### **Sigmoid Activation Function**

---

## 🔹 1. Definition

**Sigmoid activation function** একটি non-linear function যা neural network-এ neuron-এর output কে **0 এবং 1 এর মধ্যে** সীমাবদ্ধ করে।

গাণিতিকভাবে,

[
\sigma(x) = \frac{1}{1 + e^{-x}}
]

---

## 🔹 2. Output Range

[
0 < \sigma(x) < 1
]

👉 তাই sigmoid বিশেষভাবে **probability output** (যেমন binary classification) এর জন্য ব্যবহার করা হয়।

---

## 🔹 3. Graph Behavior (বোঝার জন্য)

* (x \rightarrow +\infty \Rightarrow \sigma(x) \approx 1)
* (x \rightarrow -\infty \Rightarrow \sigma(x) \approx 0)
* (x = 0 \Rightarrow \sigma(0) = 0.5)

👉 S-shaped curve (smooth & continuous)

---

## 🔹 4. Derivative (Backpropagation-এ ব্যবহৃত)

[
\frac{d}{dx}[\sigma(x)] = \sigma(x),(1 - \sigma(x))
]

Maximum value:

[
\max(\sigma'(x)) = 0.25
]

---

## 🔹 5. Why Sigmoid is Used?

✔ Non-linear mapping
✔ Smooth gradient
✔ Output can be interpreted as probability
✔ Suitable for **binary classification output layer**

---

## 🔹 6. Sigmoid in ANN Learning (Intuition)

* Input weighted sum → sigmoid
* Output বলে দেয় **“হ্যাঁ না হওয়ার সম্ভাবনা”**
* Backpropagation-এ derivative দিয়ে weight update হয়

👉 Example:
[
y = 0.87 \Rightarrow 87% \text{ probability}
]

---

## 🔹 7. Advantages

✔ Simple and smooth
✔ Differentiable everywhere
✔ Probabilistic output
✔ Historically important

---

## 🔹 8. Disadvantages

❌ **Vanishing Gradient Problem**
❌ Not zero-centered
❌ Slow convergence
❌ Saturation at extreme values

---

## 🔹 9. Where Sigmoid is Used Today?

✅ Output layer (Binary classification)
❌ Hidden layers (deep networks)

---

## 🔹 10. Small Numerical Example

ধরি,
[
x = 2
]

[
\sigma(2) = \frac{1}{1+e^{-2}} \approx 0.88
]

Derivative:
[
\sigma'(2) = 0.88(1-0.88) = 0.1056
]

---

## 🔑 Exam-Ready One Line

> **Sigmoid is a smooth, non-linear activation function with output range (0,1), commonly used in the output layer for binary classification but prone to vanishing gradient in deep networks.**

---

## 🧠 One-Line Memory Trick

> **Sigmoid = Probability output + Vanishing gradient risk**


>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
