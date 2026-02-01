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
# Sequential은 레이어를 선형으로 쌓아 모델로 그룹화합니다.
model = tf.keras.models.Sequential([
    tf.keras.layers.Flatten(input_shape=(28,28)),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dropout(0.2),
    tf.keras.layers.Dense(10, activation='softmax')
])

model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])



predictions = model(x_train[:1]).numpy()
predictions

# array([[0.10000563, 0.21942893, 0.07176314, 0.06781223, 0.14129883,
#       0.04537253, 0.13821264, 0.06895518, 0.06357346, 0.08357748]],
#     dtype=float32)

tf.nn.softmax(predictions).numpy()

# array([[0.09987405, 0.11254275, 0.09709281, 0.09670997, 0.10408449,
#       0.09456398, 0.10376377, 0.09682057, 0.0963009 , 0.0982467 ]],
#     dtype=float32)

loss_fn = tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True)

loss_fn(y_train[:1], predictions).numpy()
# np.float32(2.3584783)

model.compile(optimizer='adam',
              loss=loss_fn,
              metrics=['accuracy'])

```
## 모델 훈련 및 평가하기
``` python
model.fit(x_train, y_train, epochs=5)
# Epoch 1/5
# /usr/local/lib/python3.12/dist-packages/keras/src/backend/tensorflow/nn.py:717: UserWarning: "`sparse_categorical_crossentropy` received `from_logits=True`, but the `output` argument was produced by a Softmax activation and thus does not represent logits. Was this
# intended?
#   output, from_logits = _get_logits(
# 1875/1875 ━━━━━━━━━━━━━━━━━━━━ 16s 8ms/step - accuracy: 0.8602 - loss: 0.4736
# Epoch 2/5
# 1875/1875 ━━━━━━━━━━━━━━━━━━━━ 14s 4ms/step - accuracy: 0.9566 - loss: 0.1488
# Epoch 3/5
# 1875/1875 ━━━━━━━━━━━━━━━━━━━━ 9s 5ms/step - accuracy: 0.9696 - loss: 0.1043
# Epoch 4/5
# 1875/1875 ━━━━━━━━━━━━━━━━━━━━ 10s 5ms/step - accuracy: 0.9734 - loss: 0.0854
# Epoch 5/5
# 1875/1875 ━━━━━━━━━━━━━━━━━━━━ 13s 7ms/step - accuracy: 0.9767 - loss: 0.0746
# <keras.src.callbacks.history.History at 0x7a29731384a0>

model.fit(x_train, y_train, epochs=5)

model.evaluate(x_test, y_test, verbose=2)

probability_model = tf.keras.Sequential([
    model,
    tf.keras.layers.Softmax()
])

probability_model(x_test[:5])

```
