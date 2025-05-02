# 🐶🐱🐯 Классификация изображений животных (Cat / Dog / Wild)

## 📌 Описание проекта

Проект представляет собой систему классификации изображений животных с использованием нейронной сети. Интерфейс создан на базе **Streamlit**, а API реализован с помощью **FastAPI**. Пользователь может загрузить изображение или нарисовать его, после чего модель определяет, изображён ли **кот**, **собака** или **дикое животное**.

## 📊 Используемый датасет

Был выбран [датасет](https://www.kaggle.com/datasets/andrewmvd/animal-faces) из трёх категорий:
- 🐱 **Cat** – изображения домашних кошек
- 🐶 **Dog** – изображения домашних собак
- 🐯 **Wild** – изображения диких животных (львы, тигры, медведи и т.д.)

Размер изображений приведён к 128x128 пикселям, и они нормализованы для подачи в модель.

## 🤖 Сравнение моделей

| Модель                  | Accuracy | Precision | F1-мера | Время инференса (сек) |
|------------------------|----------|-----------|--------|----------|
| model5          | 0.9707    | 0.9707     | 0.9706   | 12.8691    |
| model4         | 0.8673   | 0.8740      | 0.8668   | 10.5642     |
| model3 | 0.8773 | 0.8776  | 0.8774 | 7.5133 |
| model2 | 0.6613 | 0.6901	  | 0.6576 | 7.6500 |

![image](https://github.com/user-attachments/assets/afdc823a-d8d1-42cc-9135-96f78a816c6d)

## 📈 Визуализации результатов

Пример распределения вероятностей предсказания модели:

![image](https://github.com/user-attachments/assets/be2a87df-e847-41ff-9dfb-86f6ceda02a3)

Пример изображения, классифицированного моделью:

![image](https://github.com/user-attachments/assets/a31be53d-6013-4caf-8928-136c3e2bfc9a)


## 🛠️ Инструкции по локальному развертыванию

1. **Клонируйте репозиторий**:
   ```bash
   git clone https://github.com/TitanLeonov/animal-image-classifier.git
   cd animal-image-classifier
2. **Установите зависимости**:
   ```bash
   pip install -r requirements.txt

3. **Запуск FastAPI (бэкенд):**:
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000 --reload

4. **Запуск Streamlit-приложения (фронтенд):**:
   ```bash
   streamlit run app.py

5. **Откройте приложение в браузере: http://localhost:8501 (порт 8501 установлен по умолчанию)**

## 🌐 Ссылки на деплой

🔗 Развёрнутый FastAPI API: https://cat-dog-wild-classification.onrender.com/docs

🎨 Streamlit-приложение: https://animal-image-classifier.streamlit.app/

# 📦 Примеры использования API (curl)

# Отправка изображения на FastAPI сервер
curl -X POST https://your-fastapi-service.onrender.com/predict/ \
  -H "accept: application/json" \
  -F "file=@your_image.png"

# 🔁 Пример ответа от сервера:
# {
#   "predicted_class": "dog",
#   "probabilities": {
#     "cat": 0.03,
#     "dog": 0.94,
#     "wild": 0.03
#   }
# }
