## **Which Activation Function to Apply — When & Why (Quick Guide)**

![Image](https://www.researchgate.net/publication/317679065/figure/fig10/AS%3A654765507768342%401533119670534/Activation-functions-in-comparison-Red-curves-stand-for-respectively-sigmoid.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A2000/1%2A0GBatebNQ5WohnGF8frGqg.png)

![Image](https://media.licdn.com/dms/image/v2/D4D12AQH2F3GJ9wen_Q/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1688885174323?e=2147483647\&t=dY_S6xeNsRCIvpIrjrPFzq8qgHPgmP4e_HLaA15ufPM\&v=beta)

---

### 🔹 **1️⃣ Sigmoid — কখন ব্যবহার করবে?**

**Best for:**

* **Binary classification**
* **Output layer** (Yes/No, 0/1)

**Why:**

* Output দেয় **0–1** → probability হিসেবে ব্যাখ্যা করা যায়

**Avoid:**

* Hidden layers (vanishing gradient)

✅ **Use when:**

> *Only one output neuron + binary decision*

---

### 🔹 **2️⃣ Tanh — কখন ব্যবহার করবে?**

**Best for:**

* **Hidden layers** (shallow / medium networks)

**Why:**

* Output **−1 to +1**
* Zero-centered → faster learning than sigmoid

**Avoid:**

* Very deep networks (still vanishing gradient)

✅ **Use when:**

> *Hidden layer + data normalized around 0*

---

### 🔹 **3️⃣ ReLU — কখন ব্যবহার করবে?**

**Best for:**

* **Hidden layers (default choice)**
* **Deep neural networks / CNN**

**Why:**

* Fast
* Vanishing gradient কম
* Simple

**Issue:**

* Dead neuron problem

✅ **Use when:**

> *Deep network + speed & simplicity needed*

---

### 🔹 **4️⃣ Leaky ReLU — কখন ব্যবহার করবে?**

**Best for:**

* ReLU কাজ করছে না
* Dead neuron সমস্যা হচ্ছে

**Why:**

* Negative side-এও gradient থাকে

✅ **Use when:**

> *ReLU dead neuron দিচ্ছে*

---

### 🔹 **5️⃣ PReLU — কখন ব্যবহার করবে?**

**Best for:**

* Very deep CNN
* Large dataset

**Why:**

* Negative slope নিজে নিজে শেখে

**Caution:**

* Extra parameter → overfitting risk

✅ **Use when:**

> *Large data + model needs flexibility*

---

### 🔹 **6️⃣ ELU — কখন ব্যবহার করবে?**

**Best for:**

* Stable & smooth training
* Deep networks যেখানে ReLU unstable

**Why:**

* Negative output → bias shift কম
* Dead neuron প্রায় নেই

**Cost:**

* ReLU থেকে ধীর

✅ **Use when:**

> *Stability > speed*

---

### 🔹 **7️⃣ Softmax — কখন ব্যবহার করবে?**

**Best for:**

* **Multiclass classification**
* **Output layer**

**Why:**

* সব class-এর probability দেয়
* Sum = 1

✅ **Use when:**

> *One sample = one class (Cat/Dog/Cow)*

---

## 📊 **One-Glance Decision Table**

| Problem Type              | Activation (Hidden)           | Activation (Output) |
| ------------------------- | ----------------------------- | ------------------- |
| Binary classification     | ReLU / Tanh                   | **Sigmoid**         |
| Multiclass (single label) | ReLU / ELU                    | **Softmax**         |
| Deep CNN                  | **ReLU / Leaky ReLU / PReLU** | Softmax             |
| Shallow ANN               | Tanh                          | Sigmoid / Softmax   |
| Training unstable         | ELU                           | Depends             |
| Dead neuron issue         | Leaky ReLU / PReLU            | —                   |

---

## 🧠 **Golden Rule (Exam + Practice)**

> **Hidden layers → ReLU-family**
> **Binary output → Sigmoid**
> **Multiclass output → Softmax**

---

## ✍️ **Exam-Ready One Line**

> **Activation functions are chosen based on network depth and task: ReLU-family for hidden layers, sigmoid for binary output, and softmax for multiclass classification.**

