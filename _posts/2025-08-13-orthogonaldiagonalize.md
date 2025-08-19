---
layout: post

title: Linear Algebra, 직교 대각화(Orthogonal Diagonalize)

tags: [Linear Algebra, CSE, Data Science, AI, 한국어]

feature-img: "assets/img/0.post/linear/strang.jpg"

thumbnail: "assets/img/0.post/linear/strang.jpg"

categories: CSE, AI
---

## 직교 대각화(Orthogonal Diagonalize)

지난번 대각행렬에서 계속해서 조건이 추가된다고 생각하자.

#### 1. 직교대각화(Orthogonal Diagonalize)

C = P-1AP를 만족하는 가역행렬 P가 A의 **고유벡터(eigen vector)** 로 이루어진 행렬일때,<br>

C는 **닮은 대각행렬**이다. <br>

이때 특별히 P가 직교행렬이면 다음을 **직교대각화**라고한다

$$
C=P^{-1}AP = P^TAP
$$

여기서 앞서 언급한 대칭행렬의 고유벡터는 수직을 가진다는 성질을 기억하면 다음과 같은 정리를 유도할 수 있다.<br>

<br>

**Theorem** <br>

A가 nxn행렬이면 다음이 성립한다.<br>

① A는 직교 대각화 가능하다.

② A는 대칭행렬이다.

<br>

<br>

#### 2. 행렬을 직교 대각화하는 방법

- 단계1. 대칭행렬 A의 n개의 **일차독립 고유벡터 v1​,v2​,⋯,vn​**을 구한다. <br>
  
- 단계2. **Gram-Schmidt 직교화과정**을 적용하여 각 고유공간의 정규직교기저를 만든다.<br>
  
- 단계3. 단계2에서 만든 벡터 w1​,w2​,⋯,wn​을 그 **열벡터로 하는 행렬 P**를 구성한다.<br>
  
- 단계4. 이 경우 행렬 P−1AP=PTAP는 연속 대각성분으로서 λ1​,λ2​,⋯,λn​을 갖는 대각행렬이 될 것이다. <br>여기서 λi​는 wi​ (i=1,2,⋯,n)에 대응하는 고유치이다.<br>
  

<br>

예시와 함께 직교대각화를 시켜보자. <br>

<br>

다음 행렬 A를 직교대각화 시켜보자 <br>

$$
A =
\begin{pmatrix}
4 & 2 & 2 \\
2 & 4 & 2 \\
2 & 2 & 4
\end{pmatrix}
$$

의 고유치, 고유벡터를 구하면 고유치는 각각 λ=2,2,8 이라는 것을 알 수 있다 <br>

참고로 위 행렬도 행의 합이 모두 같으므로 고유치 중 1개는 8이고 Tr와 det를 이용해서 다른 고유치도 빠르게 구할 수 있다. <br>

또한 위와 같은 행렬의 고유치는 일반화 되어있는 공식이 있다.<br>

<br>

**참고**

$$
A =
\begin{pmatrix}
a & b & b \\
b & a & b \\
b & b & a
\end{pmatrix}
$$

다음과 같은 행렬의 고유치는 **a + 2b**, **a -b**, **a-b**이다. <br>

그리고 **대칭행렬**의 특징 중 **대수적중복도과 기하적중복도가 같음**을 기억하자. <br>

(즉, 중근의 개수와 차원의 개수가 같다)<br>

<br>

그리고 λ = 2에 대응하는 고유벡터를 구하면 다음과 같다

$$
v_1 = (-1, 1, 0), \quad v_2 = (-1, 0, 1)
$$

이것도 참고로 **대칭행렬**의 고유벡터끼리는 **수직(orthogonal)** 이기 때문에 내적이 0이 나옴을 기억하면 한개만 구하고 다른 한개는 내적이 0이나오는 벡터 아무거나 떠올리면 더 쉽고 빠르다.<br>

그리고 λ = 8에 대응하는 고유벡터는 다음과 같다.

$$
v_3 = (1, 1, 1)
$$

그리고 각각의 기저에 대해 Gram-Schmidt 직교화과정을 적용하자. <br>

직교화과정이 기억이 안나면 [Linear Algebra, 직교기저(Orthogonal basis) | Koder Wiki](https://koderwiki.github.io/cse,/ai/2025/08/09/ob.html)부분을 참고하자 <br>

그럼 다음과 같은 기저를 얻을수있다 (단순 계산과정이니 넘어가자)

$$
\left\{
\left(-\tfrac{1}{\sqrt{2}}, \tfrac{1}{\sqrt{2}}, 0\right), \;
\left(-\tfrac{1}{\sqrt{6}}, -\tfrac{1}{\sqrt{6}}, \tfrac{2}{\sqrt{6}}\right), \;
\left(\tfrac{1}{\sqrt{3}}, \tfrac{1}{\sqrt{3}}, \tfrac{1}{\sqrt{3}}\right)
\right\}
$$

따라서 대칭행렬 A는 직교행렬 P에 의하여 **직교대각화** 된다.

$$
P =
\begin{pmatrix}
-\tfrac{1}{\sqrt{2}} & -\tfrac{1}{\sqrt{6}} & \tfrac{1}{\sqrt{3}} \\
\tfrac{1}{\sqrt{2}} & -\tfrac{1}{\sqrt{6}} & \tfrac{1}{\sqrt{3}} \\
0 & \tfrac{2}{\sqrt{6}} & \tfrac{1}{\sqrt{3}}
\end{pmatrix}
$$
이해를 위해 그림을 참고하자
<img width="626" height="683" alt="image" src="https://github.com/user-attachments/assets/19982be3-e8c2-425d-8f30-87e07b2d4bfd" />

<br>

<br>

### 3. Eigen Value Decomposition(EVD, 고윳값 분해)

이 **고윳값 분해(EVD)** 는 **특이값분해(SVD)** 와 함께 **주성분분석(PCA)** 등 다양한 데이터 분석과 여러 분야에서 사용하니 꼭 숙지하고 넘어가자. <br>

그렇다고 어려운 것은 아니고 특이값 분해 또한 EVD와 비슷하게 풀 수 있으니 걱정하지 말자. <br>

이 **고윳값분해**는 **스펙트럼분해(Spectral Decompositon)** 와 거의 동일하다. <br>

스펙트럼분해는 **대칭행렬**과 **에르미트행렬**에 특화되어있는 EVD라고 생각하면 편하다. <br>

에르미트행렬과 유니터리 등 **복소행렬**과 **특이값분해**와 **QR분해** 등은 추후에 나오니 이름정도만 알고 넘어가자. <br>

<br>

행렬 A가 P=[u1,u2, ... un] 로 직교 대각화가 되는 대칭행렬이고, λ1, λ2, ..., λn 은 고유벡터 u1, u2, ..., un에 대한 고유값이라고 하자. <br>

여기서 일반적인 EVD에서는 단위길이일 필요없지만, **대칭행렬**과 같은 형태에는 **단위 고유벡터(det(u) = 1)** 를 사용한다

그럼 다음의 식을 얻는다.

$$
A = P D P^T 
= [u_1 \; u_2 \; \cdots \; u_n]
\begin{bmatrix}
\lambda_1 & 0 & \cdots & 0 \\
0 & \lambda_2 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & \lambda_n
\end{bmatrix}
\begin{bmatrix}
u_1^T \\
u_2^T \\
\vdots \\
u_n^T
\end{bmatrix}
$$$$
= [\lambda_1 u_1 \; \lambda_2 u_2 \; \cdots \; \lambda_n u_n]
\begin{bmatrix}
u_1^T \\
u_2^T \\
\vdots \\
u_n^T
\end{bmatrix}
= \lambda_1 u_1 u_1^T + \lambda_2 u_2 u_2^T + \cdots + \lambda_n u_n u_n^T
$$

이 공식을 A의 EVD(고유값 분해)라고 한다.<br>

<br>

이해를 위해 예제를 풀어보자. <br>

<br>

##### 문제1

3×3 행렬에 대해 다음의 등식이 성립한다.

$$
\begin{bmatrix}
1 & 2 & 3 \\
2 & 4 & 5 \\
3 & 5 & 6
\end{bmatrix}
=
a \begin{bmatrix} u_1 \\ u_2 \\ u_3 \end{bmatrix}
\begin{bmatrix} u_1 & u_2 & u_3 \end{bmatrix}
+ b \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix}
\begin{bmatrix} v_1 & v_2 & v_3 \end{bmatrix}
+ c \begin{bmatrix} w_1 \\ w_2 \\ w_3 \end{bmatrix}
\begin{bmatrix} w_1 & w_2 & w_3 \end{bmatrix}.
$$

이때,

$$
a(u_1^2 + u_2^2 + u_3^2)
+ b(v_1^2 + v_2^2 + v_3^2)
+ c(w_1^2 + w_2^2 + w_3^2)
$$

의 값을 구하시오. (단, \(T\) 는 transpose를 의미한다.) <br>

<br>

다음은 대칭행렬 A의 고유값 분해를 이용하면 된다. <br>

따라서 a, b, c는 A의 고유치 이다. <br>

또한 대칭행렬이므로 각 고유벡터는 단위고유벡터이므로 결국에는 **고유치의 합**문제가 되고 이는 Tr(A)에 해당한다. <br>

따라서 답은 11이다.

<br>

<br>

##### 문제2

$$
A =
\begin{bmatrix}
0 & 2 & -1 \\
2 & 3 & -2 \\
-1 & -2 & 0
\end{bmatrix}
$$

적당한 직교행렬 \(P\)에 대하여

$$
P^{-1}AP =
\begin{bmatrix}
-1 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 5
\end{bmatrix}
$$

를 만족한다. <br>
\(P\)의 열을 순서대로 \(u_1, u_2, u_3\)라 할 때,

$$
u_1 u_1^T + u_2 u_2^T
$$

을 구하시오.<br>

<br>

P-1AP는 대칭행렬 A의 직교대각화 이므로 P의 열은 고유치 -1 -1 5에 해당하는 **단위고유벡터**이다. <br>

대칭행렬 A의 스펙트럼분해를 이용하면

$$
A = -1 u_1 u_1^T - 1 u_2 u_2^T + 5 u_3 u_3^T 이다.
$$

즉,

$$
u_1 u_1^T + u_2 u_2^T = 5 u_3 u_3^T - A 이다.
$$

또한,

$$
A - 5I =
\begin{bmatrix}
-5 & 2 & -1 \\
2 & -2 & -2 \\
-1 & -2 & -5
\end{bmatrix}
$$

이고

$$
(-1, -2, -5) \times (2, -2, -2) = (-6, -12, 6) \parallel (1, 2, -1)
$$

이므로

$$
u_3 = \frac{1}{\sqrt{6}}
\begin{bmatrix}
1 \\ 2 \\ -1
\end{bmatrix}
이다.
$$

따라서

$$
5 u_3 u_3^T - A
= \frac{5}{6}
\begin{bmatrix}
1 \\ 2 \\ -1
\end{bmatrix}
(1,2,-1)
-
\begin{bmatrix}
0 & 2 & -1 \\
2 & 3 & -2 \\
-1 & -2 & 0
\end{bmatrix}
$$

$$
= \frac{5}{6}
\begin{bmatrix}
1 & 2 & -1 \\
2 & 4 & -2 \\
-1 & -2 & 1
\end{bmatrix}
-
\begin{bmatrix}
0 & 2 & -1 \\
2 & 3 & -2 \\
-1 & -2 & 0
\end{bmatrix}
$$

$$
= \frac{1}{6}
\begin{bmatrix}
5 & -2 & 1 \\
-2 & 2 & 2 \\
1 & 2 & 5
\end{bmatrix}

$$

<br>

<br>

#### 4. 지수행렬(Matrix Exponential)

**지수행렬(Matrix Exponential)** 은 스칼라 지수함수의 급수 정의를 행렬에 확장한 개념으로,<br>

**EVD**를 통해 단순해진다.<br>

우선 **지수함수**의 **M-급수(매클로린 급수, x = 0에 대한 Tayler 전개)** 에 대해 언급하고 넘어가자. 다음은 **지수함수의 M-급수**이다.

$$
e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots = \sum_{n=0}^{\infty} \frac{x^n}{n!}
$$

우리의 목표는 지수행렬의 determinant를 구하는 것이다.

$$
det(e^{At})
$$

지수함수의 M급수를 이용해 A에 대해 다음과 같이 쓸수있다.

$$
e^A = I + A + \frac{A^2}{2!} + \frac{A^3}{3!} + \cdots = \sum_{n=0}^{\infty} \frac{A^n}{n!}
$$

그럼 고윳값 분해를 통해 다음과 같이 전개할 수 있다. <br>

여기서 P-1AP는 A=P-1DP에서 P-1,P를 양변에 곱한것이다.

$$
P^{-1}AP = D = \begin{pmatrix} \lambda_1 & 0 \\ 0 & \lambda_2 \end{pmatrix}
$$

$$
e^{At} = P \begin{pmatrix} e^{\lambda_1 t} & 0 \\ 0 & e^{\lambda_2 t} \end{pmatrix} P^{-1}
$$

$$
|e^{At}| = e^{\lambda_1 t} \cdot e^{\lambda_2 t} = e^{(\lambda_1 + \lambda_2)t} = e^{\operatorname{tr}(A)t}
$$

$$
= \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}
+ \begin{pmatrix} \lambda_1 & 0 \\ 0 & \lambda_2 \end{pmatrix}
+ \frac{1}{2!}\begin{pmatrix} \lambda_1^2 & 0 \\ 0 & \lambda_2^2 \end{pmatrix} + \cdots
$$

$$
= \begin{pmatrix} 1 + \lambda_1 + \tfrac{1}{2!}\lambda_1^2 + \cdots & 0 \\ 0 & 1 + \lambda_2 + \tfrac{1}{2!}\lambda_2^2 + \cdots \end{pmatrix}
$$

$$
= \begin{pmatrix} e^{\lambda_1} & 0 \\ 0 & e^{\lambda_2} \end{pmatrix}
$$

고윳값분해를 통해 깔끔하게 구할수 있고 그럼 지수행렬의 determinant는 다음과 같이 구할 수있다.

$$
e^{At} = P 
\begin{pmatrix}
e^{\lambda_1 t} & 0 \\
0 & e^{\lambda_2 t}
\end{pmatrix}
P^{-1}
$$

$$
\det\!\left(e^{At}\right) 
= e^{\lambda_1 t} \cdot e^{\lambda_2 t} 
= e^{(\lambda_1 + \lambda_2)t} 
= e^{\operatorname{tr}(A)t}
$$

이해를 위해 문제를 풀어보자. <br>

<br>

##### 문제3

행렬

$$
A =
\begin{bmatrix}
1 & 2 & 6 & 9 \\
0 & 3 & 0 & 0 \\
0 & 4 & 7 & 0 \\
0 & 5 & 8 & 10
\end{bmatrix}
$$

에 대하여

$$
e^A = \lim_{n \to \infty} \left( I + A + \frac{1}{2!} A^2 + \cdots + \frac{1}{n!} A^n \right)
$$

으로 정의할 때,

$$
e^A \text{ 의 행렬식의 값은?}
$$

<br>

<br>

지수행렬의 대각화를 이용하면 쉽게 풀 수 있는데, 더 쉽게 풀기위해서 특성다항식 빠르게 푸는 과정을 알려주면 <br>

결국에는 주대각원소에 λ를 빼서 det를 구하는 것이기 때문에 저렇게 한행의 피봇만 0이 아닐때는<br>

Laplace전개를 쓰면 더 수월하게 구할수있다. 위 행렬의 경우에는 특히 소행렬식에서 계속해서 한행만 0이 아니기 때문에 특성다항식을 눈만있으면 구할 수 있다. <br>

그럼 특성다항식은 (1-λ)(3-λ)(7-λ)(10-λ) = 0 이고 고유값은 1 3 7 10이 나온다. <br>

또한 서로다른 4개의 고유값을 가지므로 full-rank여서 대각화가 가능하다. <br>

따라서 답은 e^tr(A)이므로 e^21이다.
