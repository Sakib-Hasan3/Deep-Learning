---

## 0) Tiny dataset (one training example)

ধরি আমরা “translation-like” task করছি:

**Input (source):** `A B`
**Output (target):** `X Y`

Decoder-এর জন্য special tokens:

* `<SOS>` শুরু
* `<EOS>` শেষ

Target sequence হবে: `<SOS> → X → Y → <EOS>`

---

## 1) Model definition (super simple)

### Token → number (embedding as scalar)

Encoder input embedding:

* (e(A)=1)
* (e(B)=2)

Decoder input embedding:

* (e(<SOS>)=0)
* (e(X)=1)
* (e(Y)=2)


### Encoder RNN (linear)

$$
h_t = 0.5\,e(x_t) + 0.1\,h_{t-1}, \quad h_0=0
$$


**Context vector:**
$$
C = h_T
$$


### Decoder RNN (linear)

$$
s_t = 0.6\,e(y_{t-1}) + 0.2\,s_{t-1} + 0.5\,C, \quad s_0=0
$$


### Output layer (logits for 3 classes: X, Y, EOS)

$$
z_t(X)=1.0\,s_t,\quad z_t(Y)=0.5\,s_t,\quad z_t(EOS)=-0.5\,s_t
$$
$$
p_t = \text{softmax}(z_t)
$$

---

# Part A — Encoder (stepwise)


## Step E1: read `A`

$$
h_1 = 0.5(1)+0.1(0)=0.5
$$


## Step E2: read `B`

$$
h_2 = 0.5(2)+0.1(0.5)=1+0.05=1.05
$$


✅ Context:
$$
C=h_2=1.05
$$

Intuition: Encoder “A B” পড়ে এক লাইনে “meaning summary” বানাল—এটাই (C)।

---

# Part B — Decoder (stepwise generation)


## Step D1: input `<SOS>` → predict first token

$$
s_1 = 0.6(0)+0.2(0)+0.5(1.05)=0.525
$$


Logits:

* $z_1(X)=0.525$
* $z_1(Y)=0.2625$
* $z_1(EOS)=-0.2625$


Softmax করতে $e^{(\cdot)}$ দরকার:

* $e^{0.525}\approx 1.690$
* $e^{0.2625}\approx 1.300$
* $e^{-0.2625}\approx 0.769$


Sum $=1.690+1.300+0.769=3.759$


Probabilities:

* $p_1(X)=1.690/3.759 \approx 0.45$
* $p_1(Y)=1.300/3.759 \approx 0.35$
* $p_1(EOS)=0.769/3.759 \approx 0.20$

✅ Prediction (max): **X**

---


## Step D2: input previous predicted `X` → predict next

$$
s_2 = 0.6(1)+0.2(0.525)+0.5(1.05)=0.6+0.105+0.525=1.23
$$


Logits:

* $z_2(X)=1.23$
* $z_2(Y)=0.615$
* $z_2(EOS)=-0.615$


Exponentials (approx):

* $e^{1.23}\approx 3.421$
* $e^{0.615}\approx 1.850$
* $e^{-0.615}\approx 0.541$


Sum $=3.421+1.850+0.541=5.812$


Probabilities:

* $p_2(X)\approx 3.421/5.812 = 0.59$
* $p_2(Y)\approx 1.850/5.812 = 0.32$
* $p_2(EOS)\approx 0.541/5.812 = 0.09$

➡️ এখানে max **X** আসছে, কিন্তু আমাদের target ছিল **Y**।
এটাই শেখায়: training করে weights শিখতে হয়—না হলে ভুল হতে পারে।

(Teacher forcing থাকলে এই step-এ আমরা decoder-কে **true token `X`** দিয়েছি—সেটা এখানে একই, কিন্তু পরের step-এ পার্থক্য দেখা যায়।)

---


## Step D3: (Teacher Forcing ধরে) input `Y` → predict `<EOS>`

Training-এর সময় সাধারণত teacher forcing করা হয়, তাই $y_{t-1}$ হিসেবে **true** token দেওয়া হয়।
তাহলে step 3-এ input হবে `Y`:

$$
s_3 = 0.6(2)+0.2(1.23)+0.5(1.05)=1.2+0.246+0.525=1.971
$$


Logits:

* $z_3(X)=1.971$
* $z_3(Y)=0.9855$
* $z_3(EOS)=-0.9855$

এখানেও max **X** হবে (কারণ logits definition এমন), তাই model এখনও “EOS” দিতে শিখেনি—training দরকার।

---

## এই mini-example থেকে মূল বোঝার পয়েন্ট ✅

1. **Encoder** input sequence পড়ে শেষ hidden থেকে **context (C)** বানায়।
2. **Decoder** প্রতিটি step-এ:

   * আগের token (SOS/previous word)
   * আগের decoder state
   * context (C)
     → দিয়ে নতুন state (s_t) বানায়, তারপর softmax দিয়ে শব্দ বেছে নেয়।
3. যদি weights শেখানো না থাকে, prediction ভুল হবে—এটাই training-এর কাজ।

---

