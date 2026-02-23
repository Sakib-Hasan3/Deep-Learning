<<<<<<< HEAD
---

## RNN কী?

**RNN** এমন এক ধরনের Neural Network যা **sequence data** নিয়ে কাজ করে।

📌 Sequence মানে

* বাক্য (শব্দের সিরিজ)
* টাইম সিরিজ
* Speech
* Text

👉 RNN আগের তথ্য **মনে রেখে** পরের ইনপুট বুঝতে পারে।

---

## Simple Neural Network vs RNN

### 🔹 Normal Neural Network

* প্রতিটা input আলাদা
* কোনো memory নেই

### 🔹 RNN

* আগের output / state মনে রাখে
* sequence বুঝতে পারে

---

## RNN কীভাবে কাজ করে?

একটা sentence ধরো:

```
আমি আজ স্কুলে যাই
```

RNN একবারে পুরো বাক্য নেয় না ❌
👉 শব্দ ধরে ধরে নেয়:

```
আমি → আজ → স্কুলে → যাই
```

প্রতিটা ধাপে RNN দুইটা জিনিস ব্যবহার করে:

* বর্তমান input (xₜ)
* আগের hidden state (hₜ₋₁)

---

## Simple RNN এর Formula (Basic)

প্রতি time step এ:

[
h_t = \tanh(W_h h_{t-1} + W_x x_t + b)
]

* (x_t) = বর্তমান শব্দ
* (h_{t-1}) = আগের memory
* (h_t) = নতুন memory
* (W) = weight
* tanh = activation function

---

## Visual Idea 🧠

```
x1 → [RNN] → h1
x2 → [RNN] → h2
x3 → [RNN] → h3
```

👉 h2 তৈরি হয় h1 মনে রেখে
👉 h3 তৈরি হয় h2 মনে রেখে

---

## Simple Example (Sentiment)

Sentence:

```
"এই সিনেমাটা খুব ভালো"
```

* "ভালো" আসার আগে RNN জানে
* আগে "খুব" এসেছে
  ➡️ তাই sentiment positive বুঝতে পারে

---

## Simple RNN Code (Keras / TensorFlow)

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import SimpleRNN, Dense

model = Sequential()
model.add(SimpleRNN(32, input_shape=(10, 1)))
model.add(Dense(1, activation='sigmoid'))

model.compile(optimizer='adam',
              loss='binary_crossentropy',
              metrics=['accuracy'])

model.summary()
```

📌 এখানে

* `32` = hidden units
* `10` = sequence length
* `1` = feature per step

---

## RNN কোথায় ব্যবহার হয়?

* Text classification
* Language modeling
* Simple chatbot
* Speech recognition

---

## RNN এর সমস্যা ❌

* Long sentence এ আগের তথ্য ভুলে যায়
* Vanishing gradient problem

👉 এজন্যই পরে এসেছে
✅ **LSTM**
✅ **GRU**

---

## কখন Simple RNN ব্যবহার করবে?

✔ ছোট sequence
✔ learning purpose
✔ basic NLP understanding

❌ বড় paragraph / long context → LSTM / Transformer ভালো

---

=======
---

## RNN কী?

**RNN** এমন এক ধরনের Neural Network যা **sequence data** নিয়ে কাজ করে।

📌 Sequence মানে

* বাক্য (শব্দের সিরিজ)
* টাইম সিরিজ
* Speech
* Text

👉 RNN আগের তথ্য **মনে রেখে** পরের ইনপুট বুঝতে পারে।

---

## Simple Neural Network vs RNN

### 🔹 Normal Neural Network

* প্রতিটা input আলাদা
* কোনো memory নেই

### 🔹 RNN

* আগের output / state মনে রাখে
* sequence বুঝতে পারে

---

## RNN কীভাবে কাজ করে?

একটা sentence ধরো:

```
আমি আজ স্কুলে যাই
```

RNN একবারে পুরো বাক্য নেয় না ❌
👉 শব্দ ধরে ধরে নেয়:

```
আমি → আজ → স্কুলে → যাই
```

প্রতিটা ধাপে RNN দুইটা জিনিস ব্যবহার করে:

* বর্তমান input (xₜ)
* আগের hidden state (hₜ₋₁)

---

## Simple RNN এর Formula (Basic)

প্রতি time step এ:

[
h_t = \tanh(W_h h_{t-1} + W_x x_t + b)
]

* (x_t) = বর্তমান শব্দ
* (h_{t-1}) = আগের memory
* (h_t) = নতুন memory
* (W) = weight
* tanh = activation function

---

## Visual Idea 🧠

```
x1 → [RNN] → h1
x2 → [RNN] → h2
x3 → [RNN] → h3
```

👉 h2 তৈরি হয় h1 মনে রেখে
👉 h3 তৈরি হয় h2 মনে রেখে

---

## Simple Example (Sentiment)

Sentence:

```
"এই সিনেমাটা খুব ভালো"
```

* "ভালো" আসার আগে RNN জানে
* আগে "খুব" এসেছে
  ➡️ তাই sentiment positive বুঝতে পারে

---

## Simple RNN Code (Keras / TensorFlow)

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import SimpleRNN, Dense

model = Sequential()
model.add(SimpleRNN(32, input_shape=(10, 1)))
model.add(Dense(1, activation='sigmoid'))

model.compile(optimizer='adam',
              loss='binary_crossentropy',
              metrics=['accuracy'])

model.summary()
```

📌 এখানে

* `32` = hidden units
* `10` = sequence length
* `1` = feature per step

---

## RNN কোথায় ব্যবহার হয়?

* Text classification
* Language modeling
* Simple chatbot
* Speech recognition

---

## RNN এর সমস্যা ❌

* Long sentence এ আগের তথ্য ভুলে যায়
* Vanishing gradient problem

👉 এজন্যই পরে এসেছে
✅ **LSTM**
✅ **GRU**

---

## কখন Simple RNN ব্যবহার করবে?

✔ ছোট sequence
✔ learning purpose
✔ basic NLP understanding

❌ বড় paragraph / long context → LSTM / Transformer ভালো

---

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
