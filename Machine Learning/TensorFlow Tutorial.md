## TensorFlow 설정하기
``` python
import tensorflow as tf
print("TensorFolow version :", tf.__version__)
```
## 데이터세트 로드하기
``` python
# 샘플데이터를 정수에서 부동 소수점 숫자로 변환
mnist = tf.keras.datasets.mnist

# x_train : 훈련용 이미지 데이터 , y_train : 정답 라벨
# x_test, y_test 모델 평가용
(x_train, y_train), (x_test, y_test) = mnist.load_data()

# 255로 나누는 이유는 픽셀값이 0~255범위이기에 0.0~1.0으로 바꾸는 정규화 작
x_train, x_test = x_train / 255.0, x_test / 255.0

```

```python
# 실제 데이터 확인해보기
import matplotlib.pyplot as plt

plt.imshow(x_train[0], cmap='gray')
plt.colorbar()
plt.show()

print(y_train[0])
```

## 머신러닝 모델 빌드하기
``` python

```
## 모델 훈련 및 평가하기
``` python

```
