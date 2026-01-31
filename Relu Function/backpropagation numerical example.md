---

## 1) Model (Single Neuron with ReLU)

[
z = wx + b
]
[
y = \text{ReLU}(z)=\max(0,z)
]

Loss (MSE):
[
E=\frac{1}{2}(t-y)^2
]

ReLU derivative:
[
\frac{dy}{dz}=
\begin{cases}
1,& z>0\
0,& z<0
\end{cases}
]
((z=0) এ সাধারণত 0 বা 1 ধরা হয়)

---

## 2) Given (Numbers)

* Input: (;x=2)
* Target: (;t=3)
* Initial: (;w=1,; b=-1)
* Learning rate: (\eta=0.1)

---

# ✅ Case A: (z>0) (Neuron learns)

## 3) Forward Pass

[
z = wx+b = (1)(2)+(-1)=1
]
[
y=\text{ReLU}(1)=1
]

Error:
[
E=\frac{1}{2}(3-1)^2=\frac{1}{2}\cdot 4=2
]

---

## 4) Backpropagation

[
\frac{dE}{dy}=(y-t)=1-3=-2
]

Since (z=1>0),
[
\frac{dy}{dz}=1
]

Chain rule:
[
\frac{dE}{dw}=\frac{dE}{dy}\cdot\frac{dy}{dz}\cdot\frac{dz}{dw}
]
[
\frac{dz}{dw}=x=2
]
[
\Rightarrow \frac{dE}{dw}=(-2)(1)(2)=-4
]

Bias gradient:
[
\frac{dE}{db}=\frac{dE}{dy}\cdot\frac{dy}{dz}\cdot\frac{dz}{db}
]
[
\frac{dz}{db}=1
\Rightarrow \frac{dE}{db}=(-2)(1)(1)=-2
]

---

## 5) Weight Update (Gradient Descent)

[
w_{\text{new}}=w-\eta\frac{dE}{dw}
]
[
b_{\text{new}}=b-\eta\frac{dE}{db}
]

So:
[
w_{\text{new}}=1-0.1(-4)=1.4
]
[
b_{\text{new}}=-1-0.1(-2)=-0.8
]

---

## 6) Quick Check (Error কমলো?)

New forward:
[
z_{\text{new}}=(1.4)(2)+(-0.8)=2.8-0.8=2.0
]
[
y_{\text{new}}=\text{ReLU}(2)=2
]

New error:
[
E_{\text{new}}=\frac{1}{2}(3-2)^2=0.5
]

✅ Error: **2 → 0.5 কমেছে**, মানে neuron শিখেছে।

---

# ❌ Case B: (z<0) (Dead ReLU: learning stops)

ধরি অন্য initial:
[
w=0.2,; b=-1,; x=2
]
[
z=(0.2)(2)-1= -0.6
\Rightarrow y=\text{ReLU}(-0.6)=0
]

এখানে (z<0) তাই:
[
\frac{dy}{dz}=0
\Rightarrow \frac{dE}{dw}=0,; \frac{dE}{db}=0
]

✅ Output ভুল হলেও weights **update হবে না**
👉 এটাকেই বলে **Dead ReLU problem**

---

## ⭐ Exam-Ready Summary Formula (ReLU)

যদি (z>0):
[
\delta = (y-t)\cdot 1 = (y-t)
]
[
\frac{dE}{dw}=\delta x,\quad \frac{dE}{db}=\delta
]

যদি (z<0):
[
\delta = 0 \Rightarrow \text{no update}
]

---

