<<<<<<< HEAD
### **Backpropagation and Weight Updation (with Mathematical Example)**

এটা ANN শেখার **সবচেয়ে গুরুত্বপূর্ণ অংশ**। সহজ ভাষায় বললে—

> **Backpropagation = ভুল বের করা + সেই ভুল অনুযায়ী weight ঠিক করা**

---

## 1️⃣ Basic Idea (সহজ করে)

* ANN একটি output দেয়
* output যদি ভুল হয় → **error** বের করি
* error ব্যবহার করে **weight update** করি
* বারবার করলে error কমে → ANN শেখে

---

## 2️⃣ Simple ANN Model (Single Neuron)

ধরি একটি neuron আছে:

[
y = f(z)
]
যেখানে,
[
z = w_1x_1 + w_2x_2 + b
]

Activation function (Sigmoid):

[
f(z) = \frac{1}{1+e^{-z}}
]

---

## 3️⃣ Given Example Data

ধরি:

* Input:
  [
  x_1=1,; x_2=0
  ]
* Target output:
  [
  t=1
  ]

Initial values:
[
w_1=0.4,; w_2=0.6,; b=0.1
]
Learning rate:
[
\eta = 0.5
]

---

## 4️⃣ Forward Propagation (Output বের করা)

### Step 1: Net input

[
z = (1)(0.4) + (0)(0.6) + 0.1 = 0.5
]

### Step 2: Output

[
y = \frac{1}{1+e^{-0.5}} \approx 0.62
]

---

## 5️⃣ Error Calculation

Mean Squared Error (MSE):

[
E = \frac{1}{2}(t-y)^2
]

[
E = \frac{1}{2}(1-0.62)^2 = 0.072
]

---

## 6️⃣ Backpropagation (Gradient বের করা)

আমরা বের করব:

[
\frac{\partial E}{\partial w}
]

### Step 1: Error derivative

[
\frac{\partial E}{\partial y} = (y-t)
]

[
= (0.62-1) = -0.38
]

---

### Step 2: Sigmoid derivative

[
\frac{dy}{dz} = y(1-y)
]

[
= 0.62(1-0.62) = 0.2356
]

---

### Step 3: Chain Rule (Backpropagation)

[
\frac{\partial E}{\partial w_1}
= (y-t)\cdot y(1-y)\cdot x_1
]

[
= (-0.38)(0.2356)(1)
= -0.0895
]

---

## 7️⃣ Weight Updation Formula

[
w_{new} = w_{old} - \eta \frac{\partial E}{\partial w}
]

---

### Update (w_1)

[
w_1 = 0.4 - 0.5(-0.0895)
]

[
w_1 = 0.4447
]

---

### Update (w_2)

[
\frac{\partial E}{\partial w_2}
= (y-t)y(1-y)x_2
= (-0.38)(0.2356)(0) = 0
]

[
w_2 = 0.6
]

---

### Update Bias

[
\frac{\partial E}{\partial b}
= (y-t)y(1-y)
= -0.0895
]

[
b = 0.1 - 0.5(-0.0895) = 0.1447
]

---

## 8️⃣ Updated Parameters (After Learning)

[
w_1=0.4447,; w_2=0.6,; b=0.1447
]

👉 Output এখন target-এর আরও কাছাকাছি হবে
👉 **Error কমেছে**
👉 ANN শিখেছে

---

## 🔁 Backpropagation মানে কী?

* Output থেকে error পেছনের দিকে পাঠানো
* Chain rule দিয়ে প্রতিটি weight-এর contribution বের করা
* Gradient descent দিয়ে weight ঠিক করা

---

## 🔑 One-Line Summary (Exam Ready)

> **Backpropagation computes the gradient of error using chain rule, and weight updation minimizes error using gradient descent.**

---

=======
### **Backpropagation and Weight Updation (with Mathematical Example)**

এটা ANN শেখার **সবচেয়ে গুরুত্বপূর্ণ অংশ**। সহজ ভাষায় বললে—

> **Backpropagation = ভুল বের করা + সেই ভুল অনুযায়ী weight ঠিক করা**

---

## 1️⃣ Basic Idea (সহজ করে)

* ANN একটি output দেয়
* output যদি ভুল হয় → **error** বের করি
* error ব্যবহার করে **weight update** করি
* বারবার করলে error কমে → ANN শেখে

---

## 2️⃣ Simple ANN Model (Single Neuron)

ধরি একটি neuron আছে:

[
y = f(z)
]
যেখানে,
[
z = w_1x_1 + w_2x_2 + b
]

Activation function (Sigmoid):

[
f(z) = \frac{1}{1+e^{-z}}
]

---

## 3️⃣ Given Example Data

ধরি:

* Input:
  [
  x_1=1,; x_2=0
  ]
* Target output:
  [
  t=1
  ]

Initial values:
[
w_1=0.4,; w_2=0.6,; b=0.1
]
Learning rate:
[
\eta = 0.5
]

---

## 4️⃣ Forward Propagation (Output বের করা)

### Step 1: Net input

[
z = (1)(0.4) + (0)(0.6) + 0.1 = 0.5
]

### Step 2: Output

[
y = \frac{1}{1+e^{-0.5}} \approx 0.62
]

---

## 5️⃣ Error Calculation

Mean Squared Error (MSE):

[
E = \frac{1}{2}(t-y)^2
]

[
E = \frac{1}{2}(1-0.62)^2 = 0.072
]

---

## 6️⃣ Backpropagation (Gradient বের করা)

আমরা বের করব:

[
\frac{\partial E}{\partial w}
]

### Step 1: Error derivative

[
\frac{\partial E}{\partial y} = (y-t)
]

[
= (0.62-1) = -0.38
]

---

### Step 2: Sigmoid derivative

[
\frac{dy}{dz} = y(1-y)
]

[
= 0.62(1-0.62) = 0.2356
]

---

### Step 3: Chain Rule (Backpropagation)

[
\frac{\partial E}{\partial w_1}
= (y-t)\cdot y(1-y)\cdot x_1
]

[
= (-0.38)(0.2356)(1)
= -0.0895
]

---

## 7️⃣ Weight Updation Formula

[
w_{new} = w_{old} - \eta \frac{\partial E}{\partial w}
]

---

### Update (w_1)

[
w_1 = 0.4 - 0.5(-0.0895)
]

[
w_1 = 0.4447
]

---

### Update (w_2)

[
\frac{\partial E}{\partial w_2}
= (y-t)y(1-y)x_2
= (-0.38)(0.2356)(0) = 0
]

[
w_2 = 0.6
]

---

### Update Bias

[
\frac{\partial E}{\partial b}
= (y-t)y(1-y)
= -0.0895
]

[
b = 0.1 - 0.5(-0.0895) = 0.1447
]

---

## 8️⃣ Updated Parameters (After Learning)

[
w_1=0.4447,; w_2=0.6,; b=0.1447
]

👉 Output এখন target-এর আরও কাছাকাছি হবে
👉 **Error কমেছে**
👉 ANN শিখেছে

---

## 🔁 Backpropagation মানে কী?

* Output থেকে error পেছনের দিকে পাঠানো
* Chain rule দিয়ে প্রতিটি weight-এর contribution বের করা
* Gradient descent দিয়ে weight ঠিক করা

---

## 🔑 One-Line Summary (Exam Ready)

> **Backpropagation computes the gradient of error using chain rule, and weight updation minimizes error using gradient descent.**

---

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
