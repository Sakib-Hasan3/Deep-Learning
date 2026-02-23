---

# 🔹 ANN with One Hidden Layer (Mathematical Example)

আমরা নেবো:

* **2 Input neurons**
* **1 Hidden layer (2 neurons)**
* **1 Output neuron**
* **Sigmoid activation**

---

## 1️⃣ Network Structure

```
x1 ----> (h1) ----\
        (h2) -----> (output y)
x2 ---->
```

---

## 2️⃣ Given Values (ধরা হলো)

### Inputs

[
x_1 = 1,\quad x_2 = 0
]

### Target

[
t = 1
]

### Initial Weights

**Input → Hidden**
[
w_{11}=0.1,; w_{12}=0.2
]
[
w_{21}=0.3,; w_{22}=0.4
]

**Hidden → Output**
[
v_1 = 0.5,; v_2 = 0.6
]

Bias:
[
b_h = 0.1,\quad b_o = 0.2
]

Learning rate:
[
\eta = 0.5
]

---

## 3️⃣ Forward Propagation

### 🔸 Hidden Layer Calculation

#### Neuron h1

[
z_{h1} = (1)(0.1) + (0)(0.3) + 0.1 = 0.2
]

[
h_1 = \sigma(0.2) = \frac{1}{1+e^{-0.2}} \approx 0.55
]

#### Neuron h2

[
z_{h2} = (1)(0.2) + (0)(0.4) + 0.1 = 0.3
]

[
h_2 = \sigma(0.3) \approx 0.57
]

---

### 🔸 Output Layer

[
z_o = (0.55)(0.5) + (0.57)(0.6) + 0.2
]

[
z_o = 0.275 + 0.342 + 0.2 = 0.817
]

[
y = \sigma(0.817) \approx 0.69
]

---

## 4️⃣ Error Calculation

[
E = \frac{1}{2}(t-y)^2
]

[
E = \frac{1}{2}(1-0.69)^2 = 0.048
]

---

## 5️⃣ Backpropagation (Output Layer)

### Output Gradient

[
\delta_o = (y-t),y(1-y)
]

[
\delta_o = (0.69-1)(0.69)(0.31)
]

[
\delta_o = -0.066
]

---

## 6️⃣ Update Hidden → Output Weights

[
v_{new} = v_{old} - \eta \delta_o h
]

### Update (v_1)

[
v_1 = 0.5 - 0.5(-0.066)(0.55)
]
[
v_1 = 0.518
]

### Update (v_2)

[
v_2 = 0.6 - 0.5(-0.066)(0.57)
]
[
v_2 = 0.619
]

---

## 7️⃣ Backpropagation (Hidden Layer)

### Hidden Error Term

[
\delta_h = \delta_o \cdot v \cdot h(1-h)
]

#### For h1

[
\delta_{h1} = (-0.066)(0.5)(0.55)(0.45)
]
[
\delta_{h1} = -0.0082
]

#### For h2

[
\delta_{h2} = (-0.066)(0.6)(0.57)(0.43)
]
[
\delta_{h2} = -0.0097
]

---

## 8️⃣ Update Input → Hidden Weights

### Update (w_{11})

[
w_{11} = 0.1 - 0.5(-0.0082)(1)
]
[
w_{11} = 0.1041
]

### Update (w_{12})

[
w_{12} = 0.2 - 0.5(-0.0097)(1)
]
[
w_{12} = 0.2049
]

((x_2=0), তাই (w_{21}, w_{22}) unchanged)

---

## 9️⃣ Final Updated Weights (After 1 Iteration)

* **Input → Hidden**
  [
  w_{11}=0.104,; w_{12}=0.205
  ]

* **Hidden → Output**
  [
  v_1=0.518,; v_2=0.619
  ]

👉 Error কমেছে
👉 ANN শিখেছে
👉 **Hidden layer-ই non-linear learning সম্ভব করেছে**

---

## 🔑 Exam-Ready One Line

> **In ANN with hidden layers, backpropagation distributes output error backward using chain rule, enabling learning of complex non-linear patterns.**

---


