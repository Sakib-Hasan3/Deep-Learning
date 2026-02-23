<<<<<<< HEAD
## **Regression Cost Function — বাংলায় ব্যাখ্যা (Intuition + Math + Graph)**

![Image](https://global.discourse-cdn.com/dlai/original/3X/4/3/433e18a3eb780e1e01210d38066f4763855252c1.png)

![Image](https://miro.medium.com/0%2AfcNdB994NRWt_XZ2.gif)

![Image](https://editor.analyticsvidhya.com/uploads/46591Capture5.PNG)

![Image](https://editor.analyticsvidhya.com/uploads/661483.png)

---

## 🔹 ১) Regression Cost Function কী?

**Regression**–এ model continuous value predict করে (যেমন: price, height, temperature)।
**Regression Cost Function** মাপে—

> 👉 model-এর prediction আসল মান থেকে **গড়ে কতটা দূরে**।

Training-এর লক্ষ্য:

> **Cost function minimize করা**

---

## 🔹 ২) সবচেয়ে ব্যবহৃত Regression Cost Function: **Mean Squared Error (MSE)**

### Mathematical Formula

ধরি,

* (y_i) = actual value
* (\hat{y}_i) = predicted value
* (N) = মোট data point

[
J(\theta)=\frac{1}{2N}\sum_{i=1}^{N}(y_i-\hat{y}_i)^2
]

👉 (\frac{1}{2}) নেওয়া হয় derivative সহজ করার জন্য।

---

## 🔹 ৩) Intuition (সহজ ভাষায়)

* Prediction যদি একটু ভুল → cost ছোট
* Prediction যদি অনেক ভুল → cost অনেক বড় (কারণ **square**)

👉 বড় ভুলকে বেশি শাস্তি দেয়
👉 তাই regression-এর জন্য খুব কার্যকর

---

## 🔹 ৪) Single Data Point vs Dataset

### Loss (একটা sample):

[
\ell_i=\frac{1}{2}(y_i-\hat{y}_i)^2
]

### Cost (সব sample):

[
J=\frac{1}{N}\sum \ell_i
]

---

## 🔹 ৫) Numerical Example

ধরি 3টা data point:

| Actual (y) | Predicted (\hat{y}) |
| ---------- | ------------------- |
| 3          | 2                   |
| 5          | 4                   |
| 7          | 6                   |

Error:
[
(3-2)^2=1,\quad (5-4)^2=1,\quad (7-6)^2=1
]

Cost:
[
J=\frac{1}{2\times 3}(1+1+1)=\frac{3}{6}=0.5
]

---

## 🔹 ৬) Cost Function Graph দিয়ে বোঝা

* X-axis → model parameters (weight, bias)
* Y-axis → cost

👉 Graph সাধারণত **bowl / U-shape**
👉 Minimum point = **best parameters**

এটাই Gradient Descent খুঁজে বের করে।

---

## 🔹 ৭) কেন Square Error ব্যবহার করা হয়?

✔ Smooth & differentiable
✔ Gradient descent সহজ
✔ Large error-কে বেশি গুরুত্ব দেয়

---

## 🔹 ৮) Regression-এর অন্য Cost Functions (সংক্ষেপে)

| Cost Function                 | ব্যবহার                 |
| ----------------------------- | ----------------------- |
| **MSE**                       | Standard regression     |
| **MAE** (Mean Absolute Error) | Outlier কম গুরুত্ব দিতে |
| **Huber Loss**                | MSE + MAE এর balance    |

---

## 🧠 মনে রাখার কৌশল

> **Regression = difference → square → average**

---

## ✍️ Exam-Ready এক লাইন

> **Regression cost function, commonly Mean Squared Error, measures the average squared difference between actual and predicted values and is minimized to train regression models.**

=======
## **Regression Cost Function — বাংলায় ব্যাখ্যা (Intuition + Math + Graph)**

![Image](https://global.discourse-cdn.com/dlai/original/3X/4/3/433e18a3eb780e1e01210d38066f4763855252c1.png)

![Image](https://miro.medium.com/0%2AfcNdB994NRWt_XZ2.gif)

![Image](https://editor.analyticsvidhya.com/uploads/46591Capture5.PNG)

![Image](https://editor.analyticsvidhya.com/uploads/661483.png)

---

## 🔹 ১) Regression Cost Function কী?

**Regression**–এ model continuous value predict করে (যেমন: price, height, temperature)।
**Regression Cost Function** মাপে—

> 👉 model-এর prediction আসল মান থেকে **গড়ে কতটা দূরে**।

Training-এর লক্ষ্য:

> **Cost function minimize করা**

---

## 🔹 ২) সবচেয়ে ব্যবহৃত Regression Cost Function: **Mean Squared Error (MSE)**

### Mathematical Formula

ধরি,

* (y_i) = actual value
* (\hat{y}_i) = predicted value
* (N) = মোট data point

[
J(\theta)=\frac{1}{2N}\sum_{i=1}^{N}(y_i-\hat{y}_i)^2
]

👉 (\frac{1}{2}) নেওয়া হয় derivative সহজ করার জন্য।

---

## 🔹 ৩) Intuition (সহজ ভাষায়)

* Prediction যদি একটু ভুল → cost ছোট
* Prediction যদি অনেক ভুল → cost অনেক বড় (কারণ **square**)

👉 বড় ভুলকে বেশি শাস্তি দেয়
👉 তাই regression-এর জন্য খুব কার্যকর

---

## 🔹 ৪) Single Data Point vs Dataset

### Loss (একটা sample):

[
\ell_i=\frac{1}{2}(y_i-\hat{y}_i)^2
]

### Cost (সব sample):

[
J=\frac{1}{N}\sum \ell_i
]

---

## 🔹 ৫) Numerical Example

ধরি 3টা data point:

| Actual (y) | Predicted (\hat{y}) |
| ---------- | ------------------- |
| 3          | 2                   |
| 5          | 4                   |
| 7          | 6                   |

Error:
[
(3-2)^2=1,\quad (5-4)^2=1,\quad (7-6)^2=1
]

Cost:
[
J=\frac{1}{2\times 3}(1+1+1)=\frac{3}{6}=0.5
]

---

## 🔹 ৬) Cost Function Graph দিয়ে বোঝা

* X-axis → model parameters (weight, bias)
* Y-axis → cost

👉 Graph সাধারণত **bowl / U-shape**
👉 Minimum point = **best parameters**

এটাই Gradient Descent খুঁজে বের করে।

---

## 🔹 ৭) কেন Square Error ব্যবহার করা হয়?

✔ Smooth & differentiable
✔ Gradient descent সহজ
✔ Large error-কে বেশি গুরুত্ব দেয়

---

## 🔹 ৮) Regression-এর অন্য Cost Functions (সংক্ষেপে)

| Cost Function                 | ব্যবহার                 |
| ----------------------------- | ----------------------- |
| **MSE**                       | Standard regression     |
| **MAE** (Mean Absolute Error) | Outlier কম গুরুত্ব দিতে |
| **Huber Loss**                | MSE + MAE এর balance    |

---

## 🧠 মনে রাখার কৌশল

> **Regression = difference → square → average**

---

## ✍️ Exam-Ready এক লাইন

> **Regression cost function, commonly Mean Squared Error, measures the average squared difference between actual and predicted values and is minimized to train regression models.**

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
