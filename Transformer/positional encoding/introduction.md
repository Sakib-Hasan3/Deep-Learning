# Positional Encoding (Transformer-এ এর ভূমিকা ও কাজ)

Transformer-এর attention mechanism নিজে থেকে **sequence order বোঝে না**।
কারণ attention কেবল similarity দেখে—token কোন position-এ আছে সেটা জানে না।

তাই আমরা **Positional Encoding (PE)** যোগ করি।

---

# 1️⃣ কেন দরকার?

ধরি বাক্য:

```
"I love you"
```

আরেকটা:

```
"You love I"
```

Embedding একই হলে attention similarity-ই দেখবে।
Order না দিলে model বুঝবে না কে subject, কে object।

👉 তাই position তথ্য inject করতে হয়।

---

# 2️⃣ Basic Idea

প্রতিটি token embedding-এর সাথে একটি positional vector যোগ করা হয়:

$$
X_{final} = X_{embedding} + PE
$$

এখানে:

* (X_{embedding}) = semantic information
* (PE) = structural/order information

---

# 3️⃣ Sinusoidal Positional Encoding (Original Transformer)

Paper: *Attention Is All You Need*

$$
PE(pos, 2i) = \sin\left(\frac{pos}{10000^{2i/d}}\right)
$$

$$
PE(pos, 2i+1) = \cos\left(\frac{pos}{10000^{2i/d}}\right)
$$

Where:

* (pos) = position index
* (i) = dimension index
* (d) = embedding dimension

---

# 4️⃣ Intuition Behind Sin & Cos

## 🔹 Multi-frequency encoding

Different dimensions encode different wavelengths.

* Lower dimension → high frequency
* Higher dimension → low frequency

এটা position-কে multi-scale ভাবে represent করে।

---

# 5️⃣ Mathematical Property (Relative Shift)

Sinusoidal encoding-এর বড় সুবিধা:

$$
PE(pos + k)
$$

কে linear combination দিয়ে (PE(pos)) থেকে বের করা যায়।

কারণ:

$$
\sin(a+b)=\sin a \cos b + \cos a \sin b
$$

👉 Model relative distance শিখতে পারে।

---

# 6️⃣ Visual Understanding

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AH00aHX2y16eNbeceLC13cA.png)

![Image](https://www.researchgate.net/publication/343349141/figure/fig1/AS%3A925937990373377%401597772228899/The-heatmap-visualization-of-positional-encoding-There-are-100-rows-and-each-row-is-a.png)

![Image](https://cdn.hashnode.com/res/hashnode/image/upload/v1742329614922/afe61e71-be4a-4d48-a19e-94fc1f4bfa0a.png)

![Image](https://us1.discourse-cdn.com/hellohellohello/optimized/3X/5/d/5dd6629d86fd21957d5b6aac1ae0e5e2465a9089_2_690x440.png)

---

# 7️⃣ Absolute vs Learned Positional Encoding

### 🔹 Absolute (Sinusoidal)

* Fixed
* Generalizes to longer sequences

### 🔹 Learned

* Trainable parameter
* Flexible
* Fixed maximum length

---

# 8️⃣ Why Add Instead of Concatenate?

$$
X + PE
$$

কারণ:

* Same dimension maintain হয়
* Model learnable mixing করতে পারে
* Simpler computation

---

# 9️⃣ Transformer Flow With PE

```text
Token → Embedding
         ↓
   + Positional Encoding
         ↓
   Multi-Head Attention
```

---

# 🔟 Big Conceptual Insight

Embedding = “What”
Positional Encoding = “Where”

Together → “What at Where”

---

# 11️⃣ Advanced Variants

Modern models use:

* Relative Positional Encoding
* Rotary Positional Embedding (RoPE)
* ALiBi

এগুলো long context handling improve করে।

---

# 🎯 Final Summary

Positional Encoding:

* Order inject করে
* Structure preserve করে
* Relative distance recoverable করে
* Attention-কে sequence-aware বানায়

---

