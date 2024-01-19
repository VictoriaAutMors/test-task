## Содержимое
* [Задания](#task)
* [Зависимости](#dependencies)
* [Классификатор тональности текста](#sentiment)
* [Классификатор тематики текста](#classification)
* [Векторный поиск](#cos)

# <a name="task"> </a> Задания
1. Написать на Python, без использования генеративных сетей, простой классификатор тональности текста.

2. Написать на Python, без использования генеративных сетей, простой классификатор тематики текста.
a. Например, в качестве теста, чтоб умел различать две тематики: Спорт и Политика.

3. Написать на Python векторный поиск, без использования генеративных сетей. Например, у нас есть 20 строк с разным текстом разных тематик, пользователь вводит текст, и мы должны найти максимально близкую строку путем косинусной близости.
В обоих случаях, на вход получает текст, результат выводит в консоль.

# <a name="dependencies"></a> зависимости 
#### sklearn
#### spacy
##### spacy - ru_core_news_md
##### spacy - en_core_web_md

# <a name="sentiment"></a> классификатор тональности текста
Модель обучена на комментариях с reddit. Программа раздлена на две части data_processing и sentiment_analysis:
* data_processing - обработка датасета и приведения его к стандартной форме.
* sentiment_analysis - обучения модели и прогнозировние. Модель была обучена с помощью Логичской Регрессии(tf-idf) и Наивной Баевской классификации(tf-idf)
классификационные метрики для модели обученной с помощью Логичской Регрессии(tf-idf):
              precision    recall  f1-score   support

          -1       0.78      0.62      0.70      1634
           0       0.78      0.90      0.83      2606
           1       0.82      0.80      0.81      3190

    accuracy                           0.80      7430
   macro avg       0.79      0.77      0.78      7430
weighted avg       0.80      0.80      0.79      7430

классификационные метрики для модели обученной с помощью Наивной Баевской классификации(tf-idf):
              precision    recall  f1-score   support

          -1       0.92      0.10      0.19      1634
           0       0.84      0.32      0.46      2606
           1       0.49      0.97      0.65      3190

    accuracy                           0.55      7430
   macro avg       0.75      0.46      0.43      7430
weighted avg       0.71      0.55      0.48      7430

# <a name="classification"></a> классификатор тематики текста
Модель обучена на Корпусе новостей с Lenta.Ru. Программа раздлена на две части data_processing и classification_analysis:
* data_processing - обработка датасета и приведения его к стандартной форме.
* classification_analysis - обучения модели и прогнозировние. Модель была обучена с помощью Логичской Регрессии(tf-idf)
Обучены две модели одна различает только спорт и политику, другая может различать 47 разных тэгов с Lenta.Ru.
классификационные метрики для модели:
              precision    recall  f1-score   support

    Политика       1.00      1.00      1.00      8085
       Спорт       0.99      0.99      0.99      5306

    accuracy                           0.99     13391
   macro avg       0.99      0.99      0.99     13391
weighted avg       0.99      0.99      0.99     13391

# <a name="cos"></a> Векторный поиск
Есть возможность использовать либо русский или английский язык(по умолчанию идет английский). Использует для теста csv файл в папке data для сравнения с предложением данным пользователем. Если такого нет, то программа воспользуется базовым набором для сравнения. Также есть возможность сравнить набор с самим собой, если оставить ввод пустым. 