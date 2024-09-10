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
$[\begin{bmatrix}
k_l(\lambda) \\
k_m(\lambda) \\
k_s(\lambda) 
\end{bmatrix}]$
와 같은 행렬의 형태로 표기할 수 있다.