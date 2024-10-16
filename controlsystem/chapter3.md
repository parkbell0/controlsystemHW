#**제어공학 HW Chapter.3**
#**2021732082_박종영**  
###P3.1,  P3.3, P3.5, P3.12, P3.17

# P3.1

## (a) **state variables.**

Spring Mass Damper System의 경우, 2차 미분 방정식이므로 2개의 state를 정의하면 다음과 같다.
### **Answer**
$$
x_1(t) = 위치 y_(t)
$$
$$  
x_2(t) = 속도 V(t) = \frac{dy(t)}{dt}
$$

## (b) **first-order differential equations in terms of the state variables**

Newton's law에 의하여 외력 = 질량가속도 + 댐퍼힘 + 스프링힘으로 정의할수 있다.

$$
외력 = F(t) 
$$
$$ 
질량 가속도 = M\frac{d^2 y(t)}{dt^2}
$$
$$
댐퍼 힘 = bV(t) = b\frac{dy(t)}{dt}
$$
$$
스프링 힘 = ky(t)
$$

이를 외력에 대한 식으로 정리하면 다음과 같다.

$$
F(t) = M\frac{d^2 y(t)}{dt^2} + b\frac{dy(t)}{dt} + ky(t)
$$


a)에서 정의한 state 변수를 위 식에 대입하여 두 개의 일차 미분방정식으로 정리할 수 있다.

### **Answer**  
  $$
  \frac{dx_1(t)}{dt} = x_2(t)
  $$

  $$
  \frac{dx_2(t)}{dt} = -\frac{k}{M}x_1(t) - \frac{b}{M}x_2(t) + \frac{1}{M}F(t)
  $$

## (c) **state differential equation.**
외력인 F(t)를 입력신호 u(t)로 본다면 다음과 같은 differential equation으로 나타낼수 있다.

### **Answer** 
\begin{align*}
\text{C)} \quad &\left\{
\begin{array}{l}
\dot{x}_1(t) = x_2(t) \\
\dot{x}_2(t) = \frac{k}{M}x_1(t) - \frac{b}{M}x_2(t) + \frac{1}{M}F(t)
\end{array}
\right. \\
&\Rightarrow \dot{x}(t) = 
\begin{pmatrix}
0 & 1 \\
\frac{k}{M} & -\frac{b}{M}
\end{pmatrix}
x(t) + 
\begin{pmatrix}
0 \\
\frac{1}{M}
\end{pmatrix}
F(t)
\end{align*}

# P3.3 **state differential equation**
KCL을 다음회로의 가운데 노드에 적용하면 다음과 같이 식이 정리된다.
$$
KCL >> -i_L(t) + i_C(t) + i_R(t) = 0  
$$
이때 전류성분을 state로 정리하면 다음과 같다.
$$
i_C = \frac{dV_C(t)}{dt}= \frac{dx_2(t)}{dt}
$$
$$
i_L(t) = x_1(t)
$$
이를 KCL식에 대입하여 정리하면 다음과 같은 이계 미분식을 얻을수 있다.  

$$
\dot{x_2(t)} = -\frac{x_1(t)}{C} + \frac{i_R(t)}{C}
$$

안쪽 loop에 대하여 KVL을 적용하면 다음과 같다.
$$
V_2(t) - V_C(t) = i_R(t)R
$$
이를 i_R(t)에 대하여 정리하면 
$$
i_R(t) = -\frac{x_2(t)}{R} + \frac{V_2(t)}{R}
$$
이를 위의 이계미분식에 대입하여 정리하면
$$
\dot{x_2(t)} = -\frac{x_1(t)}{C}-\frac{x_2(t)}{RC}+\frac{V_2(t)}{RC}
$$

이번엔 바깥쪽 loop에 대하여 KVL을 적용하면 다음과 같은 식을 얻을수 있다.
$$
-V_1(t) +L\frac{di_L(t)}{dt} -V_C(t) +V_2(t) =0
$$
이에 대해 다시 전류성분에 대한 정리식을 대입하면
$$
\frac{dx_1(t)}{dt}-x_2(t) -V_1(t) +V_2(t) =0
$$
다음과 같이 두개의 일차미분방정식을 도출할수 있고 이를 통해 state differential equation을 도출하면
$$
\dot{x_1(t)} =\frac{x_2(t)}{L}+\frac{V_1(t)}{L}-\frac{V_2(t)}{L}
$$
$$
\dot{x_2(t)} = -\frac{x_1(t)}{C} + \frac{i_R(t)}{C}
$$

### **Answer**
$$
\dot{x}(t) = 
\begin{pmatrix}
0 & \frac{1}{L} \\
-\frac{1}{C} & -\frac{1}{RC}
\end{pmatrix}
x(t)
+ 
\begin{pmatrix}
\frac{1}{L} & -\frac{1}{L} \\
0 & \frac{1}{RC}
\end{pmatrix}
\begin{pmatrix}
V_1(t) \\
V_2(t)
\end{pmatrix}
$$



#  P3.5
## a) **transfer function**
### **Answer**
$$
\frac{Y(s)}{R(s)} = T(s) = \frac{s+2}{(s+8)(s-2)(s)}=\frac{(s+2)}{(s^3+5s^2-24s)}
$$

## b) **phase variable form**
위의 transfer function에 Z(s)를 분모와 분자에 곱해주면
$$
\frac{Y(s)}{R(s)} = T(s) = \frac{s+2}{(s+8)(s-2)(s)}=\frac{(s+2)Z(s)}{(s^3+5s^2-24s)Z(s)}
$$

$$
Y(s) = (s+2)Z(s)
$$
$$ 
R(s) =( s^3+5s^2-24s)Z(s)
$$
위의식을 역라플라스를 취하면
$$
y(t) =\dot{z(t)} +2z(t)
$$
$$
R(t) = \dddot{z(t)}+5\ddot{z(t)}-24\dot{z(t)}
$$

$$
x(t) = \begin{pmatrix} x_1(t) \\ x_2(t) \\ x_3(t) \end{pmatrix}
= \begin{pmatrix} x_1 \\ \dot{x_1(t)} \\ \dot{x_2(t)} \end{pmatrix}
= \begin{pmatrix} z(t) \\ \dot{z(t)} \\ \ddot{z(t)} \end{pmatrix}
$$

$$
y_(t) = x_2(t) + 2x_1(t)
$$

$$
R(t) = \dot{x_3(t)}+5x_3(t)-24x_2(t)
$$

$$
\dot{x_3(t)} = -5x_3(t)+24x_2(t)+R(t)
$$

### **Answer**
$$
\dot{x_(t)} = \begin{pmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 24 & -5 \end{pmatrix}x(t) + \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}R(t)
$$

$$
y(t) = \begin{pmatrix} 2 & 1 & 0 \end{pmatrix}x(t)
$$



#P3.12
##**(a) state variable model**
phase variable form을 이용하여 transfer function에서 state space를 유도해 보면

$$
\frac{Y(s) \mathcal{Z}(s)}{R(s) \mathcal{Z}(s)} = \frac{8(s+5) \mathcal{Z}(s)}{(s^3 + 12s^2 + 44s + 48) \mathcal{Z}(s)}
$$

$$
Y(s) = 8(s+5)\mathcal{Z}(s)
$$

$$
R(s) = (s^3 + 12s^2 + 44s + 48)\mathcal{Z}(s)
$$
두 수식에 역라플라스를 취하면 
$$
y(t) = 8\dot{\mathcal{Z}}(t) + 40\mathcal{Z}(t)
$$

$$
R(t) = \dddot{\mathcal{Z}}(t) + 12\ddot{\mathcal{Z}}(t) + 44\dot{\mathcal{Z}}(t) + 48\mathcal{Z}(t)
$$

state vector를 다음과 같이 정의하고

$$
x(t) = \begin{pmatrix} x_1(t) \\ x_2(t) \\ x_3(t) \end{pmatrix} = \begin{pmatrix} \mathcal{Z}(t) \\ \dot{\mathcal{Z}}(t) \\ \ddot{\mathcal{Z}}(t) \end{pmatrix}
$$

이를 위에 수식에 대입하면 다음과 같다.

$$
y(t) = 8x_2(t) + 40x_1(t)
$$

$$
R(t) = \dot{x}_3(t) + 12x_3(t) + 44x_2(t) +48x_1(t)
$$
이를통해 x_3(t)를 표현하고 state spcace equation을 나타내면 다음과 같다.


$$
\dot{x}_3(t) = -12x_3(t) - 44x_2(t) - 48x_1(t) + R(t)
$$
##**Answer**
###**-state differential equation**
$$
\dot{x}(t) = \begin{pmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ -48 & -44 & -12 \end{pmatrix} x(t) + \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} R(t)
$$
###**-output equation**
$$
y(t) = \begin{pmatrix} 40 & 8 & 0 \end{pmatrix} x(t)
$$


##**(b)state transition matrix**
state transition matrix를 구하는 수식은 다음과 같다.
$$
\Phi(s) = (sI - A)^{-1} = \begin{pmatrix} s & -1 & 0 \\ 0 & s & -1 \\ 48 & 44 & s+12 \end{pmatrix}^{-1}
$$

역행렬의 결과는 다음과 같다.
$$
\Phi(s) = \begin{pmatrix} 
\frac{3}{s+2} - \frac{3}{s+4} + \frac{1}{s+6} & \frac{5}{4(s+2)} - \frac{2}{s+4} + \frac{3}{4(s+6)} & \frac{1}{8(s+2)} - \frac{1}{4(s+4)} + \frac{1}{8(s+6)} \\
\frac{-6}{s+2} + \frac{12}{s+4} - \frac{6}{s+6} & \frac{-5}{2(s+2)} + \frac{8}{s+4} - \frac{9}{2(s+6)} & \frac{-1}{4(s+2)} + \frac{1}{s+4} - \frac{3}{4(s+6)} \\
\frac{12}{s+2} - \frac{48}{s+4} + \frac{36}{s+6} & \frac{5}{s+2} - \frac{32}{s+4} + \frac{27}{s+6} & \frac{1}{2(s+2)} - \frac{4}{s+4} + \frac{9}{2(s+6)}
\end{pmatrix}
$$

이를 역라플라스를 취하면 다음과 같다.

###**Answer**
$$
\Phi(t) = \begin{pmatrix} 
3e^{-2t} - 3e^{-4t} + e^{-6t} & \frac{5}{4}e^{-2t} - 2e^{-4t} + \frac{3}{4}e^{-6t} & \frac{1}{8}e^{-2t} - \frac{1}{4}e^{-4t} + \frac{1}{8}e^{-6t} \\
-6e^{-2t} + 12e^{-4t} - 6e^{-6t} & -\frac{5}{2}e^{-2t} + 8e^{-4t} - \frac{9}{2}e^{-6t} & -\frac{1}{4}e^{-2t} + e^{-4t} - \frac{3}{4}e^{-6t} \\
12e^{-2t} - 48e^{-4t} + 36e^{-6t} & 5e^{-2t} - 32e^{-4t} + 27e^{-6t} & \frac{1}{2}e^{-2t} - 4e^{-4t} + \frac{9}{2}e^{-6t}
\end{pmatrix}
$$




# p.3.17
주어진 state space equation으로부터 transfer function을 유도해보면
$$
\dot{x}(t) = A x(t) + B u(t)
$$
$$
y(t) = C x(t) + D u(t)
$$
두식에 대하여 라플라스를 취하면 다음과 같다.
$$
sX(s) = A X(s) + B U(s)
$$
$$
Y(s) = C X(s) + D U(s)
$$
역라플라스를 취한후 우측항을 이항하여 state transition matrix을 구할수 있다.
$$
(sI - A) X(s) = B U(s)
$$
$$
X(s) = (sI - A)^{-1} B U(s)
$$

$$
\Phi(s) = (sI - A)^{-1}
$$

state transition matrix을 X(s)으로 나타낸후 이를 Y(s)에 대입하여 G(S)를 유도할수 있다.
$$
X(s) = \Phi(s) B U(s)
$$

$$
Y(s) = C \Phi(s) B U(s) + D U(s)
$$

$$
G(s) = \frac{Y(s)}{U(s)} = C \Phi(s) B + D
$$


주어진 행렬값들을 정리해보면 다음과 같다.
$$
C = \begin{pmatrix} 1 & 0 & 0 \end{pmatrix}, \quad
\Phi = \begin{pmatrix} s-1 & -1 & 1 \\ -4 & s-3 & 0 \\ 2 & -1 & s-10 \end{pmatrix}
$$
$$
B = \begin{pmatrix} 0 \\ 0 \\ 4 \end{pmatrix}, \quad
D = 0
$$

위의 행렬들을 G(S)에 대입하여 구해보면

$$ G(s) = \begin{pmatrix} 1 & 0 & 0 \end{pmatrix} \begin{pmatrix} s-1 & -1 & 1 \\ -4 & s-3 & 0 \\ 2 & -1 & s-10 \end{pmatrix} \begin{pmatrix} 0 \\ 0 \\ 4 \end{pmatrix} + 0 $$

$$
G(s) = \begin{pmatrix} s-1 & 0 & 0 \end{pmatrix} \begin{pmatrix} 0 \\ 0 \\ 4 \end{pmatrix}=4
$$
### **Answer**
### $$G(s) = \frac{Y(s)}{U(s)} = 4$$
