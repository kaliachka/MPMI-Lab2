Лабораторная работа 2
===
Решение задачи классификации изображений из набора данных Oregon Wildlife с использованием нейронных сетей глубокого обучения и техники обучения Transfer Learning
----
#### Для решения задачи классификации изображений Oregon Wildlife необходимо было обучить нейронную сеть, с начальным случайным приближением, EfficientNet-B0.
Размерность входного изображения, как и первой лабораторной работе, 224х224х3 и, как было сказано выше, использовалась нейронная сеть EfficientNet-B0:
```
inputs = tf.keras.Input(shape=(RESIZE_TO, RESIZE_TO, 3));
outputs = EfficientNetB0(include_top=True,weights=None, classes = NUM_CLASSES)(inputs)
```
