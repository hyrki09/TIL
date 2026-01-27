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
