---
title:  "Color Vector"
excerpt: "색상 표시법"
last_modified_at: 2024-09-10
categories:
  - Vision
tags:
  - Vision
---

# 원추 세포의 분포
가시광선의 파장 범위는 380nm~770nm으로, 인간의 눈은 상기한 범위 내부의 빛만을 감별할 수 있다. 빛의 색상을 구별하는 세포가 원추 세포로, 3종류인 L(Long), M(Middle), S(Short)로 나뉘며 각각 적색, 녹색, 청색을 감지한다. 신체에서 각 원추 세포의 비율은 약 40:20:1이다.

3가지 원추 세포에 대해, 각 세포가 특정 파장 λ에 대해 얼마나 민감하게 반응하는지를 함수의 $k(\lambda)$로 나타내자. 이 경우, 단색광에 대한 망막의 반응은
$\begin{bmatrix}
k_l(\lambda) \\
k_m(\lambda) \\
k_s(\lambda) 
\end{bmatrix}$
와 같은 행렬의 형태로 표기할 수 있다.

여러 파장의 광선이 혼합된 혼합 광선 $l(\lambda)$의 경우,
$\begin{bmatrix}
\int_{\Omega}l(\lambda)k_l(\lambda)d\lambda \\
\int_{\Omega}l(\lambda)k_m(\lambda)d\lambda \\
\int_{\Omega}l(\lambda)k_s(\lambda)d\lambda 
\end{bmatrix}$
로 나타낼 수 있다. 여기서 $\Omega$는 가시광선의 파장 범위 전체, 즉 380nm~770nm을 의미하며, 즉 반응의 정도는 전 가시광선 구간에서 혼합 광선의 파장마다 얼마나 반응하는지로 따질 수 있다.

# 컬러 매칭 실험
국제 조명 위원회( Commission internationale de l'éclairage)에서 1931년에 시행한 시험으로, 피험자에게 목표 색상과 에게 적색(700nm), 녹색(546.1nm), 청색(435.8nm)의 삼원색의 세기를 조절할 수 있게 하여 목표 색상과 동일한 색상을 만들게 한 실험이다.


그런데 어떠한 색은 아무리 조절해도 만들어 낼 수 없었다. 이를 해결하기 위한 궁여지책으로, 적색광을 만드는 색이 아니라 제시된 색에 비추는 식으로 색을 맞추어도 색을 만든 것으로 인정해 주었다. 이러한 이유로, 강도가 음수일 수도 있다.
# CIEXYZ 표색계

각 축을 

이후, 이 $X, Y, Z$값을 정규화하면 

, 3개의 값은 항상 0 이상이 된다. 이 때, 이 표색계에서 $Y$값은 빛의 밝기만을 나타내도록 지정된 값으로, 색상과는 관련이 없다.

최종적으로, RGB 색상값을 CIXYZ 표색계로 옮기기 위해서는 이하의 선형변환을 거친다.

$\begin{bmatrix}
X \\
Y \\
Z \end{bmatrix}=\frac{1}{0.17697}\begin{bmatrix}
0.49 & 0.31 & 0.20 \\
0.17697 & 0.81240 & 0.01063 \\
0 & 0.01 & 0.99 \\
\end{bmatrix}\begin{bmatrix}
R \\
G \\
B\end{bmatrix}$

이후 이 값을 정규화한다. 과정은 이하와 같다.
$x=\frac{X}{X+Y+Z}, y=\frac{Y}{X+Y+Z}, z=\frac{Z}{X+Y+Z}$

그렇게 되면, $z=1-(x+y)$가 되어 $z$ 값은 생략 가능하기 때문에 적색과 녹색의 비율을 각각 x축과 y축으로 하는 좌표평면에 색을 투사할 수 있게 된다.



# CIEXYZ 