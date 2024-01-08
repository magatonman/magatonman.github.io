---
title:  "Karatsuba Multiplication"
excerpt: "수가 커질수록 곱셈에 걸리는 시간도 증가한다. 최적화할 수 있는 방법이 있을까...?"
last_modified_at: 2024-01-08
categories:
  - Algorithm
tags:
  - Algorithm
---
# Definition
분할 정복법을 이용하는 대표적인 알고리즘의 예시로, 큰 수의 곱셉을 좀 더 빠른 시간 안에 수행할 수 있도록 하는 알고리즘이다.

# Before?
엄밀히 말하면 두 $n$비트 수 $X$(피승수)와 $Y$(승수)의 곱셈은 $X$를 $Y$번 더하는 것이므로, 이 방법을 그대로 적용할 경우 시간 복잡도는 $O(2^n)$이 된다.

딱 봐도 극히 비효율적인 계산법이기 때문에, 좀 더 효율적인 방법을 쓰는 것이 낫고, 실제로도 여러 방법이 있다.

대표적인 방법으로, 세로셈을 이용해 시간복잡도를 완화하는 방법이 있다.

![세로셈](https://github.com/magatonman/magatonman.github.io/assets/47918242/eaac3474-0a5d-49cd-8189-db8e1307764e)


이 경우 각 덧셈 과정의 시간복잡도는 $O(n)$이고 $n$비트의 수에 대해서 이 반복 연산은 최대 $n$번 이루어지므로($X=2^n-1$인 경우) 시간복잡도는 $O(n^2)$가 된다.

여기서 더 줄일 수 있다.

# After
Karatsuba 알고리즘은 두 수를 이하와 같이 분할한다. 

$$
\begin{aligned}
    X&=2^{n/2}A+B\\
    Y&=2^{n/2}C+D
\end{aligned}
$$

두 수를 곱한 결과는 이하의 식과 같다.

$$
\begin{aligned}
    XY=2^nAC+2^{n/2}(AD+BC)+BD
\end{aligned}
$$

이 식을 계산하는 과정에서, 상수들의 계산을 제외하고 계산되는 부분은 $AC, AD, BC, BD$의 계산이다. $XY$의 계산에 걸리는 시간을 $T(n)$이라 하면, 저 네 항의 계산은 각 항마다 시간이 $T(n/2)$만큼 걸리므로 $T(n)=4T(n/2)+cn$으로 다시 쓸 수 있다.

하지만 이 재귀식을 풀면 나오는 시간복잡도는 $O(n^2)$라서 기존과 동일하다.

$$
XY=(2^n-2^{n/2})AC+2^{n/2}(A+B)(C+D)+(1-2^{n/2})BD
$$

그래서 처음 나온 식을 다른 방법으로 묶는다면 이런 방법으로 묶을 수 있는데, 그 결과 기존의 곱셈 항 $AD, BC$가 $(A+B)(C+D)$로 합쳐져서 $T(n)=3T(n/2)+cn$이 된다. 이 식을 풀면 시간복잡도는 $O(n^{log_2^3})$이 된다.

# 출처
* A.Karatsuba and Yu.Ofman (1962), Multiplication of Many-Digital Numbers by Automatic Computers, 《Proceedings of the USSR Academy of Sciences》 145: 293–294.

* <https://www.cs.cmu.edu/~15451-f22/lectures/lec23-strassen.pdf>
