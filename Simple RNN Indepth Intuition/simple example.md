<<<<<<< HEAD
## 0) Simple dataset

আমরা 1টা sequence নেব (length = 3):

* Inputs:  $[x_1, x_2, x_3] = [1, 2, 3]$
* Targets: $[t_1, t_2, t_3] = [0.5, 1.0, 1.5]$

## 1) Tiny RNN model (1 hidden unit)

এটা intentionally ছোট রাখা হয়েছে:

* Hidden update:
  $$
  h_t = \tanh(a_t), \quad a_t = W_{xh}x_t + W_{hh}h_{t-1}
  $$
* Output:
  $$
  y_t = W_{hy}h_t
  $$
* Loss (MSE):
  $$
  L = \frac12\sum_{t=1}^{3}(y_t - t_t)^2
  $$

**Initial weights (ধরা):**

* $W_{xh}=0.5$
* $W_{hh}=0.1$
* $W_{hy}=1.0$
* $h_0=0$

---

## 2) Forward pass (t=1 → 3)

| t | (x_t) | (a_t=W_{xh}x_t+W_{hh}h_{t-1}) | (h_t=\tanh(a_t)) | (y_t=W_{hy}h_t) | target (t_t) |
| - | ----: | ----------------------------: | ---------------: | --------------: | -----------: |
| 1 |     1 |                        0.5000 |           0.4621 |          0.4621 |          0.5 |
| 2 |     2 |                        1.0462 |           0.7803 |          0.7803 |          1.0 |
| 3 |     3 |                        1.5780 |           0.9183 |          0.9183 |          1.5 |

Loss:
$$
L \approx 0.1940
$$

---

## 3) Backward pass (BPTT: t=3 → 1)

### দরকারি derivative

* $\frac{\partial L}{\partial y_t} = (y_t - t_t) \equiv dy_t$
* $\tanh'(a_t)=1-h_t^2$
* **BPTT recursion (scalar case):**

  * $dh_t = dy_t\cdot W_{hy} + dh_{\text{next}}$
  * $da_t = dh_t \cdot (1-h_t^2)$
  * $dh_{\text{next}} = da_t \cdot W_{hh}$

### Gradient accumulation

* $dW_{hy} += dy_t\cdot h_t$
* $dW_{xh} += da_t\cdot x_t$
* $dW_{hh} += da_t\cdot h_{t-1}$

---

### Step-by-step numbers

#### ✅ t = 3

* $dy_3 = y_3 - t_3 = 0.9183 - 1.5 = -0.5817$
* $dh_3 = dy_3 + 0 = -0.5817$
* $da_3 = dh_3(1-h_3^2) \approx -0.5817(1-0.9183^2)\approx -0.09117$
* Gradients add:

  * $dW_{hy} += (-0.5817)(0.9183)$
  * $dW_{xh} += (-0.09117)\cdot 3$
  * $dW_{hh} += (-0.09117)\cdot h_2\ (=0.7803)$
* Pass error back:

  * $dh_{\text{next}} = da_3 W_{hh} \approx -0.09117\cdot 0.1 = -0.009117$

#### ✅ t = 2

* $dy_2 = 0.7803 - 1.0 = -0.2197$
* $dh_2 = dy_2 + dh_{\text{next}} \approx -0.2197 + (-0.009117)= -0.2288$
* $da_2 \approx -0.2288(1-0.7803^2)= -0.08948$
* Gradients add:

  * $dW_{hy} += (-0.2197)(0.7803)$
  * $dW_{xh} += (-0.08948)\cdot 2$
  * $dW_{hh} += (-0.08948)\cdot h_1\ (=0.4621)$
* Pass back:

  * $dh_{\text{next}} \approx -0.08948\cdot 0.1 = -0.008948$

#### ✅ t = 1

* $dy_1 = 0.4621 - 0.5 = -0.03788$
* $dh_1 = dy_1 + dh_{\text{next}} \approx -0.03788 + (-0.008948)= -0.04683$
* $da_1 \approx -0.04683(1-0.4621^2)= -0.03683$
* Gradients add:

  * $dW_{hy} += (-0.03788)(0.4621)$
  * $dW_{xh} += (-0.03683)\cdot 1$
  * $dW_{hh} += (-0.03683)\cdot h_0\ (=0)$

---

## 4) Final gradients (এই 1টা sequence থেকে)

মোট (sum) gradients:

* $dW_{xh} \approx -0.48930$
* $dW_{hh} \approx -0.11249$
* $dW_{hy} \approx -0.72310$

---

## 5) One-step weight update (উদাহরণ)

Learning rate ধরি $lr=0.1$

$$
W \leftarrow W - lr\cdot dW
$$

* $W_{xh}: 0.5 - 0.1(-0.48930)= 0.54893$
* $W_{hh}: 0.1 - 0.1(-0.11249)= 0.11125$
* $W_{hy}: 1.0 - 0.1(-0.72310)= 1.07231$

👉 Notice: **একই weights তিনটা time step-এ ব্যবহার হয়েছে**, তাই backward-এও তিনটা step থেকে gradient **যোগ হয়ে** একবার update হয়েছে—এটাই BPTT-এর core।

---

=======
## 0) Simple dataset

আমরা 1টা sequence নেব (length = 3):

* Inputs:  $[x_1, x_2, x_3] = [1, 2, 3]$
* Targets: $[t_1, t_2, t_3] = [0.5, 1.0, 1.5]$

## 1) Tiny RNN model (1 hidden unit)

এটা intentionally ছোট রাখা হয়েছে:

* Hidden update:
  $$
  h_t = \tanh(a_t), \quad a_t = W_{xh}x_t + W_{hh}h_{t-1}
  $$
* Output:
  $$
  y_t = W_{hy}h_t
  $$
* Loss (MSE):
  $$
  L = \frac12\sum_{t=1}^{3}(y_t - t_t)^2
  $$

**Initial weights (ধরা):**

* $W_{xh}=0.5$
* $W_{hh}=0.1$
* $W_{hy}=1.0$
* $h_0=0$

---

## 2) Forward pass (t=1 → 3)

| t | (x_t) | (a_t=W_{xh}x_t+W_{hh}h_{t-1}) | (h_t=\tanh(a_t)) | (y_t=W_{hy}h_t) | target (t_t) |
| - | ----: | ----------------------------: | ---------------: | --------------: | -----------: |
| 1 |     1 |                        0.5000 |           0.4621 |          0.4621 |          0.5 |
| 2 |     2 |                        1.0462 |           0.7803 |          0.7803 |          1.0 |
| 3 |     3 |                        1.5780 |           0.9183 |          0.9183 |          1.5 |

Loss:
$$
L \approx 0.1940
$$

---

## 3) Backward pass (BPTT: t=3 → 1)

### দরকারি derivative

* $\frac{\partial L}{\partial y_t} = (y_t - t_t) \equiv dy_t$
* $\tanh'(a_t)=1-h_t^2$
* **BPTT recursion (scalar case):**

  * $dh_t = dy_t\cdot W_{hy} + dh_{\text{next}}$
  * $da_t = dh_t \cdot (1-h_t^2)$
  * $dh_{\text{next}} = da_t \cdot W_{hh}$

### Gradient accumulation

* $dW_{hy} += dy_t\cdot h_t$
* $dW_{xh} += da_t\cdot x_t$
* $dW_{hh} += da_t\cdot h_{t-1}$

---

### Step-by-step numbers

#### ✅ t = 3

* $dy_3 = y_3 - t_3 = 0.9183 - 1.5 = -0.5817$
* $dh_3 = dy_3 + 0 = -0.5817$
* $da_3 = dh_3(1-h_3^2) \approx -0.5817(1-0.9183^2)\approx -0.09117$
* Gradients add:

  * $dW_{hy} += (-0.5817)(0.9183)$
  * $dW_{xh} += (-0.09117)\cdot 3$
  * $dW_{hh} += (-0.09117)\cdot h_2\ (=0.7803)$
* Pass error back:

  * $dh_{\text{next}} = da_3 W_{hh} \approx -0.09117\cdot 0.1 = -0.009117$

#### ✅ t = 2

* $dy_2 = 0.7803 - 1.0 = -0.2197$
* $dh_2 = dy_2 + dh_{\text{next}} \approx -0.2197 + (-0.009117)= -0.2288$
* $da_2 \approx -0.2288(1-0.7803^2)= -0.08948$
* Gradients add:

  * $dW_{hy} += (-0.2197)(0.7803)$
  * $dW_{xh} += (-0.08948)\cdot 2$
  * $dW_{hh} += (-0.08948)\cdot h_1\ (=0.4621)$
* Pass back:

  * $dh_{\text{next}} \approx -0.08948\cdot 0.1 = -0.008948$

#### ✅ t = 1

* $dy_1 = 0.4621 - 0.5 = -0.03788$
* $dh_1 = dy_1 + dh_{\text{next}} \approx -0.03788 + (-0.008948)= -0.04683$
* $da_1 \approx -0.04683(1-0.4621^2)= -0.03683$
* Gradients add:

  * $dW_{hy} += (-0.03788)(0.4621)$
  * $dW_{xh} += (-0.03683)\cdot 1$
  * $dW_{hh} += (-0.03683)\cdot h_0\ (=0)$

---

## 4) Final gradients (এই 1টা sequence থেকে)

মোট (sum) gradients:

* $dW_{xh} \approx -0.48930$
* $dW_{hh} \approx -0.11249$
* $dW_{hy} \approx -0.72310$

---

## 5) One-step weight update (উদাহরণ)

Learning rate ধরি $lr=0.1$

$$
W \leftarrow W - lr\cdot dW
$$

* $W_{xh}: 0.5 - 0.1(-0.48930)= 0.54893$
* $W_{hh}: 0.1 - 0.1(-0.11249)= 0.11125$
* $W_{hy}: 1.0 - 0.1(-0.72310)= 1.07231$

👉 Notice: **একই weights তিনটা time step-এ ব্যবহার হয়েছে**, তাই backward-এও তিনটা step থেকে gradient **যোগ হয়ে** একবার update হয়েছে—এটাই BPTT-এর core।

---

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
