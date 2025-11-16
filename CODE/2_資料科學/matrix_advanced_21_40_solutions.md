# 進階矩陣運算題庫（第 21～40 題，含解答）

> 說明：本檔為第 21～40 題進階矩陣題目，並加入重點解答與部分 Python（NumPy）驗算程式碼。

---

## 📘 A. 特徵值／特徵向量（Eigenvalues & Eigenvectors）

---

### 第 21 題：求底下矩陣的特徵值與特徵向量（2×2）

$$ 
A = \begin{pmatrix}
4 & 1 \\
2 & 3
\end{pmatrix}
$$

**解答：**

特徵方程式：

$$
\det(A-\lambda I) = 
\begin{vmatrix}
4-\lambda & 1\\
2 & 3-\lambda
\end{vmatrix}
= (4-\lambda)(3-\lambda)-2
$$

展開：

$$
(4-\lambda)(3-\lambda)-2 = (12 - 7\lambda + \lambda^2) - 2
= \lambda^2 - 7\lambda + 10
$$

解二次方程式：

$$
\lambda^2 - 7\lambda + 10 = 0
$$

$$
\lambda = \frac{7 \pm \sqrt{49 - 40}}{2}
= \frac{7 \pm 3}{2}
$$

故  
- $\lambda_1 = 5$ 
- $\lambda_2 = 2$

**Python 驗算：**
```python
import numpy as np
A = np.array([[4,1],[2,3]])
np.linalg.eigvals(A)
```

---

### 第 22 題：求特徵向量

A 同上。

**解答：**

1. 對 $\lambda_1 = 5$：求 $(A-5I)v=0$

$$
A-5I = \begin{pmatrix}
-1 & 1  \\ 
2 & -2
\end{pmatrix}
$$



解：

$$
x -  y = 0  \Rightarrow  y = x 
$$

故特徵向量可取：

$$
v_1 = \begin{pmatrix}
1 \\ 
1
\end{pmatrix}
$$

2. 對 $\lambda_2 = 2$：求 $(A-2I)v=0$

$$
A-2I = \begin{pmatrix}
2 & 1 \\ 
2 & 1
\end{pmatrix}
$$

解：

$$
2x + y = 0 \Rightarrow y = -2x
$$

故特徵向量可取：

$$
v_2 = \begin{pmatrix}
1 \\ 
-2
\end{pmatrix}
$$

**Python 驗算：**
```python
vals, vecs = np.linalg.eig(A)
vals, vecs  # vecs 的每一欄為對應特徵向量
```

---

### 第 23 題：對稱矩陣必可對角化

A = \\(\begin{bmatrix}2 & 1\\1 & 2\end{bmatrix}\\)

**(1) 特徵值**

\\[
\det(A-\lambda I) = 
\begin{vmatrix}
2-\lambda & 1\\
1 & 2-\lambda
\end{vmatrix}
= (2-\lambda)^2 - 1
\\]

令其為 0：
\\[
(2-\lambda)^2 - 1 = 0
\\]
\\[
(2-\lambda)^2 = 1 \Rightarrow 2-\lambda = \pm 1
\\]
\\[
\Rightarrow \lambda_1 = 3,\ \lambda_2 = 1
\\]

**(2) 特徵向量**

- 對 \(\lambda_1 = 3\)：

\\[
A-3I = \begin{bmatrix}-1 & 1\\1 & -1\end{bmatrix}
\\]
\\[
- x + y = 0 \Rightarrow y = x
\\]
\\[
v_1 = \begin{bmatrix}1 \\ 1\end{bmatrix}
\\]

- 對 \(\lambda_2 = 1\)：

\\[
A-I = \begin{bmatrix}1 & 1\\1 & 1\end{bmatrix}
\\]
\\[
x + y = 0 \Rightarrow y = -x
\\]
\\[
v_2 = \begin{bmatrix}1 \\ -1\end{bmatrix}
\\]

**(3) 寫出對角化**

令
\\[
P = \begin{bmatrix}1 & 1\\1 & -1\end{bmatrix},\
D = \begin{bmatrix}3 & 0\\0 & 1\end{bmatrix}
\\]

則有：
\\[
A = P D P^{-1}
\\]

(可另外計算 \(P^{-1}\) 驗證。)

---

### 第 24 題：不可對角化矩陣範例

A = \\(\begin{bmatrix}1 & 1\\0 & 1\end{bmatrix}\\)

**(1) 特徵值**

\\[
\det(A-\lambda I) = 
\begin{vmatrix}
1-\lambda & 1\\
0 & 1-\lambda
\end{vmatrix}
= (1-\lambda)^2
\\]

故只有單一特徵值 \(\lambda = 1\)，其代數重數為 2。

**(2) 特徵向量與是否可對角化**

\[
(A-I)v = 0
= \begin{bmatrix}0 & 1\\0 & 0\end{bmatrix}
\begin{bmatrix}x\\y\end{bmatrix}
= 0
\Rightarrow y = 0,\ x \text{ 任意}
\]

特徵空間：
\\[
v = \begin{bmatrix}1\\0\end{bmatrix}t
\\]

幾何重數為 1 (只有一個線性獨立特徵向量)，小於代數重數 2  
→ **不可對角化**。

---

### 第 25 題：3×3 特徵值

A =
\\[
\begin{bmatrix}
3 & 0 & 0\\
0 & 2 & 1\\
0 & 1 & 2
\end{bmatrix}
\\]

**解答：**

(1) 其為分塊矩陣：第一維與後兩維分開。

第二塊 B = \\(\begin{bmatrix}2 & 1\\1 & 2\end{bmatrix}\\)，  
其特徵值如前題：3 與 1。

因此整個 A 的特徵值為：

- 來自第一維：3  
- 來自 B：3, 1  

**故特徵值集合：** \(\{3, 3, 1\}\)

---

### 第 26 題：trace / det 與特徵值關係

A = \\(\begin{bmatrix}2 & 1\\1 & 2\end{bmatrix}\\)  
前面求得特徵值：\(\lambda_1 = 3, \lambda_2 = 1\)

**驗證：**

- trace：

\\[
\text{tr}(A) = 2 + 2 = 4
\\]
\\[
\lambda_1 + \lambda_2 = 3 + 1 = 4
\\]

- determinant：

\\[
\det(A) = 2\cdot 2 - 1\cdot 1 = 4 - 1 = 3
\\]
\\[
\lambda_1 \lambda_2 = 3 \cdot 1 = 3
\\]

兩者皆符合  
→ 驗證「特徵值之和＝trace」、「特徵值之積＝det」。

---

## 📘 B. 對角化（Diagonalization）

---

### 第 27 題：判斷是否可對角化

A = \\(\begin{bmatrix}5 & 4\\1 & 2\end{bmatrix}\\)

**解答：**

先求特徵值：

\\[
\det(A-\lambda I) =
\begin{vmatrix}
5-\lambda & 4\\
1 & 2-\lambda
\end{vmatrix}
= (5-\lambda)(2-\lambda) - 4
\\]
\\[
= (10 - 7\lambda + \lambda^2) - 4
= \lambda^2 - 7\lambda + 6
\\]

解：
\\[
\lambda^2 - 7\lambda + 6 = 0
\\]
\\[
\lambda = \frac{7 \pm \sqrt{49-24}}{2}
= \frac{7 \pm 5}{2}
\\]
\\[
\Rightarrow \lambda_1 = 6,\ \lambda_2 = 1
\\]

兩個特徵值皆不相同 → 幾何重數一定為 1+1  
→ **A 可對角化**。

---

### 第 28 題：對角化應用：A^{10}

同第 27 題 A。  
由對角化 \(A = P D P^{-1}\)，則

\\[
A^{10} = P D^{10} P^{-1}
\\]

D 為對角矩陣：
\\[
D = \begin{bmatrix}6 & 0\\0 & 1\end{bmatrix}
\\]
\\[
D^{10} = \begin{bmatrix}6^{10} & 0\\0 & 1^{10}\end{bmatrix}
= \begin{bmatrix}6^{10} & 0\\0 & 1\end{bmatrix}
\\]

實際上要算出數值矩陣，需要求出 P 與 \(P^{-1}\)，  
但**理論上**已可表示：
\\[
A^{10} = P \begin{bmatrix}6^{10} & 0\\0 & 1\end{bmatrix} P^{-1}
\\]

**Python 驗算（直接次方）：**
```python
import numpy as np
A = np.array([[5,4],[1,2]])
np.linalg.matrix_power(A, 10)
```

---

## 📘 C. SVD（奇異值分解）

---

### 第 29 題：奇異值

A =
\\[
\begin{bmatrix}
3 & 4\\
0 & 0
\end{bmatrix}
\\]

奇異值為 \(\sqrt{A^T A}\) 的特徵值開根號。

\\[
A^T A =
\begin{bmatrix}
3 & 0\\
4 & 0
\end{bmatrix}
\begin{bmatrix}
3 & 4\\
0 & 0
\end{bmatrix}
=
\begin{bmatrix}
9 & 12\\
12 & 16
\end{bmatrix}
\\]

求 \(A^T A\) 特徵值：

\\[
\det(A^T A - \lambda I) =
\begin{vmatrix}
9-\lambda & 12\\
12 & 16-\lambda
\end{vmatrix}
= (9-\lambda)(16-\lambda) - 144
\\]
\\[
= (144 - 25\lambda + \lambda^2) - 144
= \lambda^2 - 25\lambda
= \lambda(\lambda - 25)
\\]

故特徵值為 25, 0。  
奇異值為其非負平方根：

- \(\sigma_1 = 5\)  
- \(\sigma_2 = 0\)

**Python 驗算：**
```python
import numpy as np
A = np.array([[3,4],[0,0]])
u, s, vh = np.linalg.svd(A)
s   # [5. 0.]
```

---

### 第 30 題：Rank 與奇異值

承第 29 題，奇異值為 (5, 0)。

**結論：**

非零奇異值個數 = rank(A)  
→ rank(A) = 1。

---

### 第 31 題：SVD 主軸方向（幾何）

承第 29 題。

**說明：**

SVD：\\(A = U \Sigma V^T\\)

- V 的欄向量為「輸入空間」的正交主軸  
- U 的欄向量為「輸出空間」的正交主軸  
- \(\Sigma\\) 中非零奇異值 5 對應一條主軸方向，其餘為壓扁成 0。

因 rank = 1，  
單位球在 A 映射後為一條線段（橢圓退化），  
主軸方向由對應最大奇異值 5 的 V 的欄向量給出。

**Python 看 V：**
```python
u, s, vh = np.linalg.svd(A)
vh  # V^T，逐列為 V 的行向量轉置
```

---

### 第 32 題：最佳秩 k 近似

**概念解答（簡述）：**

對任意矩陣 \(A\in\mathbb{R}^{m\times n}\\) 做 SVD：

\\[
A = U \Sigma V^T
\\]

令 \(\Sigma_k\\) 為只保留前 k 個最大奇異值、其他設為 0 的對角矩陣，  
對應的 U, V 的前 k 欄為 \(U_k, V_k\\)。

則
\\[
A_k = U_k \Sigma_k V_k^T
\\]
為 **在所有 rank ≤ k 的矩陣中，最接近 A**（就 Frobenius norm 或 2- norm 而言）。  
這是「Eckart–Young–Mirsky theorem」的內容。

當 k=1 時，\\(A_1\\) 是保留最大奇異值與其對應的左右奇異向量 \(u_1, v_1\\) 的外積：
\\[
A_1 = \sigma_1 u_1 v_1^T
\\]

---

## 📘 D. PCA（主成分分析）

---

### 第 33 題：協方差矩陣

資料：
\\[
X = 
\begin{bmatrix}
1 & 2\\
2 & 3\\
3 & 4
\end{bmatrix}
\\]
每列是一筆樣本，兩維特徵。

**(1) mean centering**

各維平均：

\\[
\bar{x}_1 = \frac{1+2+3}{3} = 2,\quad
\bar{x}_2 = \frac{2+3+4}{3} = 3
\\]

中心化後：

\\[
X_c =
\begin{bmatrix}
1-2 & 2-3\\
2-2 & 3-3\\
3-2 & 4-3
\end{bmatrix}
=
\begin{bmatrix}
-1 & -1\\
0 & 0\\
1 & 1
\end{bmatrix}
\\]

**(2) 協方差矩陣**

使用樣本協方差：\\(\frac{1}{n-1} X_c^T X_c\\)，n=3：

\\[
X_c^T X_c =
\begin{bmatrix}
-1 & 0 & 1\\
-1 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
-1 & -1\\
0 & 0\\
1 & 1
\end{bmatrix}
=
\begin{bmatrix}
2 & 2\\
2 & 2
\end{bmatrix}
\\]

所以：
\\[
C = \frac{1}{2}
\begin{bmatrix}
2 & 2\\
2 & 2
\end{bmatrix}
=
\begin{bmatrix}
1 & 1\\
1 & 1
\end{bmatrix}
\\]

**Python 驗算：**
```python
import numpy as np
X = np.array([[1,2],[2,3],[3,4]])
Xc = X - X.mean(axis=0)
C = np.cov(Xc.T, bias=False)  # (n-1) 分母
C
```

---

### 第 34 題：PCA 主軸方向

協方差矩陣：
\\[
C =
\begin{bmatrix}
1 & 1\\
1 & 1
\end{bmatrix}
\\]

求特徵值與特徵向量：

\\[
\det(C - \lambda I) =
\begin{vmatrix}
1-\lambda & 1\\
1 & 1-\lambda
\end{vmatrix}
= (1-\lambda)^2 - 1
\\]
\\[
= \lambda^2 - 2\lambda
= \lambda(\lambda-2)
\\]

特徵值：\(\lambda_1 = 2,\ \lambda_2 = 0\\)

- 對 \(\lambda_1 = 2\)：

\\[
C - 2I =
\begin{bmatrix}
-1 & 1\\
1 & -1
\end{bmatrix}
\Rightarrow -x + y = 0 \Rightarrow y = x
\\]
\\[
v_1 = \begin{bmatrix}1\\1\end{bmatrix}
\\]

- 對 \(\lambda_2 = 0\)：

\\[
C - 0I = C =
\begin{bmatrix}
1 & 1\\
1 & 1
\end{bmatrix}
\Rightarrow x + y = 0 \Rightarrow y = -x
\\]
\\[
v_2 = \begin{bmatrix}1\\-1\end{bmatrix}
\\]

因 \(\lambda_1 = 2 > 0 = \lambda_2\\)，  
**PC1 即方向 v1 ∝ [1,1]^T**。

---

### 第 35 題：資料投影到 PC1

PC1 單位向量：

\\[
u_1 = \frac{1}{\sqrt{2}}
\begin{bmatrix}1\\1\end{bmatrix}
\\]

中心化後資料：
\\[
X_c =
\begin{bmatrix}
-1 & -1\\
0 & 0\\
1 & 1
\end{bmatrix}
\\]

投影係數為：
\\[
z_i = u_1^T x_{c,i}
\\]

計算：

1.  第一筆：\\(x_c = [-1, -1]^T\\)

\\[
z_1 = \frac{1}{\sqrt{2}}(-1) + \frac{1}{\sqrt{2}}(-1) = -\sqrt{2}
\\]

2. 第二筆：\\(x_c = [0,0]^T\\) → 投影為 0

3. 第三筆：\\(x_c = [1,1]^T\\) → \\(z_3 = \sqrt{2}\\)

故 1 維投影結果約為：

\\[
z = \begin{bmatrix}-\sqrt{2}\\0\\\sqrt{2}\end{bmatrix}
\\]

**Python 驗算：**
```python
X = np.array([[1,2],[2,3],[3,4]])
Xc = X - X.mean(axis=0)
u1 = np.array([1,1]) / np.sqrt(2)
z = Xc @ u1
z
```

---

### 第 36 題：PCA 與 SVD 關係

令中心化後資料為 \(X_c\in\mathbb{R}^{n\times d}\\)，做 SVD：

\\[
X_c = U \Sigma V^T
\\]

- 協方差矩陣：
\\[
C = \frac{1}{n-1} X_c^T X_c
= \frac{1}{n-1} (V \Sigma^T U^T)(U \Sigma V^T)
= \frac{1}{n-1} V \Sigma^2 V^T
\\]

可見 C 的特徵分解為：
\\[
C = V \left(\frac{\Sigma^2}{n-1}\right) V^T
\\]

因此：

- V 的欄向量為 C 的特徵向量 → 即 **PCA 的主軸方向**  
- 對角線 \(\frac{\sigma_i^2}{n-1}\\) 為對應主成分的變異量。

---

## 📘 E. 更多進階矩陣性質

---

### 第 37 題：正定矩陣判斷

A =
\\[
\begin{bmatrix}
2 & -1\\
-1 & 2
\end{bmatrix}
\\]

對稱矩陣，可用主子式或特徵值判斷。

**主子式法：**

- 第一主子式：\\(2 > 0\\)
- 全部行列式：
\\[
\det(A) = 2\cdot 2 - (-1)(-1) = 4 - 1 = 3 > 0
\\]

對稱矩陣且所有主子式 > 0 → **A 為正定矩陣**。

---

### 第 38 題：正交矩陣判斷

Q =
\\[
\begin{bmatrix}
3/5 & 4/5\\
-4/5 & 3/5
\end{bmatrix}
\\]

檢查 \(Q^T Q = I\\)。

計算：
\\[
Q^T =
\begin{bmatrix}
3/5 & -4/5\\
4/5 & 3/5
\end{bmatrix}
\\]

\\[
Q^T Q =
\begin{bmatrix}
3/5 & -4/5\\
4/5 & 3/5
\end{bmatrix}
\begin{bmatrix}
3/5 & 4/5\\
-4/5 & 3/5
\end{bmatrix}
=
\begin{bmatrix}
(3/5)^2 + (-4/5)^2 & 3/5\cdot4/5 + (-4/5)\cdot3/5\\
4/5\cdot3/5 + 3/5\cdot(-4/5) & (4/5)^2 + (3/5)^2
\end{bmatrix}
\\]
\\[
=
\begin{bmatrix}
9/25 + 16/25 & 12/25 - 12/25\\
12/25 - 12/25 & 16/25 + 9/25
\end{bmatrix}
=
\begin{bmatrix}
1 & 0\\
0 & 1
\end{bmatrix}
= I
\\]

故 Q 為正交矩陣。

---

### 第 39 題：冪等矩陣與投影空間

P =
\\[
\begin{bmatrix}
1 & 0\\
0 & 0
\end{bmatrix}
\\]

**(1) 驗證冪等：**

\\[
P^2 =
\begin{bmatrix}
1 & 0\\
0 & 0
\end{bmatrix}
\begin{bmatrix}
1 & 0\\
0 & 0
\end{bmatrix}
=
\begin{bmatrix}
1 & 0\\
0 & 0
\end{bmatrix}
= P
\\]

**(2) 投影空間說明：**

任意向量 \\(x = [x_1, x_2]^T\\) 經 P 映射：

\\[
Px =
\begin{bmatrix}
1 & 0\\
0 & 0
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}
=
\begin{bmatrix}
x_1\\0
\end{bmatrix}
\\]

可見 P 將所有向量投影到 x 軸方向（span([1,0]^T)）  
→ 投影空間 = x 軸。

---

### 第 40 題：向量的正交投影

子空間：\\(W = \text{Span}([1,2]^T)\\)  
向量：\\(b = [3,4]^T\\)

正交投影公式：

\\[
\text{proj}_W(b) =
\frac{v^T b}{v^T v} v,
\quad v = \begin{bmatrix}1\\2\end{bmatrix}
\\]

計算：
\\[
v^T b = 1\cdot3 + 2\cdot4 = 3 + 8 = 11
\\]
\\[
v^T v = 1^2 + 2^2 = 1 + 4 = 5
\\]
\\[
\Rightarrow
\text{proj}_W(b)
= \frac{11}{5}
\begin{bmatrix}1\\2\end{bmatrix}
=
\begin{bmatrix}
11/5\\22/5
\end{bmatrix}
\\]

**Python 驗算：**
```python
import numpy as np
v = np.array([1,2])
b = np.array([3,4])
proj = (v @ b) / (v @ v) * v
proj
```

---

如需把「前 1–20 題矩陣運算 + 本檔 21–40 題進階題」整合成一份大題庫、或轉成 PDF / PPTX，我可以再幫你自動產出。
