---
title:  "2D Geometric Transformation"
excerpt: "2D"
last_modified_at: 2024-03-10
categories:
  - OpenGL
tags:
  - OpenGL
---
# 이동
원 좌표에 이동 거리를 더하는 식으로 새로운 좌표를 구한다.
 $$x'=x+t_x\\y'=y+t_y$$

이동을 취소하기 위해서는 더한 값을 빼면 된다.
 $$x'=x-t_x\\y'=y-t_y$$

명령어로는
```glTranslate(tx, ty ,tz)```와 같은 형태로 이용한다.
# 회전 (2D)
어떤 객체를 $\theta$도 회전하고 싶다면,
$$x'=\cos\theta x-\sin\theta x\\
y'=\sin\theta x+\cos\theta x$$
의 형태로 새로운 좌표를 잡는다. 증명은 이하와 같다.
$$\begin{bmatrix} 
   x' \\
   y' \\
   \end{bmatrix}=
   \begin{bmatrix} 
   \cos\theta & -\sin\theta  \\
   \sin\theta & \cos\theta  \\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   \end{bmatrix} 
$$

거꾸로 회전하고 싶으면,
$$x'=\cos\theta x+\sin\theta x\\
y'=-\sin\theta x+\cos\theta x$$
를 이용한다.
이는
$$
   \begin{bmatrix} 
   \cos\theta & -\sin\theta  \\
   \sin\theta & \cos\theta  \\
   \end{bmatrix}^{-1}=\begin{bmatrix} 
   \cos\theta & \sin\theta  \\
   -\sin\theta & \cos\theta  \\
   \end{bmatrix}
$$

임에 기인한다.
명령어로는 ```glRotate(Degree, axisX, axisY ,axisZ)```로 표기한다. 이 때 각도는 degree로 표기하며, 우측의 좌표는 기준점이다.
# 일반화
두 동작을 합친다면,
$$x'=\cos\theta x+\sin\theta x+t_x\\
y'=-\sin\theta x+\cos\theta x+t_y$$

가 된다. 하지만 이 경우 역순 처리를 할 경우 2회에 걸친 계산이 필요하다.

# 2D의 3D화
존재하지 않는 가상의 z축 한 개를 생성하면, 이동, 회전 등 여려 유클리드 변환을 한 개의 행렬 곱셈으로 처리할 수 있다.
$$\begin{bmatrix} 
   x' \\
   y' \\
   1 \\
   \end{bmatrix}=
   \begin{bmatrix} 
   \cos\theta & -\sin\theta &t_x \\
   \sin\theta & \cos\theta &t_y \\
   0 & 0 & 1\\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   1\\
   \end{bmatrix} 
$$

# 크기 수정
어떤 도형의 크기를 $s$배 하고 싶다면, 이하의 행렬을 곱한다.
$$\begin{bmatrix} 
   x' \\
   y' \\
   1 \\
   \end{bmatrix}=
   \begin{bmatrix} 
   s & 0 & 0 \\
   0 & s & 0 \\
   0 & 0 & 1\\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   1\\
   \end{bmatrix} 
$$

코드로는 ```glScale(sx, sy, sz)```로 나타낸다.
# 기울임
x축을 기준으로 45도 기울이면 이하와 같다.
$$\begin{bmatrix} 
   x' \\
   y' \\
   1 \\
   \end{bmatrix}=
   \begin{bmatrix} 
   1 & 1 & 0 \\
   0 & 1 & 0 \\
   0 & 0 & 1\\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   1\\
   \end{bmatrix} 
$$
y축의 경우
$$\begin{bmatrix} 
   x' \\
   y' \\
   1 \\
   \end{bmatrix}=
   \begin{bmatrix} 
   1 & 0 & 0 \\
   1 & 1 & 0 \\
   0 & 0 & 1\\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   1\\
   \end{bmatrix} 
$$
# 반전
x축을 기준으로 뒤집으면 이하와 같다. 포토샵이나 한글과 다르게 진짜 x축, 즉 $y=0$을 기준으로 뒤집기 때문에 위치가 변경된다.
$$\begin{bmatrix} 
   x' \\
   y' \\
   1 \\
   \end{bmatrix}=
   \begin{bmatrix} 
   1 & 0 & 0 \\
   0 & -1 & 0 \\
   0 & 0 & 1\\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   1\\
   \end{bmatrix} 
$$
y축을 기준으로 뒤집는다면
$$\begin{bmatrix} 
   x' \\
   y' \\
   1 \\
   \end{bmatrix}=
   \begin{bmatrix} 
   -1 & 0 & 0 \\
   0 & 1 & 0 \\
   0 & 0 & 1\\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   1\\
   \end{bmatrix} 
$$
# 아핀 변환
기존까지의 이동, 회전, 크기, 반전, 기울임을 일반화한 형태.
$$\begin{bmatrix} 
   x' \\
   y' \\
   1 \\
   \end{bmatrix}=
   \begin{bmatrix} 
   a_{11}& a_{12} &a_{13} \\
   a_{21} & a_{22} &a_{23} \\
   0 & 0 & 1\\
   \end{bmatrix} \begin{bmatrix} 
   x \\
   y \\
   1\\
   \end{bmatrix} 
$$
