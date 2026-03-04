
---

## 1) FFN-এর canonical form

একটি 2-layer FFN (MLP) সাধারণত:

$$
f(x) = W_2\,\phi\left(W_1 x + b_1\right) + b_2
$$


যেখানে

* $x \in \mathbb{R}^{d}$ — input vector
* $W_1 \in \mathbb{R}^{m\times d}$, $b_1 \in \mathbb{R}^{m}$
* $W_2 \in \mathbb{R}^{d_{out}\times m}$, $b_2 \in \mathbb{R}^{d_{out}}$
* $\phi(\cdot)$ = elementwise activation (ReLU/GELU)


Intermediate variables define করি:

$$
z = W_1 x + b_1 \quad (\in \mathbb{R}^{m})
$$

$$
h = \phi(z) \quad (\in \mathbb{R}^{m})
$$

$$
y = W_2 h + b_2 \quad (\in \mathbb{R}^{d_{out}})
$$

---

## 2) “কেন activation ছাড়া FFN useless?” — exact proof

যদি (\phi) identity হয় (অর্থাৎ (\phi(z)=z)):

$$
f(x) = W_2\left(W_1 x + b_1\right) + b_2 = (W_2 W_1) x + (W_2 b_1 + b_2)
$$

এটা আবার **একটা single linear layer** হয়ে গেল।
অর্থাৎ multi-layer হলেও পুরো নেটওয়ার্ক **affine** (linear+bias) — complex nonlinear mapping শিখতে পারবে না।

**Key result:**

> Activation না থাকলে stacked linear layers collapse করে একটি linear mapping-এ।

---

## 3) Jacobian (input-এর প্রতি sensitivity)

FFN-এর Jacobian:

$$
J(x) = \frac{\partial f(x)}{\partial x}
$$


চেইন রুল ব্যবহার করে:

$$
\frac{\partial y}{\partial x} = W_2\frac{\partial h}{\partial x} = W_2\frac{\partial \phi(z)}{\partial z}\frac{\partial z}{\partial x}
$$

$$
\frac{\partial z}{\partial x} = W_1
$$

$$
\frac{\partial \phi(z)}{\partial z} = \mathrm{Diag}\big(\phi'(z)\big)
$$

সুতরাং:

$$
J(x) = W_2\,\mathrm{Diag}\big(\phi'(W_1 x + b_1)\big)\,W_1
$$

### এর অর্থ কী?

* (\mathrm{Diag}(\phi'(\cdot))) ইনপুটের উপর নির্ভর করে বদলায়
* তাই (J(x)) ইনপুটভেদে বদলায়
* এটাই FFN-কে **nonlinear** এবং expressive করে

---

## 4) Backprop gradients (weights/bias) — derivation

ধরি loss (L(y))। Let (\delta_y=\frac{\partial L}{\partial y}) (shape (d_{out}))।

ধরি loss $L(y)$. Let $\delta_y = \frac{\partial L}{\partial y}$ (shape $d_{out}$).

### (a) $W_2, b_2$

$$
y = W_2 h + b_2
$$

$$
\frac{\partial L}{\partial W_2} = \delta_y h^T
$$

$$
\frac{\partial L}{\partial b_2} = \delta_y
$$

### (b) (W_1, b_1)

### (b) $W_1, b_1$

প্রথমে:

$$
\delta_h = \frac{\partial L}{\partial h} = W_2^{\!T} \delta_y
$$

$$
h = \phi(z) \Rightarrow \delta_z = \frac{\partial L}{\partial z} = \delta_h \odot \phi'(z)
$$

(\odot = elementwise multiply)

$$
z = W_1 x + b_1
$$

$$
\frac{\partial L}{\partial W_1} = \delta_z x^T
$$

$$
\frac{\partial L}{\partial b_1} = \delta_z
$$

এগুলোই FFN-এর standard gradient equations।

---

## 5) Transformer-এ FFN “position-wise” কেন?


Transformer encoder-এ $X \in \mathbb{R}^{n\times d_{\mathrm{model}}}$ (n tokens)।

FFN প্রতিটি token-এ একই parameters দিয়ে independently apply হয়:

$$
\mathrm{FFN}(X) = \begin{bmatrix}
f(x_1) \\
f(x_2) \\
\vdots \\
f(x_n)
\end{bmatrix}
$$

এটা equivalent:

* token dimension (sequence axis) বরাবর **no mixing**
* feature dimension বরাবর **nonlinear mixing**

অর্থাৎ:

* **Self-Attention** = token-to-token mixing
* **FFN** = per-token feature transformation

---

## 6) Why “expand then contract” ( (d_{model}\to d_{ff}\to d_{model}) )?

Transformer FFN সাধারণত:

$$
f(x) = W_2\,\phi\left(W_1 x + b_1\right) + b_2
$$

যেখানে $W_1:\;\mathbb{R}^{d_{\mathrm{model}}}\to\mathbb{R}^{d_{ff}}$ এবং $W_2:\;\mathbb{R}^{d_{ff}}\to\mathbb{R}^{d_{\mathrm{model}}}$.

* (d_{ff}) বড় হলে (\phi(\cdot))–এর পরে **অনেক বেশি nonlinear basis functions** তৈরি হয়
* এরপর (W_2) সেই basis-গুলোকে combine করে useful feature বানায়

এটা “learned feature expansion” হিসেবে কাজ করে—capacity বাড়ায়, কিন্তু output dimension আগের মতো রাখে যাতে residual/add করা যায়।

(এ কারণেই অনেক model (d_{ff}\approx 4\times d_{model}) ব্যবহার করে: capacity বনাম compute-এর ভালো tradeoff।)

---

## 7) One-line takeaway (mathematical)

### 7) One-line takeaway (mathematical)

FFN-এর শক্তি আসে এই ফ্যাক্ট থেকে:

$$
f(x) = W_2\,\phi\left(W_1 x + b_1\right) + b_2
\quad\Rightarrow\quad
J(x) = W_2\,\mathrm{Diag}\big(\phi'(W_1 x + b_1)\big)\,W_1
$$

Jacobian ইনপুটভেদে বদলায় ⇒ mapping nonlinear ⇒ expressive.

---

