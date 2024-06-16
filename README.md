### Описание реализованного проекта по классификации эмоций

В данном проекте реализована модель для классификации человеческих эмоций на основе изображений лиц. Модель использует предобученную нейронную сеть MobileNetV2, которая была адаптирована для решения задачи классификации эмоций. Основные этапы проекта включают подготовку данных, создание и обучение модели, а также предсказание эмоций на новых изображениях.

#### Маппинг эмоций
В проекте используются следующие категории эмоций:
- Гнев (anger)
- Презрение (contempt)
- Отвращение (disgust)
- Страх (fear)
- Радость (happy)
- Нейтральное выражение (neutral)
- Печаль (sad)
- Удивление (surprise)
- Неуверенность (uncertain)

Для каждой категории эмоций назначен уникальный числовой идентификатор, что позволяет модели корректно сопоставлять изображения с соответствующими метками.

#### Обработка данных
Для работы с данными был создан пользовательский класс `EmotionDataset`, который загружает изображения из каталогов, преобразует их в нужный формат и сопоставляет с метками эмоций. Изображения предварительно уменьшаются до размера 128x128 пикселей для ускорения вычислений и снижения потребления ресурсов. Также изображения проходят нормализацию и преобразуются в тензоры, что необходимо для их подачи в нейронную сеть.

#### Трансформация изображений
Используется несколько трансформаций для подготовки изображений:
- Изменение размера до 128x128 пикселей.
- Преобразование в тензор.
- Нормализация с использованием средних и стандартных отклонений, характерных для предобученных моделей.

#### Создание и обучение модели
Для классификации эмоций была создана модель `EmotionClassifier`, основанная на предобученной MobileNetV2. Финальный слой классификации модели был заменен на слой с 9 выходными нейронами, соответствующими числу категорий эмоций.

Обучение модели происходило в течение 3 эпох с использованием функции потерь `CrossEntropyLoss` и оптимизатора `Adam`. Для ускорения вычислений и обработки больших объемов данных использовались пакеты размером 64 и параллельная обработка данных.

#### Предсказания на тестовых данных
Для тестирования модели был создан отдельный набор данных `TestDataset`, содержащий новые изображения, на которых необходимо сделать предсказания. Модель загружает изображения, преобразует их, а затем выполняет предсказание эмоций. Результаты предсказаний сохраняются для последующего анализа.

В итоге, реализованная модель позволяет эффективно классифицировать эмоции на основе изображений лиц, демонстрируя возможности использования предобученных нейронных сетей для решения специфических задач в области распознавания эмоций.

В качестве дополнения предоставлен файл data_research с первичным ознакомлением с данными и небольшая обработка.
