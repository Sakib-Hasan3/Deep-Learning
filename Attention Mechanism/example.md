---

## Mini dataset

Input sentence (encoder side): 3টি token
$$[x_1, x_2, x_3]$$

Encoder থেকে পাওয়া hidden states (২-ডাইমেনশন):
$$
h_1 = \begin{bmatrix}1 \\ 0\end{bmatrix},\quad
h_2 = \begin{bmatrix}0 \\ 2\end{bmatrix},\quad
h_3 = \begin{bmatrix}1 \\ 1\end{bmatrix}
$$

Decoder একটি নির্দিষ্ট step (t)-এ আছে, তার state (query):
$$
s_t = \begin{bmatrix}1 \\ 1\end{bmatrix}
$$

---

## Step 1) Score (alignment) হিসাব

Dot-product score:
$$
e_{t,i} = s_t^{\top} h_i
$$

Numerical calculations:

- $e_{t,1} = s_t^{\top} h_1 = 1\cdot1 + 1\cdot0 = 1$
- $e_{t,2} = s_t^{\top} h_2 = 1\cdot0 + 1\cdot2 = 2$
- $e_{t,3} = s_t^{\top} h_3 = 1\cdot1 + 1\cdot1 = 2$

অর্থাৎ:
$$
e_t = \begin{bmatrix}1 \\ 2 \\ 2\end{bmatrix}
$$

---

## Step 2) Softmax করে Attention Weights বের করা

$$
\alpha_{t,i} = \frac{\exp(e_{t,i})}{\sum_j \exp(e_{t,j})}
$$


$$
e^{1} \approx 2.718,\qquad e^{2} \approx 7.389
$$

Sum:

$$
2.718 + 7.389 + 7.389 = 17.496
$$

Weights:

- $\alpha_{t,1} = 2.718 / 17.496 \approx 0.155$
- $\alpha_{t,2} = 7.389 / 17.496 \approx 0.422$
- $\alpha_{t,3} = 7.389 / 17.496 \approx 0.422$

✅ Meaning: decoder এই step-এ **token 2 এবং 3**-এ বেশি focus করছে।

---

## Step 3) Context vector (weighted sum)

[\[c_t = \sum_{i=1}^{3} \alpha_{t,i} h_i\]


$$
c_t = 0.155\begin{bmatrix}1 \\ 0\end{bmatrix} + 0.422\begin{bmatrix}0 \\ 2\end{bmatrix} + 0.422\begin{bmatrix}1 \\ 1\end{bmatrix}
$$

প্রথম component:
$$
c_{t,1} = 0.155\cdot1 + 0.422\cdot0 + 0.422\cdot1 = 0.155 + 0 + 0.422 = 0.577
$$

দ্বিতীয় component:
$$
c_{t,2} = 0.155\cdot0 + 0.422\cdot2 + 0.422\cdot1 = 0 + 0.844 + 0.422 = 1.266
$$

✅ তাই:
$$
c_t = \begin{bmatrix}0.577 \\ 1.266\end{bmatrix}
$$

---

## Step 4) Context + Decoder state দিয়ে Output (একটা tiny output layer)


ধরি আমরা combined vector নেই:

$$
u_t = s_t + c_t = \begin{bmatrix}1 \\ 1\end{bmatrix} + \begin{bmatrix}0.577 \\ 1.266\end{bmatrix} = \begin{bmatrix}1.577 \\ 2.266\end{bmatrix}
$$

এবার ধরো vocabulary দুইটা ক্লাস: **A** এবং **B**।
Logits (simple example):

- $z(A) = [1\; 0]\cdot u_t = 1.577$ (selects first component)
- $z(B) = [0\; 1]\cdot u_t = 2.266$ (selects second component)

Softmax:

$$
p(A) = \frac{e^{1.577}}{e^{1.577} + e^{2.266}},\quad
p(B) = \frac{e^{2.266}}{e^{1.577} + e^{2.266}}
$$

Approx:

- $e^{1.577} \approx 4.84$
- $e^{2.266} \approx 9.64$

Sum $\approx 14.48$

So:

- $p(A) \approx 4.84 / 14.48 = 0.334$
- $p(B) \approx 9.64 / 14.48 = 0.666$

✅ Prediction: **B**

---

# এই উদাহরণে তুমি কী শিখলে (core intuition)

* **Score** বলে: “decoder এখন কোন encoder state-কে বেশি relevant ভাবছে?”
* **Softmax weights** সেই relevance-কে probability বানায়
* **Context vector** হলো encoder hidden গুলোর “weighted summary”
* Decoder এই context ব্যবহার করে **এই step-এ** output দেয় (এটাই dynamic context)

---

