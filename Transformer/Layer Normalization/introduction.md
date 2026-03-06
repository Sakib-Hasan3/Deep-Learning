# Layer Normalization (Transformer-এ এর ধারণা ও গণিত)

**Layer Normalization (LayerNorm)** হলো একটি normalization technique যা neural network-এর activation values কে **stable scale**-এ রাখতে সাহায্য করে। এটি বিশেষ করে Transformer architecture-এ খুব গুরুত্বপূর্ণ।

---

# 1️⃣ কেন Layer Normalization দরকার?

Deep neural network training-এ সাধারণ সমস্যা:

* Gradient explosion
* Gradient vanishing
* Activation values খুব বড় বা ছোট হয়ে যাওয়া
* Training instability

LayerNorm activation values normalize করে training stable রাখে।

---

# 2️⃣ Basic Idea

ধরি একটি vector:

[
x = [x_1, x_2, ..., x_d]
]

LayerNorm প্রথমে mean এবং variance বের করে।

### Mean

[
\mu = \frac{1}{d} \sum_{i=1}^{d} x_i
]

### Variance

[
\sigma^2 = \frac{1}{d} \sum_{i=1}^{d}(x_i-\mu)^2
]

---

# 3️⃣ Normalization Step

প্রতিটি element normalize করা হয়:

[
\hat{x_i} = \frac{x_i - \mu}{\sqrt{\sigma^2 + \epsilon}}
````markdown
# Layer Normalization (Transformer-এ এর ধারণা ও গণিত)

**Layer Normalization (LayerNorm)** হলো একটি normalization technique যা neural network-এর activation values কে **stable scale**-এ রাখতে সাহায্য করে। এটি বিশেষ করে Transformer architecture-এ খুব গুরুত্বপূর্ণ।

---

# 1️⃣ কেন Layer Normalization দরকার?

Deep neural network training-এ সাধারণ সমস্যা:

- Gradient explosion
- Gradient vanishing
- Activation values খুব বড় বা ছোট হয়ে যাওয়া
- Training instability

LayerNorm activation values normalize করে training stable রাখে।

---

# 2️⃣ Basic Idea

ধরি একটি vector:

$$
x = [x_1, x_2, ..., x_d]
$$

LayerNorm প্রথমে mean এবং variance বের করে।

### Mean

$$
\mu = \frac{1}{d} \sum_{i=1}^{d} x_i
$$

### Variance

$$
\sigma^2 = \frac{1}{d} \sum_{i=1}^{d}(x_i-\mu)^2
$$

---

# 3️⃣ Normalization Step

প্রতিটি element normalize করা হয়:

$$
\hat{x_i} = \frac{x_i - \mu}{\sqrt{\sigma^2 + \epsilon}}
$$

এখানে

- (\epsilon) = small constant (numerical stability)

---

# 4️⃣ Scale and Shift

Normalization করার পরে model learnable parameters ব্যবহার করে:

$$
y_i = \gamma \hat{x_i} + \beta
$$

Where:

- (\gamma) = scale parameter
- (\beta) = shift parameter

এই parameters training-এ learn হয়।

---

# 5️⃣ Simple Numeric Example

ধরি

$$
x = [2,4,6]
$$

### Step 1: Mean

$$
\mu = (2+4+6)/3 = 4
$$

### Step 2: Variance

$$
\sigma^2 = ((2-4)^2+(4-4)^2+(6-4)^2)/3
$$

$$
= (4+0+4)/3 = 2.67
$$

### Step 3: Standard deviation

$$
\sigma = \sqrt{2.67} \approx 1.63
$$

### Step 4: Normalize

$$
(2-4)/1.63 \approx -1.23
$$

$$
(4-4)/1.63 = 0
$$

$$
(6-4)/1.63 \approx 1.23
$$

Normalized output:

$$
[-1.23,0,1.23]
$$

---

# 6️⃣ Transformer-এ LayerNorm কোথায় থাকে?

Transformer encoder block:

```text
Input
  ↓
Multi-Head Attention
  ↓
Add + LayerNorm
  ↓
Feed Forward Network
  ↓
Add + LayerNorm
```

এখানে:

- Residual connection + normalization
- Stable gradient flow

---

# 7️⃣ LayerNorm vs BatchNorm

| Feature               | BatchNorm | LayerNorm |
| --------------------- | --------- | --------- |
| Normalization axis    | Batch     | Feature   |
| Sequence models       | Poor      | Good      |
| Transformer use       | No        | Yes       |
| Batch size dependency | Yes       | No        |

---

# 8️⃣ Mathematical Insight

LayerNorm essentially feature-wise standardization:

$$
y = \gamma \frac{x - \mu}{\sqrt{\sigma^2+\epsilon}} + \beta
$$

এতে activation distribution stable হয়।

---

# 9️⃣ Why Important for Transformers?

Transformer-এ

- Attention outputs large scale-এ যেতে পারে
- Deep stacking (12-96 layers)

LayerNorm ensures:

- Stable gradient
- Faster convergence
- Better training

---

# 🔟 Core Intuition

LayerNorm basically বলে:

> "এই layer-এর output-কে standard scale-এ নিয়ে আসো যাতে training stable থাকে"

---

✅ **Short summary**

Layer Normalization:

- activation values normalize করে
- training stable করে
- transformer-এ essential component

---
 
````

