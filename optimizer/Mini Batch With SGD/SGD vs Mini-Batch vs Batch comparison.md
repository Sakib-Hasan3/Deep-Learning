<<<<<<< HEAD
## **SGD vs Mini-Batch vs Batch Gradient Descent — Full Comparison (Easy + Exam-Ready)**

![Image](https://miro.medium.com/1%2AFXHp55rpDM0tkaD5oz3Dvg.png)

![Image](https://www.researchgate.net/publication/369740077/figure/fig2/AS%3A11431281136661792%401680549836475/Comparison-of-the-optimization-paths-for-gradient-descent-training-GD-and-the-solutions.ppm)

![Image](https://miro.medium.com/1%2AbKSddSmLDaYszWllvQ3Z6A.png)

---

## 🔹 1️⃣ Basic Idea (এক লাইনে)

* **Batch GD** → সব data একসাথে → একবার update
* **SGD** → ১টা sample → সাথে সাথে update
* **Mini-Batch SGD** → কয়েকটা sample → average করে update

---

## 🔹 2️⃣ How Weight Update Happens

ধরি total dataset size = (N)


### 🔸 Batch Gradient Descent
$$
	heta \leftarrow \theta - \eta \frac{1}{N} \sum_{i=1}^{N} \nabla \ell_i
$$


### 🔸 Stochastic Gradient Descent (SGD)
$$
	heta \leftarrow \theta - \eta \nabla \ell_i
$$
(একটা sample)


### 🔸 Mini-Batch SGD
$$
	heta \leftarrow \theta - \eta \frac{1}{m} \sum_{i=1}^{m} \nabla \ell_i
$$
($m$ = batch size, যেমন 32/64)

---

## 🔹 3️⃣ Core Comparison Table (Most Important)

| Feature            | Batch GD      | SGD         | Mini-Batch SGD    |
| ------------------ | ------------- | ----------- | ----------------- |
| Samples per update | All (N)       | 1           | Few (m)           |
| Update speed       | ❌ Slow        | ✅ Very fast | ✅ Fast            |
| Stability          | ✅ Very stable | ❌ Noisy     | ✅ Balanced        |
| Memory usage       | ❌ High        | ✅ Very low  | ✅ Moderate        |
| Convergence        | Smooth        | Zig-zag     | Smooth-ish        |
| GPU efficiency     | ❌ Poor        | ❌ Poor      | ✅ Excellent       |
| Practical use      | Rare          | Rare        | ⭐ **Most common** |

---

## 🔹 4️⃣ Intuition (সহজভাবে বোঝা)

### 🐢 Batch GD

* পুরো পাহাড়ের ম্যাপ দেখে নামা
* ধীর কিন্তু নিশ্চিত

### 🐇 SGD

* চোখ বন্ধ করে দৌড়ানো
* দ্রুত কিন্তু এদিক-ওদিক

### 🐎 Mini-Batch

* ছোট ম্যাপ দেখে দৌড়ানো
* দ্রুত + নিয়ন্ত্রিত

---

## 🔹 5️⃣ Noise vs Convergence

* **Batch GD:**

  * Smooth path
  * Exact minimum খুঁজে পায়
* **SGD:**

  * High noise
  * Minimum-এর আশেপাশে ঘোরে
* **Mini-Batch:**

  * Moderate noise
  * Stable minimum-এর কাছে পৌঁছায়

---

## 🔹 6️⃣ Epoch, Iteration Difference

ধরি:

* Dataset = 1000 samples
* Batch size = 100

| Method     | Iterations per epoch |
| ---------- | -------------------- |
| Batch GD   | 1                    |
| SGD        | 1000                 |
| Mini-Batch | 10                   |

---

## 🔹 7️⃣ When to Use Which?

### ✅ Use **Batch GD** when:

* Dataset খুব ছোট
* Memory issue নেই
* Mathematical clarity দরকার

### ✅ Use **SGD** when:

* Streaming / online data
* Extremely large dataset
* Very fast rough learning দরকার

### ✅ Use **Mini-Batch SGD** when:

* Deep learning
* GPU/TPU ব্যবহার
* Real-world large dataset

👉 **Industry default = Mini-Batch SGD**

---

## 🧠 Memory Trick

> **Batch = Slow & Stable**
> **SGD = Fast & Noisy**
> **Mini-Batch = Fast + Stable (Best)**

---

## ✍️ Exam-Ready One-Line Answer

> **Batch gradient descent uses all data per update, SGD uses one sample per update causing noisy convergence, while mini-batch gradient descent balances speed and stability by updating with a small subset of data.**

---

=======
## **SGD vs Mini-Batch vs Batch Gradient Descent — Full Comparison (Easy + Exam-Ready)**

![Image](https://miro.medium.com/1%2AFXHp55rpDM0tkaD5oz3Dvg.png)

![Image](https://www.researchgate.net/publication/369740077/figure/fig2/AS%3A11431281136661792%401680549836475/Comparison-of-the-optimization-paths-for-gradient-descent-training-GD-and-the-solutions.ppm)

![Image](https://miro.medium.com/1%2AbKSddSmLDaYszWllvQ3Z6A.png)

---

## 🔹 1️⃣ Basic Idea (এক লাইনে)

* **Batch GD** → সব data একসাথে → একবার update
* **SGD** → ১টা sample → সাথে সাথে update
* **Mini-Batch SGD** → কয়েকটা sample → average করে update

---

## 🔹 2️⃣ How Weight Update Happens

ধরি total dataset size = (N)


### 🔸 Batch Gradient Descent
$$
	heta \leftarrow \theta - \eta \frac{1}{N} \sum_{i=1}^{N} \nabla \ell_i
$$


### 🔸 Stochastic Gradient Descent (SGD)
$$
	heta \leftarrow \theta - \eta \nabla \ell_i
$$
(একটা sample)


### 🔸 Mini-Batch SGD
$$
	heta \leftarrow \theta - \eta \frac{1}{m} \sum_{i=1}^{m} \nabla \ell_i
$$
($m$ = batch size, যেমন 32/64)

---

## 🔹 3️⃣ Core Comparison Table (Most Important)

| Feature            | Batch GD      | SGD         | Mini-Batch SGD    |
| ------------------ | ------------- | ----------- | ----------------- |
| Samples per update | All (N)       | 1           | Few (m)           |
| Update speed       | ❌ Slow        | ✅ Very fast | ✅ Fast            |
| Stability          | ✅ Very stable | ❌ Noisy     | ✅ Balanced        |
| Memory usage       | ❌ High        | ✅ Very low  | ✅ Moderate        |
| Convergence        | Smooth        | Zig-zag     | Smooth-ish        |
| GPU efficiency     | ❌ Poor        | ❌ Poor      | ✅ Excellent       |
| Practical use      | Rare          | Rare        | ⭐ **Most common** |

---

## 🔹 4️⃣ Intuition (সহজভাবে বোঝা)

### 🐢 Batch GD

* পুরো পাহাড়ের ম্যাপ দেখে নামা
* ধীর কিন্তু নিশ্চিত

### 🐇 SGD

* চোখ বন্ধ করে দৌড়ানো
* দ্রুত কিন্তু এদিক-ওদিক

### 🐎 Mini-Batch

* ছোট ম্যাপ দেখে দৌড়ানো
* দ্রুত + নিয়ন্ত্রিত

---

## 🔹 5️⃣ Noise vs Convergence

* **Batch GD:**

  * Smooth path
  * Exact minimum খুঁজে পায়
* **SGD:**

  * High noise
  * Minimum-এর আশেপাশে ঘোরে
* **Mini-Batch:**

  * Moderate noise
  * Stable minimum-এর কাছে পৌঁছায়

---

## 🔹 6️⃣ Epoch, Iteration Difference

ধরি:

* Dataset = 1000 samples
* Batch size = 100

| Method     | Iterations per epoch |
| ---------- | -------------------- |
| Batch GD   | 1                    |
| SGD        | 1000                 |
| Mini-Batch | 10                   |

---

## 🔹 7️⃣ When to Use Which?

### ✅ Use **Batch GD** when:

* Dataset খুব ছোট
* Memory issue নেই
* Mathematical clarity দরকার

### ✅ Use **SGD** when:

* Streaming / online data
* Extremely large dataset
* Very fast rough learning দরকার

### ✅ Use **Mini-Batch SGD** when:

* Deep learning
* GPU/TPU ব্যবহার
* Real-world large dataset

👉 **Industry default = Mini-Batch SGD**

---

## 🧠 Memory Trick

> **Batch = Slow & Stable**
> **SGD = Fast & Noisy**
> **Mini-Batch = Fast + Stable (Best)**

---

## ✍️ Exam-Ready One-Line Answer

> **Batch gradient descent uses all data per update, SGD uses one sample per update causing noisy convergence, while mini-batch gradient descent balances speed and stability by updating with a small subset of data.**

---

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
