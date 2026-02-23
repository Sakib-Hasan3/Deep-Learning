<<<<<<< HEAD
---

## 1) Problem (একটা কাজ শিখবে)

ধরি ANN শিখবে এই rule:

> **OR gate**
> (যেকোনো একটা 1 হলেই output 1)

Training data:

| x1 | x2 | Target (t) |
| -- | -- | ---------- |
| 0  | 0  | 0          |
| 0  | 1  | 1          |
| 1  | 0  | 1          |
| 1  | 1  | 1          |

---

## 2) Model (Neuron equation)

Neuron output:

[
y = \begin{cases}
1, & \text{if } (w_1x_1 + w_2x_2 + b)\ge 0\
0, & \text{otherwise}
\end{cases}
]

Learning rule (Perceptron update):

[
w_i \leftarrow w_i + \eta (t-y)x_i
]
[
b \leftarrow b + \eta (t-y)
]

ধরি learning rate (\eta = 1)

---

## 3) Initialize (শুরুতে ধরলাম)

[
w_1=0,; w_2=0,; b=0
]

---

## 4) Training step-by-step (একটা epoch দেখাই)

### ✅ Sample 1: (x1=0, x2=0, t=0)

Net:
[
0\cdot0 + 0\cdot0 + 0 = 0
\Rightarrow y=1 ; (\text{কারণ } \ge 0)
]
Error term:
[
(t-y)=0-1=-1
]
Update:
[
w_1 = 0 + (-1)\cdot0 = 0
]
[
w_2 = 0 + (-1)\cdot0 = 0
]
[
b = 0 + (-1) = -1
]

---

### ✅ Sample 2: (0,1, t=1)

Net:
[
0\cdot0 + 0\cdot1 - 1 = -1 \Rightarrow y=0
]
Error:
[
(t-y)=1-0=1
]
Update:
[
w_1 = 0 + 1\cdot0 = 0
]
[
w_2 = 0 + 1\cdot1 = 1
]
[
b = -1 + 1 = 0
]

---

### ✅ Sample 3: (1,0, t=1)

Net:
[
0\cdot1 + 1\cdot0 + 0 = 0 \Rightarrow y=1
]
Error:
[
(t-y)=1-1=0
]
Update: কিছুই বদলাবে না

---

### ✅ Sample 4: (1,1, t=1)

Net:
[
0\cdot1 + 1\cdot1 + 0 = 1 \Rightarrow y=1
]
Error:
[
(t-y)=0
]
Update: কিছুই বদলাবে না

---

## 5) Final learned parameters (এখানে শেখা শেষের মতো)

[
w_1=0,; w_2=1,; b=0
]

---

## 6) ANN Intuition (এখানে “intuition” কী?)

এখন ANN-এর **intuition** হলো এই learned rule:

[
\text{If } x_2=1,; \text{output হবে 1}
]

মানে ANN **ডেটা দেখে বুঝে নিয়েছে** কোন ইনপুটটা বেশি গুরুত্বপূর্ণ (এখানে (x_2))—এটাই তার learned intuition/pattern understanding।

---

### ✅ Quick test

* (0,0): net = 0 ⇒ y=1 (এটা ভুল হতে পারে threshold rule এর কারণে)
  👉 বাস্তবে আমরা bias/threshold একটু টিউন করি বা activation rule পরিবর্তন করি (>(0) ব্যবহার করি) যাতে (0,0) ঠিকভাবে 0 হয়।

উদাহরণ হিসেবে যদি rule নিই:

[
y=1 \text{ if net} > 0
]
তাহলে (0,0) net=0 ⇒ y=0 (ঠিক)

---

=======
---

## 1) Problem (একটা কাজ শিখবে)

ধরি ANN শিখবে এই rule:

> **OR gate**
> (যেকোনো একটা 1 হলেই output 1)

Training data:

| x1 | x2 | Target (t) |
| -- | -- | ---------- |
| 0  | 0  | 0          |
| 0  | 1  | 1          |
| 1  | 0  | 1          |
| 1  | 1  | 1          |

---

## 2) Model (Neuron equation)

Neuron output:

[
y = \begin{cases}
1, & \text{if } (w_1x_1 + w_2x_2 + b)\ge 0\
0, & \text{otherwise}
\end{cases}
]

Learning rule (Perceptron update):

[
w_i \leftarrow w_i + \eta (t-y)x_i
]
[
b \leftarrow b + \eta (t-y)
]

ধরি learning rate (\eta = 1)

---

## 3) Initialize (শুরুতে ধরলাম)

[
w_1=0,; w_2=0,; b=0
]

---

## 4) Training step-by-step (একটা epoch দেখাই)

### ✅ Sample 1: (x1=0, x2=0, t=0)

Net:
[
0\cdot0 + 0\cdot0 + 0 = 0
\Rightarrow y=1 ; (\text{কারণ } \ge 0)
]
Error term:
[
(t-y)=0-1=-1
]
Update:
[
w_1 = 0 + (-1)\cdot0 = 0
]
[
w_2 = 0 + (-1)\cdot0 = 0
]
[
b = 0 + (-1) = -1
]

---

### ✅ Sample 2: (0,1, t=1)

Net:
[
0\cdot0 + 0\cdot1 - 1 = -1 \Rightarrow y=0
]
Error:
[
(t-y)=1-0=1
]
Update:
[
w_1 = 0 + 1\cdot0 = 0
]
[
w_2 = 0 + 1\cdot1 = 1
]
[
b = -1 + 1 = 0
]

---

### ✅ Sample 3: (1,0, t=1)

Net:
[
0\cdot1 + 1\cdot0 + 0 = 0 \Rightarrow y=1
]
Error:
[
(t-y)=1-1=0
]
Update: কিছুই বদলাবে না

---

### ✅ Sample 4: (1,1, t=1)

Net:
[
0\cdot1 + 1\cdot1 + 0 = 1 \Rightarrow y=1
]
Error:
[
(t-y)=0
]
Update: কিছুই বদলাবে না

---

## 5) Final learned parameters (এখানে শেখা শেষের মতো)

[
w_1=0,; w_2=1,; b=0
]

---

## 6) ANN Intuition (এখানে “intuition” কী?)

এখন ANN-এর **intuition** হলো এই learned rule:

[
\text{If } x_2=1,; \text{output হবে 1}
]

মানে ANN **ডেটা দেখে বুঝে নিয়েছে** কোন ইনপুটটা বেশি গুরুত্বপূর্ণ (এখানে (x_2))—এটাই তার learned intuition/pattern understanding।

---

### ✅ Quick test

* (0,0): net = 0 ⇒ y=1 (এটা ভুল হতে পারে threshold rule এর কারণে)
  👉 বাস্তবে আমরা bias/threshold একটু টিউন করি বা activation rule পরিবর্তন করি (>(0) ব্যবহার করি) যাতে (0,0) ঠিকভাবে 0 হয়।

উদাহরণ হিসেবে যদি rule নিই:

[
y=1 \text{ if net} > 0
]
তাহলে (0,0) net=0 ⇒ y=0 (ঠিক)

---

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
