---

## 0) Setup (৩টা token)

ধরি আমাদের ৩টা token embedding:

- $x_1 = [1,\;0]$
- $x_2 = [0,\;1]$
- $x_3 = [1,\;1]$

এগুলো নিয়ে matrix (X) (৩×২):

$$
X =
\begin{bmatrix}
1 & 0 \\
0 & 1 \\
1 & 1
\end{bmatrix}
$$

এখন সহজতার জন্য:

$$
W_Q = W_K = W_V = I \Rightarrow Q = K = V = X
$$

এখানে $d_k = 2$ তাই $\sqrt{d_k}=\sqrt{2}\approx 1.414$.

---

## 1) Q, K, V বানানো

$$
Q = XW_Q = X,\quad K = XW_K = X,\quad V = XW_V = X
$$

অর্থাৎ:

$$
Q = K = V =
\begin{bmatrix}
1 & 0 \\
0 & 1 \\
1 & 1
\end{bmatrix}
$$

---

## 2) Score matrix (Dot product): ( $S = QK^\top$ )

প্রতিটি token অন্য token-এর সাথে dot-product:

- $x_1\cdot x_1 = 1$, $x_1\cdot x_2 = 0$, $x_1\cdot x_3 = 1$
- $x_2\cdot x_1 = 0$, $x_2\cdot x_2 = 1$, $x_2\cdot x_3 = 1$
- $x_3\cdot x_1 = 1$, $x_3\cdot x_2 = 1$, $x_3\cdot x_3 = 2$

তাই:

$$
S =
\begin{bmatrix}
1 & 0 & 1 \\
0 & 1 & 1 \\
1 & 1 & 2
\end{bmatrix}
$$

---

## 3) Scale করা: ( $S' = \dfrac{S}{\sqrt{d_k}}$ )

$$
\frac{1}{1.414} = 0.707,\quad \frac{2}{1.414} = 1.414
$$

$$
S' =
\begin{bmatrix}
0.707 & 0 & 0.707 \\
0 & 0.707 & 0.707 \\
0.707 & 0.707 & 1.414
\end{bmatrix}
$$

---

## 4) Softmax (row-wise) → Attention Weights (A)

### Row 1: $[0.707,\;0,\;0.707]$

- $e^{0.707}\approx 2.028$
- $e^{0}=1$

Sum $=2.028+1+2.028=5.056$

Weights:

- $2.028/5.056=0.401$
- $1/5.056=0.198$
- $2.028/5.056=0.401$

✅ Row1 = $[0.401,\;0.198,\;0.401]$

---

### Row 2: $[0,\;0.707,\;0.707]$

এখানেও একই সংখ্যা, শুধু অবস্থান বদলেছে:

✅ Row2 = $[0.198,\;0.401,\;0.401]$

---

### Row 3: $[0.707,\;0.707,\;1.414]$

- $e^{0.707}\approx 2.028$
- $e^{1.414}\approx 4.113$

Sum $=2.028+2.028+4.113=8.169$

Weights:

- $2.028/8.169=0.248$
- $2.028/8.169=0.248$
- $4.113/8.169=0.503$

✅ Row3 = $[0.248,\;0.248,\;0.503]$

---

### Final Attention Weight Matrix (A)

$$
A =
\begin{bmatrix}
0.401 & 0.198 & 0.401 \\
0.198 & 0.401 & 0.401 \\
0.248 & 0.248 & 0.503
\end{bmatrix}
$$

---

## 5) Output: ( $Z = A \cdot V$ )

যেহেতু $V = X$:

$$
V =
\begin{bmatrix}
1 & 0 \\
0 & 1 \\
1 & 1
\end{bmatrix}
$$

### Output for token 1: $z_1 = 0.401x_1 + 0.198x_2 + 0.401x_3$

- প্রথম dimension: $0.401\cdot 1 + 0.198\cdot 0 + 0.401\cdot 1 = 0.802$
- দ্বিতীয় dimension: $0.401\cdot 0 + 0.198\cdot 1 + 0.401\cdot 1 = 0.599$

✅ $z_1 \approx [0.802,\;0.599]$

---

### Output for token 2: $z_2 = 0.198x_1 + 0.401x_2 + 0.401x_3$

✅ $z_2 \approx [0.599,\;0.802]$

---

### Output for token 3: $z_3 = 0.248x_1 + 0.248x_2 + 0.503x_3$

- প্রথম dimension: $0.248 + 0 + 0.503 = 0.751$
- দ্বিতীয় dimension: $0 + 0.248 + 0.503 = 0.751$

✅ $z_3 \approx [0.751,\;0.751]$

---

## কী বোঝা গেল?

- **Attention weights** বলে দিচ্ছে প্রতিটি token বাক্যের অন্য token গুলোকে কতটা গুরুত্ব দিচ্ছে।
- **Output embedding** হলো অন্য token থেকে তথ্য “মিশিয়ে” পাওয়া নতুন contextual representation।

---
