---

# 🔹 Weight Initialization Techniques

## ❓ Weight Initialization কী?

Neural Network train করার আগে প্রতিটা neuron-এর weight-এ **শুরুর মান বসানোকে** Weight Initialization বলে।

ভুল initialization হলে:

* ❌ Vanishing Gradient
* ❌ Exploding Gradient
* ❌ Training slow বা fail

---

## 🎯 লক্ষ্য (Why important?)

Weight এমন হতে হবে যেন:

* Gradient খুব ছোট না হয়
* Gradient খুব বড় না হয়
* Signal forward & backward দুই দিকেই stable থাকে

---

## 🚫 খারাপ উদাহরণ

### 1️⃣ সব weight = 0

```math
w = 0
```

সমস্যা:

* সব neuron একই output দেবে
* সব gradient একই হবে
* Network কিছুই শিখবে না
  ➡️ **Symmetry Problem**

---

### 2️⃣ খুব বড় random weight

```math
w \sim \mathcal{N}(0, 10)
```

সমস্যা:

* Activation saturate করে
* Exploding Gradient

---

## ✅ ভালো Initialization Techniques

---

## 1️⃣ Random Initialization (Basic)

```math
w \sim \mathcal{N}(0, 0.01)
```

✔️ Symmetry ভাঙে
❌ Deep network-এর জন্য ভালো না

---

## 2️⃣ Xavier / Glorot Initialization

### 🎯 কখন ব্যবহার?

* **Sigmoid**
* **Tanh**

---

### 📐 Formula

```math
w \sim U\left(-\sqrt{\frac{6}{n_{in}+n_{out}}},
\sqrt{\frac{6}{n_{in}+n_{out}}}\right)
```

```math
w \sim \mathcal{N}\left(0, \frac{2}{n_{in}+n_{out}}\right)
```

---

### 🧠 Intuition

* Forward ও backward signal-এর variance সমান রাখে
* Gradient neither vanish nor explode

---

### 🔢 Example

ধরি:

* Input neuron = 100
* Output neuron = 50

```math
\sqrt{\frac{6}{150}} = \sqrt{0.04} = 0.2
```

Weight range:
```math
[-0.2, +0.2]
```

---

## 3️⃣ He Initialization

### 🎯 কখন ব্যবহার?

* **ReLU**
* **Leaky ReLU**
* **ELU**

---

### 📐 Formula

```math
w \sim \mathcal{N}\left(0, \frac{2}{n_{in}}\right)
```

```math
w \sim U\left(-\sqrt{\frac{6}{n_{in}}},
\sqrt{\frac{6}{n_{in}}}\right)
```

---

### 🧠 Intuition

ReLU অর্ধেক neuron deactivate করে (negative অংশ)

➡️ তাই variance বাড়ানো দরকার

---

### 🔢 Example

ধরি:

* Input neuron = 100

```math
\sqrt{\frac{6}{100}} = \sqrt{0.06} \approx 0.245
```

Weight range:
```math
[-0.245, +0.245]
```

---

## 4️⃣ LeCun Initialization

### 🎯 কখন ব্যবহার?

* **SELU**
* **Self-Normalizing Networks**

---

### 📐 Formula

```math
w \sim \mathcal{N}\left(0, \frac{1}{n_{in}}\right)
```

```math
w \sim U\left(-\sqrt{\frac{3}{n_{in}}},
\sqrt{\frac{3}{n_{in}}}\right)
```

---

## 5️⃣ Orthogonal Initialization

```math
W^T W = I
```

✔️ Gradient stable থাকে
✔️ RNN-এ ভালো কাজ করে
❌ Compute expensive

---

## 📊 Comparison Table

| Initialization | Best For         | Activation    | Problem Solved  |
| -------------- | ---------------- | ------------- | --------------- |
| Random         | Shallow NN       | Any           | Symmetry        |
| Xavier         | Medium / Deep    | Sigmoid, Tanh | Vanishing       |
| He             | Deep NN          | ReLU family   | Vanishing       |
| LeCun          | Self-normalizing | SELU          | Stable variance |
| Orthogonal     | RNN              | Any           | Exploding       |

---

## 🧠 পরীক্ষার জন্য Key Points

* Sigmoid/Tanh → **Xavier**
* ReLU family → **He**
* SELU → **LeCun**
* RNN → **Orthogonal**

---

## 🔗 Weight Init vs Gradient Problem

| Weight      | Result             |
| ----------- | ------------------ |
| Too small   | Vanishing Gradient |
| Too large   | Exploding Gradient |
| Proper init | Stable training    |

---

## ✍️ এক লাইনের সংজ্ঞা

> **Weight Initialization হল neural network training শুরু করার আগে এমনভাবে weight সেট করা যাতে forward ও backward signal stable থাকে।**

---

