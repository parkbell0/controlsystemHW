#**제어공학 HW Chapter.2**
#**2021732082_박종영**  
###p2.7, p2.12, p2.15, p2.26, p2.37


# P2.7
##**transfer function**
op-amp의 경우 이상적이라는 가정을 했을때 입력단 임피던스는 무한이고,
입력 전류가 0, 입력단 전위차가 0이다. 즉 -단자 전위가 ground와 같은 0V이다. input 에서 -단자 방향으로 흐르는 전류 I_in과 커패시터를 
지나 출력단 방향으로 흐르는 전류 I_C의 크기를 구해보면
$$
Iin = \frac{V_1(t)-0}{R}=\frac{V_1(t)}{R}
$$

$$
I_C = C\frac{dV_2(t)}{dt}
$$
이때 -단자로 흘러들어가는 전류는 0이므로 KCL법칙에 의해 I_in과 I_C는 같은것을 알수있다. 즉 다음과 같은 등식이 성립함으로
$$
Iin = \frac{V_1(t)}{R} =C\frac{dV_2(t)}{dt} = I_C
$$
이를 라플라스하면 
$$
\frac{V_1(s)}{R} = CsV_2(s)
$$
이를 정리하여 transfer function으로 표현하면
### **Answer**
$$
\frac{V_2(s)}{V_1(s)} = \frac{1}{RCs}
$$

# P2.12  
open-loop transfer function은 다음과 같다.  
$$
\frac{Y(s)}{R(s)} = T(s) = \frac{K}{s+50}
$$
$$
R(s) = \frac{1}{s}일때
$$

$$
Y(s) = \frac{k}{50}(\frac{1}{s}-\frac{1}{s+50})이므로
$$
이를 역라플라스 하면
$$
y(t) = \frac{k}{50}(1-e^{-50t})
$$
이때 t가 양의 무한대로 향할때
$$
\lim_{s \to 0}y(t)=\frac{k}{50}
$$
즉 k가 50일때 y(t) = 1로 수렴한다고 볼수 있다.
이를 정리하면
$$
y(t)_{t \to \infty} = \lim_{s \to 0} sY(s) = \frac{K}{50}
$$

### **Answer**

$$
K=50일때, y(t)_{t \to \infty} =1
$$

# P2.15 
##**differential equation**
Newton's second law에 의하여  
mass m에 가해지는 모든 힘의 합 F, 즉 외력에 댐퍼에 의한 반발력과 스프링에 의한 반발력을 뺀 값이 가속도로 작용함을 근거로 수학적 모델링을 세워보면 다음과 같다.
$$ 
 \sum F = r(t)-b\frac{dx(t)}{dt}-kx(t)=Ma=M\frac{d^2x(t)}{dt^2}
$$
이때 초기조건에서 impulse input이 0이므로 r(t)=0이므로  이를 대입하여
 differential equation으로 정리하면

###**Answer**
$$
\frac{d^2x(t)}{dt^2}=-\frac{b}{M}\frac{dx(t)}{dt}-\frac{k}{M}x(t)
$$
# P2.26
## **equation of motion for two mass model of robot**

$$
M\ddot{x(t)} + b(\dot{x(t)} - \dot{y(t)}) + k(x(t) - y(t)) = F(t)
$$

$$
m\ddot{y(t)} + b(\dot{y(t)} - \dot{x(t)}) + k(y(t) - x(t)) = 0
$$
두식을 라플라스 한결과는 다음과 같다.
$$
(Ms^2+bs+k)X(x)−(bs+k)Y(s) = F(s) 
$$

$$
−(bs +k)X(x)+ (ms2+bs+k)Y(s) = 0
$$
이를 matrix form으로 정리하면
## **Matrix form**
$$
\begin{pmatrix} Ms^2+bs+k & −(bs+k) \\ −(bs +k) & ms2+bs+k \end{pmatrix}\begin{pmatrix} X(s) \\ Y(s)\end{pmatrix}=\begin{pmatrix} F(s) \\ 0\end{pmatrix}
$$

###**Answer**  
$$
\frac{Y(s)}{F(s)}=\frac{(bs + k)}{mM s^2 \left[ s^2 + \left(1 + \frac{m}{M}\right) \left(\frac{bs}{m} + \frac{k}{m}\right) \right]}
$$
# P2.37
##**a) differential equation**
P2.15와 마찬가지로 mass에 가해지는 힘의 합이 가속도로 나타남을 근거로
수학적 모델링을 세워보면 다음과 같다. 

$$
\sum F = Ma=m_1 \frac{d^2x(t)}{dt^2} =-( k_1 + k_2) x(t) + y(t) 
$$

$$
\sum F = Ma=m_2 \frac{d^2y(t)}{dt^2} = k_2 (x(t) - y(t)) + u(t)
$$
이때 input force는 m2에만 영향을 주며,
주어진 상수 m1 = m2 =1, k1 =k2 =1을 위에 식에 대입한후 정리해 주면 다음과 같다.
###**Answer**
$$
m_1 \frac{d^2x(t)}{dt^2} =  −2x(t)+y(t)
$$

$$
m_2 \frac{d^2y(t)}{dt^2} =  x(t)−y(t)+u(t) 
$$

##**b) transfer function**
위에 두가지 식에 라플라스를 적용하면

$$
 s^2X(s) +2X(s) = Y(s)
$$
$$
s^2Y(s)+Y(s) = X(s)+U(s)
$$
첫번째 식을 정리하면
$$
X(s) =\frac{Y(s)}{s^2+2}
$$
이를 두번째식에 대입하여 Y(s)에 대하여 정리하면

$$
(s^2+1)Y(s)=\frac{Y(s)}{s^2+2}+U(s)
$$
###**Answer**
$$
 \frac{Y(s)}{U(s)} = \frac{(s^2+2)}{s^4+3s^2+1}
$$
