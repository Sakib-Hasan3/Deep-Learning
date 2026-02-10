## Setup (খুব ছোট BiRNN)


Sequence length $T=3$

**Inputs:**
$x_1=1$, $x_2=2$, $x_3=3$


আমরা সহজ করার জন্য **activation (tanh) বাদ** দিয়ে purely linear রাখছি:

### Forward RNN

$$
\overrightarrow{h_t}=0.5x_t + 0.1\overrightarrow{h_{t-1}},\quad \overrightarrow{h_0}=0
$$


### Backward RNN

$$
\overleftarrow{h_t}=0.4x_t + 0.2\overleftarrow{h_{t+1}},\quad \overleftarrow{h_4}=0
$$


### Combine (concat)

$$
h_t = [\overrightarrow{h_t}\;||\;\overleftarrow{h_t}]
$$


### Output (single scalar per time step)

$$
y_t = 1\cdot \overrightarrow{h_t} + 1\cdot \overleftarrow{h_t}
$$
(মানে দুইটা যোগ করলাম)

---

## Step 1: Forward pass (left → right)


### (t=1)

$$
\overrightarrow{h_1}=0.5(1)+0.1(0)=0.5
$$


### (t=2)

$$
\overrightarrow{h_2}=0.5(2)+0.1(0.5)=1+0.05=1.05
$$


### (t=3)

$$
\overrightarrow{h_3}=0.5(3)+0.1(1.05)=1.5+0.105=1.605
$$


✅ Forward hidden:
$$
(\overrightarrow{h_1},\overrightarrow{h_2},\overrightarrow{h_3})=(0.5,1.05,1.605)
$$

---

## Step 2: Backward pass (right → left)


### (t=3) (শেষ থেকে শুরু)

$$
\overleftarrow{h_3}=0.4(3)+0.2(0)=1.2
$$


### (t=2)

$$
\overleftarrow{h_2}=0.4(2)+0.2(1.2)=0.8+0.24=1.04
$$


### (t=1)

$$
\overleftarrow{h_1}=0.4(1)+0.2(1.04)=0.4+0.208=0.608
$$


✅ Backward hidden:
$$
(\overleftarrow{h_1},\overleftarrow{h_2},\overleftarrow{h_3})=(0.608,1.04,1.2)
$$

---

## Step 3: Combine + Output


### (t=1)

$$
h_1=[0.5||0.608],\quad y_1=0.5+0.608=1.108
$$


### (t=2)

$$
h_2=[1.05||1.04],\quad y_2=1.05+1.04=2.09
$$


### (t=3)

$$
h_3=[1.605||1.2],\quad y_3=1.605+1.2=2.805
$$

---

## Final Result (এক নজরে)

| t | (x_t) | (\overrightarrow{h_t}) | (\overleftarrow{h_t}) | concat (h_t)     | (y_t) |
| - | ----: | ---------------------: | --------------------: | ---------------- | ----: |
| 1 |     1 |                  0.500 |                 0.608 | [0.500 || 0.608] | 1.108 |
| 2 |     2 |                  1.050 |                 1.040 | [1.050 || 1.040] | 2.090 |
| 3 |     3 |                  1.605 |                 1.200 | [1.605 || 1.200] | 2.805 |

---

## এই উদাহরণ থেকে মূল শেখার পয়েন্ট

* **Forward hidden** = past context (আগের দিকের তথ্য)
* **Backward hidden** = future context (পরে কী আছে তার তথ্য)
* BiRNN প্রতিটি position-এ **দুই দিকের context যোগ করে** output দেয়
  → ambiguity কমে, labeling/understanding ভালো হয়


