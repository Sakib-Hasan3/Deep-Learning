---

## 0) Formula (Transformer paper)

$$
PE(pos, 2i) = \sin\left(\frac{pos}{10000^{2i/d}}\right)
$$

$$
PE(pos, 2i+1) = \cos\left(\frac{pos}{10000^{2i/d}}\right)
$$

* (pos) = token position (0,1,2,…)
* (i) = pair index (0,1,2,…)
* (d) = embedding dimension
* **Trigonometric functions radian-এ** কাজ করে (ডিগ্রি না)

---

## 1) Set values

ধরি:

* (d = 4) ⇒ dimensions: 0,1,2,3
* তাহলে (i = 0, 1) (কারণ pair: (0,1) এবং (2,3))

---

## 2) Denominator বের করি (একদম গুরুত্বপূর্ণ অংশ)

### যখন (i=0)

$$
10000^{2i/d} = 10000^{2\cdot 0/4} = 10000^{0} = 1
$$

### যখন (i=1)

$$
10000^{2i/d} = 10000^{2\cdot 1/4} = 10000^{0.5} = \sqrt{10000} = 100
$$

---

## 3) এখন PE vector লিখি (d=4)

তাহলে:

* **dim 0:** $\sin(pos/1)=\sin(pos)$
* **dim 1:** $\cos(pos/1)=\cos(pos)$
* **dim 2:** $\sin(pos/100)$
* **dim 3:** $\cos(pos/100)$

---

## 4) Step-by-step numeric values

### ✅ Position (pos=0)

* $\sin(0)=0$
* $\cos(0)=1$
* $\sin(0/100)=\sin(0)=0$
* $\cos(0/100)=\cos(0)=1$

$$
PE(0) = [0,\ 1,\ 0,\ 1]
$$

---

### ✅ Position (pos=1)

* $\sin(1)\approx 0.841471$
* $\cos(1)\approx 0.540302$
* $\sin(1/100)=\sin(0.01)\approx 0.010000$
* $\cos(0.01)\approx 0.999950$

$$
PE(1) \approx [0.841471,\ 0.540302,\ 0.010000,\ 0.999950]
$$

---

### ✅ Position (pos=2)

* $\sin(2)\approx 0.909297$
* $\cos(2)\approx -0.416147$
* $\sin(2/100)=\sin(0.02)\approx 0.019999$
* $\cos(0.02)\approx 0.999800$

$$
PE(2) \approx [0.909297,\ -0.416147,\ 0.019999,\ 0.999800]
$$

---

### ✅ Position (pos=3)

* $\sin(3)\approx 0.141120$
* $\cos(3)\approx -0.989992$
* $\sin(3/100)=\sin(0.03)\approx 0.029996$
* $\cos(0.03)\approx 0.999550$

$$
PE(3) \approx [0.141120,\ -0.989992,\ 0.029996,\ 0.999550]
$$

---

## 5) Intuition (কেন এটা কাজ করে?)

* dim0, dim1: **fast wave** (pos directly) ⇒ position দ্রুত পরিবর্তন ধরা পড়ে
* dim2, dim3: **slow wave** (pos/100) ⇒ দূরের position গুলোর relative pattern ধরা পড়ে

অর্থাৎ বিভিন্ন dimension বিভিন্ন “frequency” তে position encode করে → model position/distance বুঝতে পারে।

---
