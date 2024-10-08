<h1>Определение возраста покупателей</h1>

**Проект для супермаркета «Хлеб-Соль»**

**Описание проекта.**

Сетевой супермаркет «Хлеб-Соль» внедряет систему компьютерного зрения для обработки фотографий покупателей. Фотофиксация в прикассовой зоне поможет определять возраст клиентов, чтобы:

- Анализировать покупки и предлагать товары, которые могут заинтересовать покупателей этой возрастной группы;
- Контролировать добросовестность кассиров при продаже алкоголя.
  
Постройте модель, которая по фотографии определит приблизительный возраст человека. В вашем распоряжении набор фотографий людей с указанием возраста.


<h2>Цель исследования</h2>

Построить модель, которая по фотографии определить приблизительный возраст человека.


<h2>Задачи исследования:</h2>

- Провести исследовательский анализ набора фотографий.
- Подготовить данные к обучению.
- Обучить нейронную сеть и рассчитайте её качество.


 <h2>Инструменты решения задачи</h2>

 - os
- pandas 
- numpy 
- matplotlib
- tensorflow
- seaborn 

- tensorflow.keras
- tensorflow.keras.layers  (Dense, GlobalAveragePooling2D)
- tensorflow.keras.models.Sequential
- tensorflow.keras.optimizers.Adam
- tensorflow.keras.preprocessing.image.ImageDataGenerator
- tensorflow.keras.applications.resnet.ResNet50


<h2>Исходные данные</h2>

Данные для анализа взяты с сайта ChaLearn Looking at People.

Данные находятся в папке /datasets/faces/: одна папка со всеми изображениями (/final_files) и CSV-файл labels.csv с двумя колонками:

- 'file_name' - названия файлов
- 'real_age' - возраст людей, изображенных в файлах (целевой признак)

<h2>Вывод по итогам исследования</h2>

Выполнила предобработку данных и исследовательский анализ.

Обучение модели запускали в отдельном GPU-тренажёре.

Перед обучением модели масштабировали фотографии и выровняли их горизонтально. Создали последовательную модель, с тремя слоями:

- базовый блок ResNet50
- слой глобальной средней обработки
- линейный слой с активацией ReLU.
- Добавили оптимизатор Adam с learning rate 0.0001 и компилируем модель с целью минимизации mean squared error и метрикой mean absolute error.

Значение MAE на тестовой выборке получилось 5.8188, что соответствует условию задачи. Это означает, что наша модель ошибается не более, чем на 5,8 лет.

Чтобы повысить качество модели рекомендую дополнить базу покупателями возраста старше 50 лет и подростками 10-15 лет, сейчас основная масса покупателей представлена в возрасте 20-40 лет.

Данная модель не рекомендована для контроля продажи алкоголя, но может успешно использоваться для анализа покупок и специализированных предложений в зависимости от возраста покупателей.
