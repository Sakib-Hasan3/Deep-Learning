
---

# 🔷 1️⃣ Single Head আসলে কী করছে?

Single-head attention:

$$
Z = \mathrm{softmax}\left(\frac{QK^{\top}}{\sqrt{d_k}}\right)V
$$

এখানে:

* একটাই projection space
* একটাই similarity metric
* একটাই attention distribution

অর্থাৎ:

> Model একটি মাত্র similarity structure শিখছে।

---

# 🔷 2️⃣ Multi-Head কীভাবে আলাদা?

Multi-head এ:

$$
\mathrm{head}_i = \mathrm{Attention}(QW_i^Q,\; KW_i^K,\; VW_i^V)
$$

তারপর:

$$
\mathrm{MultiHead} = \mathrm{Concat}(\mathrm{head}_1,\dots,\mathrm{head}_h)W_O
$$

প্রতিটি head:

* আলাদা projection matrix
* আলাদা subspace
* আলাদা similarity metric

---

# 🔷 3️⃣ Linear Algebra Perspective

ধরি:

Single-head projection:

$$
Q = X W_Q
$$

এটা একটি linear transformation।

কিন্তু multi-head এ:

$$
Q_i = X W_i^Q
$$

মানে:

* প্রতিটি head আলাদা basis তৈরি করছে
* আলাদা feature subspace-এ কাজ করছে

এটা equivalent:


$$
X \rightarrow [\mathrm{Subspace}_1,\; \mathrm{Subspace}_2,\; \dots,\; \mathrm{Subspace}_h]
$$

---

# 🔷 4️⃣ Expressiveness Proof (Conceptual)

Single head attention:

$$
Z = A V
$$

এটা essentially:

> One weighted average over one feature space


Multi-head attention:

$$
Z = [A_1V_1,\; A_2V_2,\; \dots,\; A_hV_h]W_O
$$

এটা হচ্ছে:

> Multiple independent weighted averages → তারপর learnable mixing

এটা mathematically equivalent নয় single-head এর সাথে।

---

# 🔷 5️⃣ কেন Equivalent না?

ধরি:

Single-head dimension = 64

Multi-head:

* 4 head × 16 dimension

এগুলো একই মোট dimension হলেও:

* প্রতিটি head আলাদা projection ব্যবহার করছে
* Attention weights আলাদা

অর্থাৎ:


$$
\mathrm{softmax}(Q_1K_1^{\top}) \neq \mathrm{softmax}(Q_2K_2^{\top})
$$

এগুলো combine করলে nonlinear composition তৈরি হয়।

Single-head এটা replicate করতে পারে না unless:

* dimension massively বাড়ানো হয়

---

# 🔷 6️⃣ Nonlinear Mixing Advantage

Multi-head:


$$
\mathrm{Concat}(\mathrm{head}_1,\; \mathrm{head}_2)W_O
$$

এখানে:

* প্রথমে independent nonlinear attention
* তারপর linear combination

এটা effectively deeper function class তৈরি করে।

---

# 🔷 7️⃣ Functional Capacity Comparison

| Property                    | Single Head | Multi Head |
| --------------------------- | ----------- | ---------- |
| One similarity metric       | ✅           | ❌          |
| Multiple projection space   | ❌           | ✅          |
| Multiple attention patterns | ❌           | ✅          |
| Higher rank representation  | Limited     | Higher     |

---

# 🔷 8️⃣ Geometric Interpretation

Single head:

* একটাই angle-based similarity

Multi-head:

* আলাদা coordinate system
* আলাদা angle metric

Imagine:

Head 1 → syntactic space
Head 2 → semantic space
Head 3 → positional space

একই embedding থেকে আলাদা geometry তৈরি হচ্ছে।

---

# 🔷 9️⃣ Rank Argument

Attention output rank limited by attention matrix।

Single-head:


$$
\mathrm{rank}(Z) \le d_k
$$

Multi-head:


Concatenation increases rank potential:

$$
\mathrm{rank}(Z) \le h \cdot d_k
$$

অর্থাৎ representational capacity বাড়ছে।

---

# 🔷 🔥 Core Mathematical Insight

Multi-head attention ≠ single-head attention with bigger dimension.

কারণ:

* Separate projections
* Separate softmax distributions
* Independent attention maps

এটা effectively:


$$
f(x) = W_O [f_1(x),\; f_2(x),\; \dots,\; f_h(x)]
$$

এটা mixture-of-experts টাইপ behaviour দেয়।

---

# 🔷 10️⃣ Empirical Evidence

Transformer paper-এ দেখা গেছে:

* Single-head performance drop করে
* Multi-head performance improves significantly

---

# 🎯 Final Intuition

Single-head = এক ধরনের lens দিয়ে দেখা
Multi-head = অনেক lens দিয়ে দেখা

একটা camera vs multi-camera system।

---

