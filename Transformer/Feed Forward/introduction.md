
# What is a Feed Forward Network (FFN)?

**Feed Forward Network (FFN)** হলো সবচেয়ে basic neural network structure যেখানে তথ্য একদিকে প্রবাহিত হয়:

```text
Input → Hidden Layer(s) → Output
```

এখানে কোনো feedback loop বা recurrence নেই।
তথ্য forward direction-এ যায় — তাই নাম **Feed Forward**।

---

# 1️⃣ Basic Structure

একটি সাধারণ FFN-এ থাকে:

* Input layer
* 1 বা একাধিক hidden layer
* Output layer
* Activation function

---

## Mathematical Form (Single Hidden Layer)

$$
y = W_2\,\sigma\left(W_1 x + b_1\right) + b_2
$$

Where:

* $x$ = input vector
* $W_1, W_2$ = weight matrices
* $b_1, b_2$ = biases
* $\sigma$ = activation (ReLU, GELU, sigmoid, etc.)

---

# 2️⃣ Simple Numeric Example

ধরি:

$$
x = [2, 3]
$$

ধরি:


$$
W_1 = \begin{bmatrix} 1 & 0 \\
0 & 1 \end{bmatrix}
$$

$$
b_1 = [1, 1]
$$

### Step 1: Linear

$$
z = W_1 x + b_1 = [2, 3] + [1, 1] = [3, 4]
$$

### Step 2: Activation (ReLU)

$$
\mathrm{ReLU}([3, 4]) = [3, 4]
$$

### Step 3: Second Linear

ধরি (W_2 = I)

Final output = [3,4]

---

# 3️⃣ Why It Is Important?

FFN:

✔ Non-linearity যোগ করে
✔ Feature transformation করে
✔ Model-কে complex pattern শেখায়

Without activation → network purely linear হয়ে যায়।

---

# 4️⃣ In Transformer Context

Transformer-এ FFN:

* প্রতিটি token-এ independently apply হয়
* Attention-এর পরে representation refine করে

Typical dimension:

$$
d_{\mathrm{model}} = 512
$$

$$
d_{ff} = 2048
$$

Structure:

```text
512 → 2048 → 512
```

---

# 5️⃣ Intuitive Meaning

Attention করে:

> “কোন token গুরুত্বপূর্ণ?”

FFN করে:

> “এই তথ্য দিয়ে কী নতুন feature তৈরি করবো?”

---

# 6️⃣ FFN vs Attention

| Attention         | Feed Forward         |
| ----------------- | -------------------- |
| Token interaction | Token transformation |
| Global mixing     | Local refinement     |
| Context creation  | Feature extraction   |

---

# 7️⃣ Visual Concept

![Image](https://images.openai.com/static-rsc-3/HsvMPdOGd41XTtbO7G2sfFPG7GjlvzBnT63Ax4ZzHPQSd1W8z5A3u7ksK_uhX87fz2PkvQ0spOLCxA5avyxtY19agBPRzzX_8SG-qMPMaYA?purpose=fullsize\&v=1)

![Image](https://images.openai.com/static-rsc-3/wTaYCHV1c3BYs0-HiugQ41UkG03D49yg0MSZg9CCJ_ZNLqOvkT3mJJtrIV9H9VWQhhPp55CxdGa6JhK60ApfWUwv_PcLeWv9OYKflblXkBU?purpose=fullsize\&v=1)

![Image](https://www.researchgate.net/publication/348703101/figure/fig3/AS%3A983057658019843%401611390618534/Graphic-representation-of-the-ReLU-activation-function.ppm)

![Image](https://www.researchgate.net/publication/343675998/figure/fig3/AS%3A924834280267785%401597509083229/Graph-of-ReLu-activation-function.ppm)

---

# 8️⃣ Key Insight

Feed Forward Network হলো:

> Linear transformation + Nonlinear activation + Linear projection

এটাই deep learning-এর backbone।

---
