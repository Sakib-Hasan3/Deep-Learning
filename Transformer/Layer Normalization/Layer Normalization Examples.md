# Layer Normalization — Worked Examples

Layer Normalization (LayerNorm) একটি vector-এর **feature dimension** বরাবর normalize করে। নিচে ধাপে ধাপে কয়েকটি ছোট উদাহরণ দেওয়া হলো।

---

## 1) Example–1 (১টি vector)

ধরি ইনপুট:

[
x = [2,;4,;6]
]

### Step–1: Mean

[
\mu = \frac{2+4+6}{3} = 4
]

### Step–2: Variance

[
\sigma^2 = \frac{(2-4)^2+(4-4)^2+(6-4)^2}{3}
]

[
= \frac{4+0+4}{3} = 2.67
]

### Step–3: Standard Deviation

[
\sigma = \sqrt{2.67} \approx 1.63
]

---

### Step–4: Normalize

[
\hat{x}_i = \frac{x_i-\mu}{\sigma}
]

For each element:

* ((2-4)/1.63 ≈ -1.23)
* ((4-4)/1.63 = 0)
* ((6-4)/1.63 ≈ 1.23)

Normalized vector:

[
[-1.23,;0,;1.23]
]

---

### Step–5: Scale & Shift

LayerNorm final output:

[
y_i = \gamma \hat{x_i} + \beta
]

ধরি:

[
\gamma = 1,\quad \beta = 0
]

তাহলে output একই থাকবে:

[
[-1.23,;0,;1.23]
]

---

# 2) Example–2 (Transformer token vector)

ধরি একটি token embedding:

[
x = [1,;2,;3,;4]
]

### Step–1: Mean

[
\mu = (1+2+3+4)/4 = 2.5
]

---

### Step–2: Variance

[
\sigma^2 = \frac{(1-2.5)^2+(2-2.5)^2+(3-2.5)^2+(4-2.5)^2}{4}
]

[
= \frac{2.25+0.25+0.25+2.25}{4}
]

[
= 1.25
]

---

### Step–3: Standard deviation

[
\sigma = \sqrt{1.25} ≈ 1.118
]

---

### Step–4: Normalize

[
(1-2.5)/1.118 ≈ -1.34
]

[
(2-2.5)/1.118 ≈ -0.45
]

[
(3-2.5)/1.118 ≈ 0.45
]

[
(4-2.5)/1.118 ≈ 1.34
]

Normalized vector:

[
[-1.34,;-0.45,;0.45,;1.34]
]

---

```markdown
# Layer Normalization — Worked Examples

Layer Normalization (LayerNorm) একটি vector-এর **feature dimension** বরাবর normalize করে। নিচে ধাপে ধাপে কয়েকটি ছোট উদাহরণ দেওয়া হলো।

---

## 1) Example–1 (১টি vector)

ধরি ইনপুট:

$$
x = [2,\;4,\;6]
$$

### Step–1: Mean

$$
\mu = \frac{2+4+6}{3} = 4
$$

### Step–2: Variance

$$
\sigma^2 = \frac{(2-4)^2+(4-4)^2+(6-4)^2}{3}
$$

$$
= \frac{4+0+4}{3} = 2.67
$$

### Step–3: Standard Deviation

$$
\sigma = \sqrt{2.67} \approx 1.63
$$

---

### Step–4: Normalize

$$
\hat{x}_i = \frac{x_i-\mu}{\sigma}
$$

For each element:

- ((2-4)/1.63 ≈ -1.23)
- ((4-4)/1.63 = 0)
- ((6-4)/1.63 ≈ 1.23)

Normalized vector:

$$
[-1.23,\;0,\;1.23]
$$

---

### Step–5: Scale & Shift

LayerNorm final output:

$$
y_i = \gamma \hat{x_i} + \beta
$$

ধরি:

$$
\gamma = 1,\quad \beta = 0
$$

তাহলে output একই থাকবে:

$$
[-1.23,\;0,\;1.23]
$$

---

# 2) Example–2 (Transformer token vector)

ধরি একটি token embedding:

$$
x = [1,\;2,\;3,\;4]
$$

### Step–1: Mean

$$
\mu = (1+2+3+4)/4 = 2.5
$$

---

### Step–2: Variance

$$
\sigma^2 = \frac{(1-2.5)^2+(2-2.5)^2+(3-2.5)^2+(4-2.5)^2}{4}
$$

$$
= \frac{2.25+0.25+0.25+2.25}{4}
$$

$$
= 1.25
$$

---

### Step–3: Standard deviation

$$
\sigma = \sqrt{1.25} \approx 1.118
$$

---

### Step–4: Normalize

$$
(1-2.5)/1.118 \approx -1.34
$$

$$
(2-2.5)/1.118 \approx -0.45
$$

$$
(3-2.5)/1.118 \approx 0.45
$$

$$
(4-2.5)/1.118 \approx 1.34
$$

Normalized vector:

$$
[-1.34,\;-0.45,\;0.45,\;1.34]
$$

---

# 3) Example–3 (Multiple Tokens)

ধরি Transformer input:

$$
X =
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6
\end{bmatrix}
$$

LayerNorm **row-wise** apply হয়।

---

### Row–1

$$
[1,2,3]
$$

Mean:

$$
\mu = 2
$$

Variance:

$$
\sigma^2 = \frac{(1-2)^2+(2-2)^2+(3-2)^2}{3} = 0.67
$$

Std:

$$
\sigma \approx 0.816
$$

Normalized:

$$
[-1.22,\;0,\;1.22]
$$

---

### Row–2

$$
[4,5,6]
$$

Mean:

$$
\mu = 5
$$

Variance:

$$
\sigma^2 = 0.67
$$

Normalized:

$$
[-1.22,\;0,\;1.22]
$$

---

# 4) Transformer Context Example

ধরি একটি token embedding:

$$
[0.8,\;1.2,\;0.5,\;2.1]
$$

LayerNorm:

1️⃣ Mean compute
2️⃣ Variance compute
3️⃣ Normalize
4️⃣ Scale & shift

এর ফলে activation values stable থাকে।

---

# 5) Intuition

LayerNorm basically বলে:

> “এই vector-এর values standard scale-এ আনো যাতে network training stable হয়।”

---

# Summary

LayerNorm steps:

1. Mean calculate
2. Variance calculate
3. Normalize
4. Scale & shift

Formula:

$$
y = \gamma \frac{x-\mu}{\sqrt{\sigma^2+\epsilon}} + \beta
$$

---
 
```

