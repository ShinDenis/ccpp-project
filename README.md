# Прогнозирование мощности газотурбинной электростанции (CCPP)

> Регрессионный анализ и сравнение ML-моделей на датасете UCI Combined Cycle Power Plant

---

## Описание проекта

Проект посвящён предсказанию **часовой выходной электрической мощности (PE, МВт)** газотурбинной электростанции комбинированного цикла по четырём параметрам окружающей среды. Работа охватывает полный цикл: от разведочного анализа данных до сравнения нескольких ML-моделей с единым препроцессинг-пайплайном.

**Датасет:** [UCI CCPP Dataset](https://archive.ics.uci.edu/dataset/294/combined+cycle+power+plant) — 9568 наблюдений, 5 переменных.

---
# Этапы и итоги проекта: [`Power plant project presentation`]( https://github.com/ShinDenis/ccpp-project/blob/main/Power%20plant%20project%20presentation.pdf)
<a href="https://github.com/ShinDenis/ccpp-project/raw/main/Power%20plant%20project%20presentation.pdf" target="_blank">
  <img src="https://img.shields.io/badge/Скачать презентацию PDF%20-blue?style=for-the-badge" alt="Скачать презентацию">
</a>


## Методология

### 1. Разведочный анализ (EDA) - `CCPP_analysis.ipynb`

### 2. Пайплайн и сравнение моделей - `CCPP_feature-eng_model.ipynb`

Все модели обучаются через единый `sklearn.Pipeline`:

```
Фильтрация выбросов → Импутация (ColumnTransformer) → RobustScaler → Модель
```

---

## Сравниваемые модели

| Модель | Примечание |
|--------|------------|
| Linear Regression | Базовая модель |
| Random Forest | Ансамбль деревьев |
| **Gradient Boosting** | Градиентный бустинг |
| SVR | Метод опорных векторов |
| KNN Regressor | k-ближайших соседей |
| XGBoost | X Градиентный бустинг |
| ANN | Нейросеть |

---

## Результаты
![alt text](<results plot.png>)
По совокупности метрик лучший результат показывают **Gradient Boosting** и **XGBoost**:

> Точные значения отображаются в интерактивном дашборде ноутбука (`Show Metrics to Compare`).

---

## Технологии

- **Python 3.x**
- pandas, numpy, scipy
- scikit-learn, feature-engine, xgboost
- tensorflow / keras
- statsmodels
- shap
- matplotlib, seaborn
- ipywidgets (интерактивный UI)

---


### Рекомендуется запускать в порядке:
1. `Power plant project presentation` - Презентация проекта. Итоги работы.
2. `CCPP_analysis.ipynb` — EDA и выбор стратегий предобработки.
3. `CCPP_feature-eng_model.ipynb` — обучение и сравнение моделей.


---

## 📎 Источники

- Pınar Tüfekci, *Prediction of full load electrical power output of a base load operated combined cycle power plant using machine learning methods*, EAAI, 2014.
- Heysem Kaya et al., *Local and Global Learning Methods for Predicting Power of a Combined Gas & Steam Turbine*, ICEEN, 2012.
- UCI ML Repository: [https://archive.ics.uci.edu/dataset/294/combined+cycle+power+plant](https://archive.ics.uci.edu/dataset/294/combined+cycle+power+plant)
