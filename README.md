# RuCode 2022 (top 5)

Решение основной задачи "Определение цвета автомобиля" трека рукод по искусственному интеллекту.

Приватный лидерборд (rucode6user-0030)  |
:---------------------------------------|
тут картинка                            |


## Данные
Тренировочные и тестовые данные представляют собой картинки различных автомобилей 7 цветов:
Черный (Black), Синий (Blue), Коричневый (Brown), Голубой (Cayan), Зеленый (Green), Серый (Gray), 
Оранжевый (Orange), Красный (Red), Фиолетовый (Violet), Белый (White), Желтый (Yellow).

> картинка с распределением данных


## Предобработка данных
Во время обучения данные предобрабатывались с помощью различных аугментаций таких, как random rotation, random perspective, random posterize, random equalize.
Из них для обучения итоговой модели была оставлена только random equalize.

> картинка с аугментацией

Затем данные нормализовались со значениями среднего ```mean = [0.485, 0.456, 0.406]``` и стандартного отклонения ```std = [0.229, 0.224, 0.225]```. Для всей предобработки данных использовался модуль ```torchvision.transforms```.

## Модель и обучение
Для классификации использовалась модель [ResNet101](https://pytorch.org/vision/stable//models/generated/torchvision.models.resnet101.html) из ```torchvision.models```.

При обучении у модели были разморежены последние два слоя (layer3 и layer4).
Так же использовался оптимизатор [Adam](https://pytorch.org/docs/stable/generated/torch.optim.Adam.html) и функция потерь [CrossEntropy](https://pytorch.org/docs/stable/generated/torch.nn.CrossEntropyLoss.html), для шедулинга lr использовался [StepLR](https://pytorch.org/docs/stable/generated/torch.optim.lr_scheduler.StepLR.html) scheduler. При обучении целью было получить максимальное значение метрики [f1-score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html).
















