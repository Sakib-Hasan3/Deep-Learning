## ✅ Example of **Operation: ANN vs CNN** (Same Image, Two Different Ways)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1358/format%3Awebp/1%2AdKssTt7Y0SwE9C00HVdNeA.jpeg)

![Image](https://www.researchgate.net/publication/337401161/figure/fig5/AS%3A897901463089154%401591087799402/llustrating-the-first-5-steps-of-convolution-operation.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/0%2AtXW8LZTpCdzdyEVO.jpeg)

![Image](https://educative.io/api/edpresso/shot/4956264175763456/image/6412986165755904.png)

নিচে **একই image** ব্যবহার করে দেখানো হলো—
👉 **ANN কীভাবে কাজ করে**
👉 **CNN কীভাবে কাজ করে**
ধাপে ধাপে, সংখ্যাসহ।

---

# 🖼️ Input Image (Same for both)

ধরি একটি ছোট **4×4 grayscale image**:

```
Image =
[ 1  2  3  0
  0  1  2  3
  1  0  1  2
  2  1  0  1 ]
```

---

# 🧠 Example 1: ANN Operation (Step-by-Step)

### 🔹 Step 1: Flatten Image

ANN image বুঝতে পারে না, তাই **flatten** করতে হয়:

```
Flattened Input =
[1,2,3,0, 0,1,2,3, 1,0,1,2, 2,1,0,1]
```

👉 Total inputs = **16 neurons**

---

### 🔹 Step 2: Weighted Sum (One Neuron Example)

ধরি একটি hidden neuron-এর weight:

```
W = [0.1, 0.2, 0.1, 0.3, ...]
```

Calculation:

```
Z = W·X + b
Z = (1×0.1) + (2×0.2) + (3×0.1) + ...
```

👉 সব pixel একসাথে mix হয়ে যায়
👉 ANN জানে না কোন pixel কোথায় ছিল

---

### 🔹 Step 3: Activation

```
A = ReLU(Z)
```

---

### 🔹 ANN কী শিখল?

* Global number pattern
* Spatial structure ❌
* Edge / shape ❌

📌 ANN শুধু বলে:

> “এই সংখ্যার pattern আগেও দেখেছি”

---

# 🤖 Example 2: CNN Operation (Step-by-Step)

### 🔹 Step 1: Keep Image as Matrix

CNN image ভাঙে না:

```
4 × 4 matrix 그대로 থাকে
```

---

### 🔹 Step 2: Convolution

ধরি একটি **3×3 kernel**:

```
Kernel =
[ 1  0 -1
  1  0 -1
  1  0 -1 ]
```

👉 Vertical edge detector

---

### 🔹 Step 3: First Convolution Calculation

Top-left 3×3 region:

```
[1 2 3
 0 1 2
 1 0 1]
```

Calculation:

```
= (1×1 + 2×0 + 3×-1)
+ (0×1 + 1×0 + 2×-1)
+ (1×1 + 0×0 + 1×-1)

= (1 - 3) + (0 - 2) + (1 - 1)
= -4
```

👉 Feature map-এর প্রথম value = **-4**

---

### 🔹 Step 4: Slide Kernel → Feature Map

Final feature map:

```
[ -4  -2
  -2   0 ]
```

---

### 🔹 Step 5: ReLU

```
ReLU →
[ 0  0
  0  0 ]
```

👉 Edge না থাকলে zero
👉 Edge থাকলে strong value

---

### 🔹 Step 6: (Later)

* Multiple kernels
* Multiple feature maps
* Pooling
* Flatten
* Fully Connected

---

# 🔍 Final Comparison from Example

| বিষয়             | ANN           | CNN       |
| ---------------- | ------------- | --------- |
| Input handling   | Flatten       | Matrix    |
| Spatial info     | হারায়         | ধরে রাখে  |
| Feature learning | Manual / weak | Automatic |
| Edge detection   | ❌             | ✅         |
| Efficiency       | কম            | বেশি      |

---

## 🧠 এক লাইনের বোঝার মতো পার্থক্য

> **ANN সব pixel একসাথে দেখে, CNN pixel-গুলোকে তাদের জায়গাসহ দেখে।**

---

## 🎯 YouTube Animation Hook (Based on This Example)

* “একই ছবি, কিন্তু দুইটা AI দুইভাবে দেখে”
* “Flatten করলে কী হারিয়ে যায়?”
* “CNN কেন edge ধরতে পারে?”

---

