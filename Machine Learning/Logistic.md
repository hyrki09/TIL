# Binary Classification

- 둘 중 하나를 고르는 것
    - Spam Detection : Spam or Ham
    - Facebook feed : show or hide
- 0,1 로 학습을 시킴

## Hypothesis

- sigmoid 함수 (logistic function)

![image.png](attachment:b15483c3-7e90-41c7-9f46-d2681881a52f:image.png)

![image.png](attachment:535b27ed-919b-42e6-9cf9-60fbc428fe85:image.png)

- 기존에 리니어때 사용한 Hypothesis를 $z=WX$ 라고 두고
새로운 Hypothesis를  $H(x)=S(z)$ 라고 하자

- 그래서 로지스틱 Hypothesis는

![image.png](attachment:c589ffe3-3fc3-4a62-9f4e-112d121e00ae:image.png)
