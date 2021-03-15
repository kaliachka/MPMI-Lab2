Лабораторная работа 2
===
Решение задачи классификации изображений из набора данных Oregon Wildlife с использованием нейронных сетей глубокого обучения и техники обучения Transfer Learning
----
### Для решения задачи классификации изображений Oregon Wildlife необходимо было обучить нейронную сеть, с начальным случайным приближением, EfficientNet-B0.
Размерность входного изображения, как и первой лабораторной работе, 224х224х3 и, как было сказано выше, использовалась нейронная сеть EfficientNet-B0:
```
inputs = tf.keras.Input(shape=(RESIZE_TO, RESIZE_TO, 3))
outputs = EfficientNetB0(include_top=True,weights=None, classes = NUM_CLASSES)(inputs)
```
В нашем случае используется параметр `weights` со значением `None`, что означает использование начального случайного приближения. Параметр `include_top=true` oзначает использование верхних слоев нейронной сети, отвечающих за классификацию изображений. Параметр `classes = NUM_CLASSES` отвечает за количество классов классифицированных изображений (в нашем случае количество классов = 20).

Графики обучения для задачи классификации изображений Oregon WildLife, используя случайное начальное приближение:
----
*синяя ломаная линия - на валидации*

*оранжевая ломаная линия - на обучении*

**График метрики точности:**

![1](https://user-images.githubusercontent.com/59210216/111230601-f1cc1700-85f8-11eb-8f42-d3ce70cec56e.jpg)


**График функции потерь:**

![2](https://user-images.githubusercontent.com/59210216/111230610-f4c70780-85f8-11eb-899b-1b96f373cedd.jpg)

Анализ полученных результатов:
-------
Анализируя полученные диаграммы можно заметить, что, на графике функции метрики точности, ломаная на валидации начала линейно возрастать, по отношению к графику функции потерь. Однако, если рассмотреть ломаную на обучении, то на графике функции потерь данная линия сильно убавила свои значения, по отношению к графику метрики точности. Также хочется отметить, что точность как на тренировочном, так и на валидационном наборе данных очень низкая (в максимальной точке достикается лишь 13%). Все это говорит о переобучение тестируемой модели, что может быть вызвано тем, что наш датасет слишком мал для начальных случайных приближений.

### С использованием примера, описываемого выше, и техники обучения Transfer Learning обучить нейроннуюсеть EfficientNet-B0, предобученную на базе изображений imagenet, для решения задачи классификации изображений Oregon WildLife:



