# Glossly — тренажёр для изучения иностранных слов

Веб-приложение для изучения иностранных слов. Персональный словарь, колоды по темам, тренировки с вариантами ответа и интервальное повторение по алгоритму SM-2.

**Авторы:** [@asfkam1ru-hub](https://github.com/asfkam1ru-hub), [@Alephod](https://github.com/Alephod)

---

## О проекте

Glossly состоит из React-фронтенда и Flask-бэкенда с SQLite. Основные разделы:

- **Главная** — статистика, история тренировок, виджет «слово дня»
- **Словарь** — CRUD слов (термин, перевод, пример, сложность, изображение)
- **Колоды** — группировка слов, тренировка по выбранной колоде
- **Тренировка** — вопросы «слово → перевод», «перевод → слово», «картинка → слово» и обратные варианты; слова с наступившей датой повторения подбираются через SM-2

**Стек**

![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?logo=vite&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router-7-CA4245?logo=reactrouter&logoColor=white)

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3-000000?logo=flask&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white)
![Gunicorn](https://img.shields.io/badge/Gunicorn-21+-499848)

![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)

---

## Скриншоты

| Главная |
|---------|
| ![Главная](docs/screenshots/home.png) |

| Словарь |
|---------|
| ![Словарь](docs/screenshots/dictionary-1.png) |
| ![Словарь](docs/screenshots/dictionary-2.png) |

| Колоды |
|---------|
| ![Колоды](docs/screenshots/decks.png) |

| Тренировка |
|---------|
| ![Тренировка](docs/screenshots/training.png) |

---

## Запуск

### Docker

```bash
git clone <url-репозитория>
cd TermPaper
```

Файл `.env` в корне:

```env
FLASK_CONFIG=production
DATABASE_URL=sqlite:///database.db

VITE_API_URL=http://localhost:5000

BACKEND_PORT=5000
FRONTEND_PORT=4173
```

```bash
docker compose up --build
```

| Сервис | URL |
|--------|-----|
| Frontend | http://localhost:4173 |
| Backend API | http://localhost:5000/api |

При первом запуске backend применяет миграции БД.

### Локальная разработка

**Backend**

```bash
cd backend
python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate     # macOS / Linux
pip install -r requirements.txt
flask db upgrade
python run.py
```


**Frontend**

```bash
cd frontend
npm install
```

Файл `frontend/.env`:

```env
VITE_API_URL=http://localhost:5000
```

```bash
npm run dev
```

---

## Структура

```
TermPaper/
├── backend/          # Flask API, SM-2, миграции
├── frontend/         # React SPA
├── docs/screenshots/ # скриншоты для README
└── docker-compose.yml
```
