## Hypothesis

$H(x)=Wx+b$

## Cost Function

- 우리가 세운 가설과 실제값이 얼마나 다른가를 나타내는 것
- 가장 작은 값을 가지는 W,b를 구하는 리그레이션의 학습이다

$cost(W,b)=\dfrac{1}{m}\displaystyle\sum_{i=1}^m(H(x^{(i)})-y^{(i)})^2$

## Gradient descent algorithm

- 경사를 따라 내려가는 알고리즘
- Cost 함수를 미니마이즈하는데 사용한다
- 경사도(기울기에 따라)를 따라서 내려가게 되면 → 결국 기울기 없는 그 지점을 구하는 알고리즘

$W\coloneqq W-\alpha\dfrac{1}{m}\displaystyle\sum_{i=1}^m(Wx^{(i)}-y^{(i)})x^{(i)}$

- 기계적으로 적용만 시키면 코스트 function을 최소화하는 W를 구할수있다.
