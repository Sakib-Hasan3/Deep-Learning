---


# 🔷 Setup

ধরি:

- Sequence length = 2 tokens
- Model dimension $d_{model} = 4$
- Number of heads $h = 2$

তাহলে:

$$
d_k = \dfrac{d_{model}}{h} = \dfrac{4}{2} = 2
$$

প্রতিটি head 2-dimensional space-এ কাজ করবে।

---

# 🔷 Input Matrix

ধরি আমাদের দুইটা token embedding:

$$
X =
\begin{bmatrix}
1 & 0 & 1 & 0 \\
0 & 1 & 0 & 1
\end{bmatrix}
$$

Shape: $(2 \times 4)$

---

# 🔷 Step 1: Split into 2 Heads

আমরা ধরছি projection এমনভাবে করা হয়েছে যেন:

Head 1 → প্রথম 2 dimension নেয়
Head 2 → শেষ 2 dimension নেয়

---

## 🔹 Head 1 Input

$$
X_1 =
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

---

## 🔹 Head 2 Input

$$
X_2 =
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

(সহজ বোঝার জন্য একই ধরলাম)

---

# 🔷 Step 2: Self-Attention per Head

### Head 1

### $Q = K = V = X_1$

$$
Q_1 = K_1 = V_1 =
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

---

### Score:

$$
S = QK^{\top} =
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

---

### Scaling

$$
\sqrt{d_k} = \sqrt{2} \approx 1.414
$$

$$
S' =
\begin{bmatrix}
0.707 & 0 \\
0 & 0.707
\end{bmatrix}
$$

---

### Softmax (row-wise)

Row1: $\mathrm{softmax}(0.707,0) \approx (0.67,\;0.33)$

Row2: $\mathrm{softmax}(0,0.707) \approx (0.33,\;0.67)$

Attention matrix:

$$
A_1 =
\begin{bmatrix}
0.67 & 0.33 \\
0.33 & 0.67
\end{bmatrix}
$$

---

### Output:

$$
Z_1 = A_1 V_1
$$

Token1 output:

$$
0.67[1,0] + 0.33[0,1] = [0.67,\;0.33]
$$

Token2 output:

$$
0.33[1,0] + 0.67[0,1] = [0.33,\;0.67]
$$

---

## 🔷 Head 2

একই process (ধরি different projection হলে আলাদা relation শিখত)

ধরি output:

$$
Z_2 =
\begin{bmatrix}
0.60 & 0.40 \\
0.40 & 0.60
\end{bmatrix}
$$

---

# 🔷 Step 3: Concatenate Heads

Head1 output (2 dim)
Head2 output (2 dim)

Concat করলে:

Token1:

$$
[0.67,\;0.33,\;0.60,\;0.40]
$$

Token2:

$$
[0.33,\;0.67,\;0.40,\;0.60]
$$

Shape আবার $(2 \times 4)$

---

# 🔷 Step 4: Final Linear Projection

$$
\mathrm{Output} = \mathrm{Concat}(Z_1,Z_2)W_O
$$

এখানে $W_O$ learnable matrix যা final mixing করে।

---

# 🔷 কী বোঝা গেল?

Multi-Head Attention:

- প্রতিটি head আলাদা representation space-এ কাজ করে
- আলাদা relation capture করে
- শেষে সব combine হয়

---

# 🔷 Intuitive Meaning

Head 1 → syntax ধরছে
Head 2 → semantic similarity ধরছে

একসাথে → richer contextual embedding

---

# 🔷 Why Better Than Single Head?

Single head = এক ধরনের similarity

Multi-head =

- Multiple subspace learning
- More expressive
- More stable training

---

