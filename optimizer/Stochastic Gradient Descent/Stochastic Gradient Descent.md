<<<<<<< HEAD
## **SGD (Stochastic Gradient Descent) **

![Image](https://miro.medium.com/1%2Af9Wbr-pYMZ2AEzS2yp8EtQ.jpeg)

![Image](https://miro.medium.com/1%2AFXHp55rpDM0tkaD5oz3Dvg.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2Af9Wbr-pYMZ2AEzS2yp8EtQ.jpeg)

![Image](https://ketanhdoshi.github.io/assets/images/OptimizerTechniques/Momentum-2.png)

---

## 🔹 1️⃣ SGD কী?

**SGD (Stochastic Gradient Descent)** হলো Gradient Descent-এর একটি variant, যেখানে
👉 **একবারে মাত্র একটি training sample ব্যবহার করে weight update করা হয়**।

---

## 🔹 2️⃣ Basic Gradient Descent vs SGD

### 🔸 Batch Gradient Descent

* পুরো dataset ব্যবহার করে
* Update ধীর কিন্তু stable

### 🔸 **SGD**

* **একটা sample** দিয়ে update
* Update দ্রুত কিন্তু noisy

---

## 🔹 3️⃣ Mathematical Update Rule (SGD)

ধরি,

* (\theta) = model parameters
* (\eta) = learning rate
* ((x_i, y_i)) = একটিমাত্র data sample

তাহলে SGD update:

[
\theta \leftarrow \theta - \eta \nabla J(\theta; x_i, y_i)
]

👉 এখানে gradient হিসাব হয় **একটি sample-এর loss থেকে**।

---

## 🔹 4️⃣ Intuition (সহজ ভাষায়)

* Batch GD = পাহাড় নামা, পুরো ম্যাপ দেখে ধীরে ধীরে নামা
* **SGD = চোখ বন্ধ করে দৌড়ানো** 😄

  * কখনো ডানে
  * কখনো বামে
  * কিন্তু দ্রুত নিচের দিকে যায়

👉 Noise থাকলেও **average direction ঠিক থাকে**।

---

## 🔹 5️⃣ SGD Graph থেকে কী বোঝা যায়?

* Path zig-zag করে
* Minimum-এর আশেপাশে ঘুরে বেড়ায়
* Exact minimum-এ থামে না, কিন্তু কাছাকাছি থাকে

---

## 🔹 6️⃣ Advantages of SGD

✔ Very fast updates
✔ Large dataset-এ scalable
✔ Memory কম লাগে
✔ Local minima থেকে বের হতে সাহায্য করে

---

## 🔹 7️⃣ Disadvantages of SGD

❌ Convergence noisy
❌ Exact minimum-এ settle করে না
❌ Learning rate ঠিক না হলে unstable
❌ Zig-zag path (slow fine-tuning)

---

## 🔹 8️⃣ SGD কখন ব্যবহার করবে?

✅ Dataset খুব বড়
✅ Online / streaming data
✅ Simple baseline optimizer
✅ Time constraint আছে

---

## 🔹 9️⃣ SGD vs Mini-batch vs Batch

| Type          | Samples per update | Speed         | Stability |
| ------------- | ------------------ | ------------- | --------- |
| Batch GD      | All                | Slow          | High      |
| **SGD**       | **1**              | **Very Fast** | Low       |
| Mini-batch GD | 32–256             | Fast          | Medium    |

👉 বাস্তবে **Mini-batch** বেশি ব্যবহার হয়।

---

## 🧠 Memory Trick

> **SGD = Fast but noisy learner**

---

## ✍️ Exam-Ready One Line

> **Stochastic Gradient Descent updates model parameters using one training example at a time, enabling fast and scalable learning at the cost of noisy convergence.**

---

=======
## **SGD (Stochastic Gradient Descent) **

![Image](https://miro.medium.com/1%2Af9Wbr-pYMZ2AEzS2yp8EtQ.jpeg)

![Image](https://miro.medium.com/1%2AFXHp55rpDM0tkaD5oz3Dvg.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2Af9Wbr-pYMZ2AEzS2yp8EtQ.jpeg)

![Image](https://ketanhdoshi.github.io/assets/images/OptimizerTechniques/Momentum-2.png)

---

## 🔹 1️⃣ SGD কী?

**SGD (Stochastic Gradient Descent)** হলো Gradient Descent-এর একটি variant, যেখানে
👉 **একবারে মাত্র একটি training sample ব্যবহার করে weight update করা হয়**।

---

## 🔹 2️⃣ Basic Gradient Descent vs SGD

### 🔸 Batch Gradient Descent

* পুরো dataset ব্যবহার করে
* Update ধীর কিন্তু stable

### 🔸 **SGD**

* **একটা sample** দিয়ে update
* Update দ্রুত কিন্তু noisy

---

## 🔹 3️⃣ Mathematical Update Rule (SGD)

ধরি,

* (\theta) = model parameters
* (\eta) = learning rate
* ((x_i, y_i)) = একটিমাত্র data sample

তাহলে SGD update:

[
\theta \leftarrow \theta - \eta \nabla J(\theta; x_i, y_i)
]

👉 এখানে gradient হিসাব হয় **একটি sample-এর loss থেকে**।

---

## 🔹 4️⃣ Intuition (সহজ ভাষায়)

* Batch GD = পাহাড় নামা, পুরো ম্যাপ দেখে ধীরে ধীরে নামা
* **SGD = চোখ বন্ধ করে দৌড়ানো** 😄

  * কখনো ডানে
  * কখনো বামে
  * কিন্তু দ্রুত নিচের দিকে যায়

👉 Noise থাকলেও **average direction ঠিক থাকে**।

---

## 🔹 5️⃣ SGD Graph থেকে কী বোঝা যায়?

* Path zig-zag করে
* Minimum-এর আশেপাশে ঘুরে বেড়ায়
* Exact minimum-এ থামে না, কিন্তু কাছাকাছি থাকে

---

## 🔹 6️⃣ Advantages of SGD

✔ Very fast updates
✔ Large dataset-এ scalable
✔ Memory কম লাগে
✔ Local minima থেকে বের হতে সাহায্য করে

---

## 🔹 7️⃣ Disadvantages of SGD

❌ Convergence noisy
❌ Exact minimum-এ settle করে না
❌ Learning rate ঠিক না হলে unstable
❌ Zig-zag path (slow fine-tuning)

---

## 🔹 8️⃣ SGD কখন ব্যবহার করবে?

✅ Dataset খুব বড়
✅ Online / streaming data
✅ Simple baseline optimizer
✅ Time constraint আছে

---

## 🔹 9️⃣ SGD vs Mini-batch vs Batch

| Type          | Samples per update | Speed         | Stability |
| ------------- | ------------------ | ------------- | --------- |
| Batch GD      | All                | Slow          | High      |
| **SGD**       | **1**              | **Very Fast** | Low       |
| Mini-batch GD | 32–256             | Fast          | Medium    |

👉 বাস্তবে **Mini-batch** বেশি ব্যবহার হয়।

---

## 🧠 Memory Trick

> **SGD = Fast but noisy learner**

---

## ✍️ Exam-Ready One Line

> **Stochastic Gradient Descent updates model parameters using one training example at a time, enabling fast and scalable learning at the cost of noisy convergence.**

---

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
