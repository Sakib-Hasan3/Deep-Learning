<<<<<<< HEAD
---

## 1) Model (Single Neuron with tanh)

[
z = wx + b
]
[
y = \tanh(z)
]

Loss (MSE):

[
E=\frac{1}{2}(t-y)^2
]

Derivative of tanh:

[
\frac{dy}{dz}=1-\tanh^2(z)=1-y^2
]

---

## 2) Given (Numbers)

* Input: (;x = 1.5)
* Target: (;t = 0.8)  (tanh-এর range -1 to +1, তাই target এই range-এ)
* Initial parameters:
  [
  w=0.4,\quad b=-0.2
  ]
* Learning rate: (\eta = 0.1)

---

## 3) Forward Pass

### Step A: Net input

[
z = wx+b = (0.4)(1.5) + (-0.2)=0.6-0.2=0.4
]

### Step B: Output (tanh)

[
y=\tanh(0.4)\approx 0.3799 ;(\approx 0.38)
]

### Step C: Error

[
E=\frac{1}{2}(t-y)^2=\frac{1}{2}(0.8-0.3799)^2
]
[
=\frac{1}{2}(0.4201)^2\approx \frac{1}{2}(0.1765)\approx 0.0882
]

---

## 4) Backpropagation (Gradients)

### Step A: (\frac{dE}{dy})

[
\frac{dE}{dy}= (y-t)=0.3799-0.8=-0.4201
]

### Step B: (\frac{dy}{dz}) for tanh

[
\frac{dy}{dz}=1-y^2 = 1-(0.3799)^2
]
[
=1-0.1443=0.8557
]

### Step C: Chain rule for (w)

[
\frac{dE}{dw}=\frac{dE}{dy}\cdot\frac{dy}{dz}\cdot\frac{dz}{dw}
]
[
\frac{dz}{dw}=x=1.5
]

So,
[
\frac{dE}{dw}=(-0.4201)(0.8557)(1.5)\approx -0.5387
]

### For bias (b)

[
\frac{dE}{db}=\frac{dE}{dy}\cdot\frac{dy}{dz}\cdot\frac{dz}{db}
]
[
\frac{dz}{db}=1
\Rightarrow \frac{dE}{db}=(-0.4201)(0.8557)\approx -0.3591
]

---

## 5) Weight Update (Gradient Descent)

Rule:
[
w_{\text{new}}=w-\eta\frac{dE}{dw},\quad b_{\text{new}}=b-\eta\frac{dE}{db}
]

### Update (w)

[
w_{\text{new}}=0.4-0.1(-0.5387)=0.4539
]

### Update (b)

[
b_{\text{new}}=-0.2-0.1(-0.3591)=-0.1641
]

---

## 6) Quick Check (After update, error কমলো কি না?)

[
z_{\text{new}}=(0.4539)(1.5)+(-0.1641)=0.6809-0.1641=0.5168
]
[
y_{\text{new}}=\tanh(0.5168)\approx 0.4756
]

New error:
[
E_{\text{new}}=\frac{1}{2}(0.8-0.4756)^2=\frac{1}{2}(0.3244)^2
\approx \frac{1}{2}(0.1052)=0.0526
]

✅ আগের (E=0.0882) থেকে কমে (E=0.0526) হয়েছে → **learning happened**।

---

### মনে রাখার মতো “tanh backprop” ফর্ম

একটা neuron-এর জন্য:
[
\delta = (y-t),(1-y^2)
]
[
\frac{dE}{dw}=\delta x,\quad \frac{dE}{db}=\delta
]
[
w\leftarrow w-\eta(\delta x),\quad b\leftarrow b-\eta\delta
]

---

=======
---

## 1) Model (Single Neuron with tanh)

[
z = wx + b
]
[
y = \tanh(z)
]

Loss (MSE):

[
E=\frac{1}{2}(t-y)^2
]

Derivative of tanh:

[
\frac{dy}{dz}=1-\tanh^2(z)=1-y^2
]

---

## 2) Given (Numbers)

* Input: (;x = 1.5)
* Target: (;t = 0.8)  (tanh-এর range -1 to +1, তাই target এই range-এ)
* Initial parameters:
  [
  w=0.4,\quad b=-0.2
  ]
* Learning rate: (\eta = 0.1)

---

## 3) Forward Pass

### Step A: Net input

[
z = wx+b = (0.4)(1.5) + (-0.2)=0.6-0.2=0.4
]

### Step B: Output (tanh)

[
y=\tanh(0.4)\approx 0.3799 ;(\approx 0.38)
]

### Step C: Error

[
E=\frac{1}{2}(t-y)^2=\frac{1}{2}(0.8-0.3799)^2
]
[
=\frac{1}{2}(0.4201)^2\approx \frac{1}{2}(0.1765)\approx 0.0882
]

---

## 4) Backpropagation (Gradients)

### Step A: (\frac{dE}{dy})

[
\frac{dE}{dy}= (y-t)=0.3799-0.8=-0.4201
]

### Step B: (\frac{dy}{dz}) for tanh

[
\frac{dy}{dz}=1-y^2 = 1-(0.3799)^2
]
[
=1-0.1443=0.8557
]

### Step C: Chain rule for (w)

[
\frac{dE}{dw}=\frac{dE}{dy}\cdot\frac{dy}{dz}\cdot\frac{dz}{dw}
]
[
\frac{dz}{dw}=x=1.5
]

So,
[
\frac{dE}{dw}=(-0.4201)(0.8557)(1.5)\approx -0.5387
]

### For bias (b)

[
\frac{dE}{db}=\frac{dE}{dy}\cdot\frac{dy}{dz}\cdot\frac{dz}{db}
]
[
\frac{dz}{db}=1
\Rightarrow \frac{dE}{db}=(-0.4201)(0.8557)\approx -0.3591
]

---

## 5) Weight Update (Gradient Descent)

Rule:
[
w_{\text{new}}=w-\eta\frac{dE}{dw},\quad b_{\text{new}}=b-\eta\frac{dE}{db}
]

### Update (w)

[
w_{\text{new}}=0.4-0.1(-0.5387)=0.4539
]

### Update (b)

[
b_{\text{new}}=-0.2-0.1(-0.3591)=-0.1641
]

---

## 6) Quick Check (After update, error কমলো কি না?)

[
z_{\text{new}}=(0.4539)(1.5)+(-0.1641)=0.6809-0.1641=0.5168
]
[
y_{\text{new}}=\tanh(0.5168)\approx 0.4756
]

New error:
[
E_{\text{new}}=\frac{1}{2}(0.8-0.4756)^2=\frac{1}{2}(0.3244)^2
\approx \frac{1}{2}(0.1052)=0.0526
]

✅ আগের (E=0.0882) থেকে কমে (E=0.0526) হয়েছে → **learning happened**।

---

### মনে রাখার মতো “tanh backprop” ফর্ম

একটা neuron-এর জন্য:
[
\delta = (y-t),(1-y^2)
]
[
\frac{dE}{dw}=\delta x,\quad \frac{dE}{db}=\delta
]
[
w\leftarrow w-\eta(\delta x),\quad b\leftarrow b-\eta\delta
]

---

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
