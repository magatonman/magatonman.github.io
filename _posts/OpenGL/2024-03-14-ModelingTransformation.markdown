---
title:  "Modeling Transformation"
excerpt: "Tensor"
last_modified_at: 2024-03-14
categories:
  - OpenGL
tags:
  - OpenGL
---
# 렌더링 파이프라이닝
일반적으로, 렌더링은 모델링 변환→Trivial Rejection→광원(Illumination)→Viewing Transformation→클리핑→Projection→래스터화→디스플레이의 과정을 거친다.

* Trivial Rejection 과정은 현재 화면과 시점의 위치 상, 보일 수 없는 물체들을 쳐낸다.
* Illumination은 빛을 계산해 눈에 보이는 색상을 표현한다.
* Viewing Transformation 단계에서는 World space를 Eye space로 이동한다. ($\dot{e}^t=\dot{w}^tV$)
* 클리핑 과정에서 현 카메라 위치에서 잘리는 부분을 없애고, 프로젝트 과정에서 2차원 공간에 3차원 이미지를 투영한다.
* 래스터화 과정에서는 3D를 픽셀로 환산한다.

# Translation
나중에
# 3D 회전
2D 회전과 다르게 회전축까지 함께 회전한다.
# 텐서곱
두 벡터 $\vec{a}=\begin{bmatrix}
a_x \\
a_y \\
a_z \\
0 
\end{bmatrix}$, $\vec{b}=\begin{bmatrix}
b_x \\
b_y \\
b_z \\
0 
\end{bmatrix}$에 대해 두 벡터의 텐서곱은 $\vec{a}=\begin{bmatrix}
a_xb_x & a_xb_y & a_xb_z & 0 \\
a_yb_x & a_yb_y & a_yb_z & 0 \\
a_zb_x & a_zb_y & a_zb_z & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}$이 된다.

# 아핀 변환 버전
