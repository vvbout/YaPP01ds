# YaPP01ds
## A telecom operator needs a model to choose between 2 tariffs to make the best offer to customers based on their behavior
## РЕКОМЕНДАЦИЯ ТАРИФОВ ДЛЯ КЛИЕНТОВ ТЕЛЕКОМ ОПЕРАТОРА

**Задача проекта:** на основании данных о поведении клиентов построить модель с максимально большим значением accuracy для задачи классификации,
которая предложит подходящий тариф (smart или ultra)

Предобработка данных, исследовательский анализ данных, визуализация данных, классификация, машинное обучение

**Язык:** Python

**Библиотеки:** Pandas, Numpy, Matplotlib, Seaborn, Scikit-learn

**ВЫВОДЫ:**

* По результатам сравнения 3-х моделей (LogisticRegression, DecisionTreeClassifier, RandomForestClassifier)
с подобранными гиперпараметрами (RandomizedSearchCV) лучшие метрики показала модель RandomForestClassifier
* Модели RandomForestClassifier подобраны гиперпараметры:
>
> n_estimators=53
>
> max_depth = 7
>
> min_samples_leaf = 8

* Модель показала на тестовой выборке следующие результаты по метрикам:

1. Accuracy: 0.82
2. Precision: 0.81
3. Recall: 0.53

* Для проверки адекватности / надежности моделей выбрана метрика ROC_AUC, которая показала, что все 3 рассматриваемые модели
имеют достаточно низкий результат по метрике:
>
> LogisticsRegression = 0.50
> 
> DecisionTreeClassifier = 0.53
> 
> RandomForestClassifier = 0.45
> 
все 3 модели находятся на пороге 0.50, который характеризует результат предсказания моделей скорее как случайный.

* на поведение метрики влияют 2 ключевых фактора:
1. дисбаланс классов (70х30)
2. 25% данных, относящихся к рецессивному классу (тариф ultra), совпадают по всем признакам с доминантным классом (тариф smart)

* Рекомендуется к внедрению выбранная модель Случайного леса с фокусом на метрику accuracy, что позволит рекомендовать клиентам "корректный" вариант тарифа,
основанный именно на их поведении.
**Лучшее соответствие предложения реальным потребностям (паттернам поведения) повысит лояльность клиентов.**
