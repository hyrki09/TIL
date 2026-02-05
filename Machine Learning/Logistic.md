# Binary Classification

- 둘 중 하나를 고르는 것
    - Spam Detection : Spam or Ham
    - Facebook feed : show or hide
- 0,1 로 학습을 시킴

## Hypothesis

- sigmoid 함수 (logistic function)
<img width="300" height="70" alt="logistic img2" src="https://github.com/user-attachments/assets/c16101d7-4395-4be3-ae9d-73425c1dd4c4" />
<img width="450" height="250" alt="logistic img" src="https://github.com/user-attachments/assets/0b5f577b-1a3b-49e2-a842-3018780d2a6f" />

- 기존에 리니어때 사용한 Hypothesis를 $z=WX$ 라고 두고
새로운 Hypothesis를  $H(x)=S(z)$ 라고 하자

- 그래서 로지스틱 Hypothesis는

<img width="630" height="228" alt="image3" src="https://github.com/user-attachments/assets/82244f1c-c21c-4ee0-b59a-041ac97980d0" />

## Hypothesis

- sigmoid 함수 (logistic function)

![image.png](attachment:b15483c3-7e90-41c7-9f46-d2681881a52f:image.png)

- 기존에 리니어때 사용한 Hypothesis를 $z=WX$ 라고 두고
새로운 Hypothesis를  $H(x)=S(z)$ 라고 하자

- 그래서 로지스틱 Hypothesis는

![image.png](attachment:c589ffe3-3fc3-4a62-9f4e-112d121e00ae:image.png)

$e^x$ 그래프

![image.png](attachment:db4abac3-efa2-422e-bd6a-57d01b8cd73e:image.png)

$e^{-x}$ 그래프

![image.png](attachment:7e25d4a3-a1b7-4402-9d35-8f024e1f062f:image.png)

로지스틱 함수는 x가 무한히 커질수록  $e^{-x}$가 0에 가까워진다. 그러므로 1에 가까워지고
x가 작아질수록   $e^{-x}$ 값은 무한히 커지며 0에 로

그러므로 이형의 그래프가 된다.

![image.png](attachment:535b27ed-919b-42e6-9cf9-60fbc428fe85:image.png)

## Cost

Hypothesis는 **확률을 만들기 위한 함수**이고, Cost 함수는 그 **확률이 얼마나 맞는지 평가하는 기준**이다.

로지스틱 회귀는 확률 모델이기 때문에 우도(likelihood)를 쓰게 되면 log함수를 사용하게 된다.

$$
c(H(x), y) =\begin{cases}-\log\big(H(x)\big), & y =  -\log\big(1 - H(x)\big), & y = 0\end{cases}
$$

$-\log(x)$

$-\log(1-x)$

![image.png](attachment:76407502-bb6d-4610-b44b-85b005599d2a:image.png)

![image.png](attachment:708a169e-c084-4695-a9d8-1121d2dd534a:image.png)

y=1일 때 $H(x)$값이 0에 가까울수록 $-\log\!\big(H(x)\big)$값이 무한히 커지게 되고 $H(x)$값이 1 에 가까울수록 0으로 간다.

반대로 y=0일 때  $H(x)$값이 1에 가까울수록 $-\log\!\big(1 - H(x)\big)$의 값이 무한히 커지게 되고  $H(x)$값이 0 에 가까울수록 0으로 간다.

이걸 하나의 식으로 변경하면

$$
c(H(x), y)= -\Big( y \log\!\big(H(x)\big)+ (1 - y)\log\!\big(1 - H(x)\big) \Big)
$$
