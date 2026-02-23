---

## 🎯 Problem Setup (Very Small)

ধরি আমরা এই loss function minimize করতে চাই:


$$
J(w) = \frac{1}{2}(w-2)^2
$$

Gradient:

$$
\frac{dJ}{dw} = w-2
$$

---

### Initial values


* Initial weight: $w_0 = 0$
* Learning rate: $\eta = 0.1$
* Decay rate: $\rho = 0.9$
* $\epsilon = 10^{-8}$
* Initial squared-gradient accumulator:
  $$
  s_0 = 0
  $$

---

## 🔁 RMSProp Formula (Reminder)


$$
s_t = \rho s_{t-1} + (1-\rho) g_t^2
$$


$$
w \leftarrow w - \frac{\eta}{\sqrt{s_t}+\epsilon} \cdot g_t
$$

---

## 🧮 Iteration 1

**Gradient**

$$
g_0 = w_0 - 2 = 0 - 2 = -2
$$

**Squared gradient average**

$$
s_1 = 0.9(0) + 0.1( (-2)^2 ) = 0.4
$$

**Weight update**

$$
w_1 = 0 - \frac{0.1}{\sqrt{0.4}}(-2)
$$


$$
\sqrt{0.4} \approx 0.632
$$


$$
w_1 \approx 0 + 0.316 = 0.316
$$

---

## 🧮 Iteration 2

**Gradient**

$$
g_1 = 0.316 - 2 = -1.684
$$

**Squared gradient average**

$$
s_2 = 0.9(0.4) + 0.1(1.684^2)
$$


$$
s_2 = 0.36 + 0.283 \approx 0.643
$$

**Weight update**

$$
w_2 = 0.316 - \frac{0.1}{\sqrt{0.643}}(-1.684)
$$


$$
\sqrt{0.643} \approx 0.802
$$


$$
w_2 \approx 0.316 + 0.21 = 0.526
$$

---

## 🔍 Observation (Important)

| Step  | Weight |
| ----- | ------ |
| (w_0) | 0      |
| (w_1) | 0.316  |
| (w_2) | 0.526  |

* Gradient কমছে
* (s_t) smoothভাবে বাড়ছে
* Learning rate **self-adjust** হচ্ছে
* Update stable (overshoot নেই)

---

## 🧠 Intuition (One Line)

> RMSProp recent gradients দেখে step size ঠিক করে, তাই learning smooth ও stable হয়।

---

## ✍️ Exam-Ready Mini Summary

**RMSProp scales the learning rate by the root mean square of recent gradients, preventing aggressive decay and stabilizing training.**

---
