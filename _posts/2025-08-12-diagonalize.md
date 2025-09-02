---
layout: post

title: Linear Algebra, 행렬의 대각화(Diagonalization)

tags: [Linear Algebra, CSE, Data Science, AI, 한국어]

feature-img: "assets/img/0.post/linear/strang.jpg"

thumbnail: "assets/img/0.post/linear/strang.jpg"

categories: CSE, AI
---

## 행렬의 대각화(Diagonalization)

이미 언급했듯이 앞부분의 개념들은 이 다음부분을 이해하기 위한 초석이다. <br>

이제부터 나오는 새로운 개념들을 위해하기 위해서는 더욱 앞부분의 행렬, 고유치, 그리고 공간 등의 개념들이 더 중요해진다. <br>

원서 : **Strang, G. (2023). *Introduction to Linear Algebra* (6th ed.).** <br>

<br>

#### 1. 행렬의 대각화(Diagonalization)

정방행렬 A에 대하여 **P−1AP**가 **대각행렬**(대각원소를 제외한 원소는 모두 0인 행렬)로 되는 가역행렬 P가 존재하면 <br>“행렬 A는 **대각화 가능**하다”라고 하고, “행렬 P는 A를 **대각화**한다”라고 한다 <br>

다음의 형식을 기억하자.

$$
C=P^{−1}AP
$$

<br>

<br>

#### 2. 닮은 행렬 (Similar matrices)

A와 C가 같은 크기의 정사각행렬일 때, 다음을 만족시키는 가역행렬 P가 존재하면, A와 C는 서로 **닮음행렬**이라고 한다. <br>

$$
C=P^{−1}AP
$$

서로 닮음인 행렬의 다음과 같은 성질들은 서로 일치한다. <br>이러한 성질을 **닮음 불변량(similarity invariant)** 이라고 한다<br>

① 계수(rank) <br>

② 행렬식(determinant) <br>

③ 가역성 (invertible) <br>

④ 대각합 (sum of diagonal elements) <br>

⑤ 고유치 & 대수적중복도와 기하적중복도 <br>

⑥ dim(ketnel) = nullity (핵의 차원) <br>

⑦ 고유다항식 (eigen polynomial) <br>

⑧ 최소다항식 (least polynomial) <br>

여기서 마지막 **최소다항식**은 처음나오는 개념인데 후에 **Jordan canonical form**과 같이 언급하지 이름만 기억하자. <br>

추가로 **닮은 행렬**이 위 **8가지 성질**을 만족하다는 것이지, 8가지 성질을 만족한다고 닮은 행렬은 **아니다**, (즉, 역은 성립하지 않는다) <br>

위 명제의 대우는 "**8개 성질중에서 하나라도 거짓이면 닮음이 아니다**"<br>

<br>

#### 3. 닮은 대각행렬 (Similar diagonal matrix)

다음 형식을 만족하는 **가역행렬 P**가 A의 **고유벡터(eigen value)** 로 이루어진 행렬일때, <br>

C는 **닮은 대각행렬**이다.

$$
C=P^{−1}AP
$$

이때 C는 닮은행렬의 성질을 A와 공유하고 형태가 대각행렬(대각원소는 A의 고유치)이 된다.

<br>

<br>

#### 4. 행렬을 대각화하는 방법

- **단계1.** A의 n개의 일차독립 고유벡터 v1​,v2​,…,vn​을 구한다. <br>
  
- **단계2.** v1​,v2​,…,vn​을 그 열벡터로 하는 행렬 P를 구성한다. <br>
  
- **단계3.** 이 경우 행렬 P−1AP는 연속 대각성분으로써 λ1​,λ2​,…,λn​을 갖는 대각행렬이 될 것이다. <br>
  

여기서 λi​는 vi​(i=1,2,…,n)에 대응하는 고유치이다. <br>

크게 어려울거 없이 고유치를 구하면 자연스럽게 대각화도 시킬 수 있다.

<br>

예시와 함께 대각화를 시켜보자.<br>

<br>

다음 행렬 A를 대각화 시켜보자.

$$
A = \begin{bmatrix} 1 & 1 \\ -2 & 4 \end{bmatrix}
$$

A의 고유치, 고유벡터를 구한다.

$$
|A - \lambda I| 
= \begin{vmatrix} 1-\lambda & 1 \\ -2 & 4-\lambda \end{vmatrix} 
= \lambda^2 - 5\lambda + 6 = 0
$$

따라서 λ = 2,3이다.<br>

여기서 각 고유치의 고유벡터를 구하면 다음과 같다.

$$
\lambda = 2 \;\; \Rightarrow \;\; v_1 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, 
\quad
\lambda = 3 \;\; \Rightarrow \;\; v_2 = \begin{bmatrix} 1 \\ 2 \end{bmatrix}
$$

그리고 고유벡터들을 열로하는 행렬 P를 잡는다.

$$
P = \begin{bmatrix} 1 & 1 \\ 1 & 2 \end{bmatrix}, 
\quad
P^{-1} = \begin{bmatrix} 2 & -1 \\ -1 & 1 \end{bmatrix}
$$

마지막으로 대각행렬 P-1AP는 대각성분들을 A의 고유치로 갖는다

$$
P^{-1} A P 
= \begin{bmatrix} 2 & -1 \\ -1 & 1 \end{bmatrix}
\begin{bmatrix} 1 & 1 \\ -2 & 4 \end{bmatrix}
\begin{bmatrix} 1 & 1 \\ 1 & 2 \end{bmatrix}
= \begin{bmatrix} 2 & 0 \\ 0 & 3 \end{bmatrix}
$$

<br>

과정을 보다 싶이 그냥 고유치 구하는 과정과 같고, 특성다항식 빨리 구하는 공식을 알면 더 쉽게 풀 수 있다. <br>

<br>

**Theorem** <br>

A가 nxn행렬이면 다음은 동치이다. <br>

① A는 대각화 가능하다. <br>

② A는 n개의 일차독립 고유벡터를 갖는다. <br>

③ 고윳값의 대수적 중복도와 기하적 중복도가 같다.

<br>

**참고**<br>

n차 정방행렬 A의 **서로 다른 고유치의 개수가 n개**이면 A의 일차독립인 고유벡터의 개수는 항상 **n개** 존재한다. <br>

따라서 n차 정방행렬 A의 서로 다른 고유치의 개수가 n개이면 n차 정방행렬 A가 대각화 가능이 된다. <br>하지만 **n차 정방행렬 A가 대각화 가능**하면 n차 정방행렬 A가 서로 다른 고유치의 개수가 **n개**라는 것은 **아니다**. <br>만약, 고유치가 **중근을 갖는 경우**에는 **일차독립인 고유벡터의 개수**에 따라 대각화의 가능성이 결정된다. <br>

또한 n차 정방행렬 A가 **대칭행렬**이면 **항상 (직교) 대각화 가능**하다. <br>그리고 A가 **가역**행렬인 것과 **대각화** 가능의 여부는 서로 **무관**하다. <br>

<br>

여기서 **직교대각화(Orthogonal Diagonalization)** 로 넘어가기 전에 **행렬의 멱승**에 관해 짚고 넘어가자.

<br>

<br>

#### 5. 행렬의 멱승 (Power of matrix)

A가 nxn행렬(정방행렬)이고, P가 가역(정칙)행렬이면 다음이 성립한다. <br>

$$
(P^{-1}AP)^2 = (P^{-1}AP)(P^{-1}AP) = P^{-1}A^2P
$$

일반적으로 임의의 양의 정수 k에 대해서 다음이 성립한다.

$$
(P^{-1}AP)^k = P^{-1}A^kP
$$

이 방정식으로 부터 A가 대각화가능하고 P-1AP가 대각행렬이면, 다음이 성립한다.

$$
D^k = (P^{-1}AP)^k = P^{-1}A^kP
$$

이러면 D의 k승은 쉽게 계산할 수 있다. <br>

<br>

행렬 A의 n승을 계산하는 방법은 크게 **3가지**로 나뉜다.

$$
A^n
$$

① element pattern (곱해서 패턴찾기) <br>

② Cayley-Hamilton Theorem <br>

③ diagonalization <br>

여기서 3번째 방법이 방금 언급한 방법이다. <br>

그리고 2번째 **cayley - hamilton** 방법을 정리해 보자. <br>

첫번째는 그냥 단순 노가다라 따로 언급안하고 넘어간다. <bR>

<br>

#### 6. Cayley-Hamilton Theorem

이름은 어려워보이지만 그냥 수학자 이름이다. <br>

쉽게 설명하면 행렬 A의 고유방정식 A - λI = 0 에 행렬 A 를 대입해도 식이 성립한다는 것이다. <br>

예시를 보면 훨씬 쉬우니 예제를 풀어보자.

<br>

##### 문제 1

행렬 A가 다음과 같을때 A^5 - 2A^3 + 2A - I의 대각 성분의 합은?

$$
\begin{bmatrix}
-1 & 0 & 0 & 0 \\
1 & -1 & 0 & 0 \\
4 & 1 & 1 & 0 \\
0 & 1 & 5 & 1
\end{bmatrix}
$$

<br>

이걸 어케 풀어 싶겠지만 cayley-hamilton을 쓰면 굉장히 쉽다. <br>

행렬 A는 상삼각행렬이기때문에 고유치 특성에 따라 고유치는 -1, -1, 1, 1 이다.<br>

따라서 특성다항식은 (λ - 1)^2(λ+1)^2가 나오고 이를 전개하면 합차의 제곱이므로 다음과 같이 나온다.

$$
λ^4 - 2λ^2 +1
$$

그리고 케일리해밀턴 정리에 따라 다음과 같이 전개할수 있다.

$$
A^4 - 2A^2 +1=0
$$

$$
A^5 - 2A^3+2A -I= (A^4 - 2A^2 +1)A + A - I = A-I
$$

따라서 A의 고유치에 1씩 빼고 합하면 -4가 나온다.<br>

<br>

그럼 이제 다른 유형의 멱승문제를 풀어보자.<br>

<br>

##### 문제 2

다음을 만족하는 두 실수 a, b를 찾아서 log2a/log2b를 구하여라.

$$
\left( \begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}^{100} 
\begin{bmatrix} 4 \\ 0 \end{bmatrix} \right)
= a \begin{bmatrix} -1 \\ -1 \end{bmatrix} 
+ b \begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

<br>

이것도 행렬의 멱승 많이 나오는 유형중 하나이다. <br>

고유벡터에 고유치를 대응하는 방법을 기억하자.

우선 대칭행렬에 행의 합이 같으므로 고유치 4를 바로 알수 있고 이어서 trA를 통해 고유치가 2,4라는 것은 바로 알 수 있다. <br>

① λ = 2

$$
\begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix} 
\begin{bmatrix} x \\ y \end{bmatrix} = 
\begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

이므로 고유벡터는 (1 -1)의 전치이다. 따라서 다음을 만족한다.

$$
\begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}
\begin{bmatrix} 1 \\ -1 \end{bmatrix}
= 2 \begin{bmatrix} 1 \\ -1 \end{bmatrix}
$$

② λ = 4

$$
\begin{bmatrix} -1 & 1 \\ -1 & -1 \end{bmatrix} 
\begin{bmatrix} x \\ y \end{bmatrix} =
\begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

이므로 고유벡터는 다음과 같다.

$$
\begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

따라서

$$
\begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}
\begin{bmatrix} 1 \\ 1 \end{bmatrix}
= 4 \begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

즉 문제는 고유벡터로 분해한 것이다. <br>

$$
\begin{bmatrix} 4 \\ 0 \end{bmatrix}
= 2 \begin{bmatrix} 1 \\ -1 \end{bmatrix}
+ 2 \begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

$$
\begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}^{100}
\begin{bmatrix} 4 \\ 0 \end{bmatrix}
=
\begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}^{100}
\left(2 \begin{bmatrix} 1 \\ -1 \end{bmatrix}
+ 2 \begin{bmatrix} 1 \\ 1 \end{bmatrix}\right)
$$

$$
= 2 \begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}^{100} 
\begin{bmatrix} 1 \\ -1 \end{bmatrix}
+ 2 \begin{bmatrix} 3 & 1 \\ 1 & 3 \end{bmatrix}^{100} 
\begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

$$
= 2 \cdot 2^{100} \begin{bmatrix} 1 \\ -1 \end{bmatrix}
+ 2 \cdot 4^{100} \begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

$$
= 2^{101} \begin{bmatrix} 1 \\ -1 \end{bmatrix}
+ 2^{201} \begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

따라서 다음과 같이 답을 구할 수 있다.

$$
a = 2^{101}, \; b = 2^{201}
$$

$$
\frac{\log_2 a}{\log_2 b}
= \frac{\log_2 2^{101}}{\log_2 2^{201}}
= \frac{101}{201}
$$