---
layout: post

title: Linear Algebra, 표현행렬

tags: [Linear Algebra, CSE, Data Science, AI]

feature-img: "assets/img/0.post/linear/strang.jpg"

thumbnail: "assets/img/0.post/linear/strang.jpg"

categories: CSE, AI, LinearAlgebra
---
## The matrix representation of a linear transformation

<br>

앞부분의 선형변환은 벡터를 다른 벡터로 보내는 규칙이였지만, <br>

지금부터 나오는 **선형변환** 은 꼭 좌표평면 벡터에만 적용하는 것이 아닌, **다항식공간** 같은 추상적인 벡터 공간에서도 정의할수 있다. <br>

이게 중요한 이유는 **미분(differentiation)** 같은 추상적 연산도 **행렬 곱** 으로 다룰 수 있다. <br>

개인적으로 지금부터 나올 **표현행렬(matrix representation)** 과 **추이행렬(기저변환행렬, change-of-basis matrix)** 이 진정한 선형대수의 꽃이라고 생각한다.<br>

<br>

#### 1. 표현행렬 (matrix representation)

모든 선형변환은 행렬로 표현할 수 있고 그 역도 성립한다. 즉, **행렬은 선형변환과 같다**.  
이는 선형대수학의 **기본정리** 라고 한다. <br>

선형변환의 표현행렬은 두 벡터 공간 V, W의 차원이 유한할 때, <br>선형변환 T : V → W를 나타내는 행렬이다. 표현행렬은 정의역과 공역의 기저의 선택에 따라 달라질 수 있으며, <br>정의역과 공역이 같은 선형변환 T : V → V일 임의의 기저에 대한 표현행렬은 모두 **닮음**이다.

선형변환의 표현행렬을 구하는 한 예를 살펴보자. <br>

다음 v에서

$$
v = (2,3) = \frac{1}{2}(1,2) + \frac{1}{2}(3,4)
$$

β = {(1,1), (1,0)}에 대하여 다음과 같이 쓸 수 있다. <br>

$$
u = (2,3) = 3(1,-1) - 1(1,0)\ 이고 \ [u]_{β} = (3,-1) 이다. \\
v = (1,-1) = 2(1,1) - 1(1,0)\ 이고 \ [v]_{β} = (2,-1) 이다. \\
w = (3,4) = 4(1,1) - 1(1,0)\ 이고 \ [w]_{β} = (4,-1) 이다.
$$

이때 다음과 같이 쓸 수 있다.

$$
[v]_\beta = [(2,3)]_\beta 
= \left[ \tfrac{1}{2}(1,2) + \tfrac{1}{2}(3,4) \right]_\beta
$$

$$
= \tfrac{1}{2}[(1,2)]_\beta + \tfrac{1}{2}[(3,4)]_\beta
$$

$$
= \tfrac{1}{2}(2,-1) + \tfrac{1}{2}(4,-1)
$$

$$
= (1,-\tfrac{1}{2}) + (2,-\tfrac{1}{2}) = (3,-1)
$$

따라서 다음이 성립함을 기억하자. (이것이 표현행렬을 만드는 원리이다.)

$$
\left[ \tfrac{1}{2}(1,2) + \tfrac{1}{2}(3,4) \right]_\beta
= \tfrac{1}{2}[(1,2)]_\beta + \tfrac{1}{2}[(3,4)]_\beta
$$

<br>

<br>

이제 본격적으로 일반화를 시켜보자. <br>

수식이 매우 복잡하지만, 다음과 같은 흐름으로 보면 이해하기 편하다. <br>

① 정의역의 기저 v를 선형변환 T에 넣는다 <br>

② T(v)를 치역의 기저 u로 쪼갠다 <br>

③ 그리고 이를 열로 세운다. <br>

<br>

이제 선형변환 T : V -> W에서 V, W의 각각의 순서기저를

$$
\alpha = \{ v_1, v_2, \cdots, v_n \}, \quad
\beta = \{ w_1, w_2, \cdots, w_m \} \text{라 하자.}
$$

$$
T(v_1) = a_{11} w_1 + a_{21} w_2 + \cdots + a_{m1} w_m
\;\;\Rightarrow\;\;
[T(v_1)]_\beta = (a_{11}, a_{21}, \cdots, a_{m1})^T
$$

$$
T(v_2) = a_{12} w_1 + a_{22} w_2 + \cdots + a_{m2} w_m
\;\;\Rightarrow\;\;
[T(v_2)]_\beta = (a_{12}, a_{22}, \cdots, a_{m2})^T
$$

$$
\vdots
$$

$$
T(v_n) = a_{1n} w_1 + a_{2n} w_2 + \cdots + a_{mn} w_m
\;\;\Rightarrow\;\;
[T(v_n)]_\beta = (a_{1n}, a_{2n}, \cdots, a_{mn})^T
$$

이때,

$$
X \in V \text{에 대하여 } X = x_1 v_1 + x_2 v_2 + \cdots + x_n v_n \text{이고,}
$$

$$
T(X) = T(x_1 v_1 + x_2 v_2 + \cdots + x_n v_n)
= x_1 T(v_1) + x_2 T(v_2) + \cdots + x_n T(v_n)
$$

(∵ \(T\)는 선형변환)

$$
[T(X)]_\beta = x_1 [T(v_1)]_\beta + x_2 [T(v_2)]_\beta + \cdots + x_n [T(v_n)]_\beta
$$

$$
= \begin{bmatrix} [T(v_1)]_\beta & [T(v_2)]_\beta & \cdots & [T(v_n)]_\beta \end{bmatrix}
\begin{bmatrix}
x_1 \\ x_2 \\ \vdots \\ x_n
\end{bmatrix}
$$

따라서 선형변환 T의 표현행렬 A는 다음과 같다.

$$
T^\beta_\alpha = A 
= \big[ [T(v_1)]_\beta, [T(v_2)]_\beta, \cdots, [T(v_n)]_\beta \big]
= \begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
$$

사실 수식으로 보면 이해하기 더 어렵고, 예제를 풀어보는게 훨씬 이해하기 쉽다. <br>

그리고 처음풀때는 부동산계약서처럼 아무것도 안보이는게 정상이다.<br>

<br>

##### 문제1

차수가 2보다 작거나 같은 다항식들의 벡터공간 P2에 대하여 P2에서 P2로의 선형사상 T를

T(f) = f' + f'' 이라 하자. <br>

P2의 기저 B = {1, x, x^2}에 대한 T의 행렬표현을 A라 할 때,

A의 모든 성분들의 합은? <br>

<br>

<br>

처음봤을때 어쩌라는건지 모르는게 정상이다. <br>

하지만 익숙해지면 이정도 수준은 갖고 놀정도가 되니 걱정말자.<br>

위에 언급했던 흐름대로 풀어보자. <br>

① 정의역의 기저 v를 선형변환 T에 넣는다 <br>

② T(v)를 치역의 기저 u로 쪼갠다 <br>

여기서 P2 -> P2이므로 기저는 동일하다.

$$
T(1) = 0 = 0 \times 1 + 0 \times x + 0 \times x^2
$$

$$
T(x) = 1 = 1 \times 1 + 0 \times x + 0 \times x^2
$$

$$
T(x^2) = 2x + 2 = 2 \times 1 + 2 \times x + 0 \times x^2
$$

③ 그리고 이를 열로 세운다

$$
A =
\begin{bmatrix}
0 & 1 & 2 \\
0 & 0 & 2 \\
0 & 0 & 0
\end{bmatrix}
$$

이러면 표현행렬 A를 구한것이고 이를 다 더하면 5이다. <br>

이 방법말고도 그냥 대입해서 빨리 푸는 방법도 있지만 위과정을 기억하자.

$$
B = \{ 1, x, x^2 \} \text{ 은 표준기저이므로}
$$

$$
T(a + bx + cx^2) = b + 2cx + 2c = (b+2c) + (2c)x + (0)x^2 \text{일 때,}
$$

$$
A \begin{bmatrix} a \\ b \\ c \end{bmatrix}
= 
\begin{bmatrix}
0 & 1 & 2 \\
0 & 0 & 2 \\
0 & 0 & 0
\end{bmatrix}
\begin{bmatrix} a \\ b \\ c \end{bmatrix}
$$

이다. 따라서

$$
A = 
\begin{bmatrix}
0 & 1 & 2 \\
0 & 0 & 2 \\
0 & 0 & 0
\end{bmatrix},
\quad
\text{그리고 모든 성분들의 합은 } 5 \text{이다.}
$$