# Kittygram

Kittygram — это социальная сеть для обмена фотографиями своих котиков. 
Пользователи могут создавать профили своих питомцев, загружать фотографии, 
отмечать достижения и следить за другими котиками.

[![Django](https://img.shields.io/badge/Django-3.2-green)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.7-blue)](https://www.python.org/)
[![React](https://img.shields.io/badge/React-17.0-red)](https://reactjs.org/)

## Основные возможности

- 📷 Создание профиля котика с фото и описанием
- � Добавление достижений и наград
- 👀 Лента всех котиков
- ❤️ Возможность отмечать понравившихся котиков
- 🔎 Поиск котиков по имени или породе
- 📱 Адаптивный дизайн для мобильных устройств

## Технологии

**Backend:**
- Python 3.7
- Django 3.2
- Django REST Framework
- PostgreSQL

**Frontend:**
- React 17
- Redux
- Axios
- Material-UI

**Инфраструктура:**
- Docker
- Nginx
- GitHub Actions (CI/CD)

## Как запустить проект локально

### Предварительные требования
- Docker
- Docker Compose

### Инструкция по запуску

### 1. Клонируйте репозиторий и перейдите в директорию проекта:
```bash
git clone https://github.com/Annttonov/Kittygram.git
cd Kittygram
```
### 2. Настройка окружения

Создайте файл `.env` в корневой директории проекта и заполните его необходимыми переменными окружения:

```env
SECRET_KEY=your_secret_key
DB_ENGINE=django.db.backends.postgresql
DB_NAME=your_db_name
POSTGRES_USER=your_db_user
POSTGRES_PASSWORD=your_db_password
DB_HOST=db
DB_PORT=5432
```

### 3. Запуск проекта с помощью Docker

Находясь в корневой директории, соберите и запустите контейнеры:
###### (если вы используете Linux или MacOS, перед каждой командой нужно указывать 'sudo')

```bash
docker compose -f docker-compose.production.yml up -d --build
```

После запуска контейнеров выполните миграции и соберите статические файлы:

```bash
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

## API Endpoints

### 1. Пользователи:
```
GET /api/users/ - список пользователей
GET /api/users/{id}/ - конкретный пользователь
```
### 2. Котики:
```
GET /api/cats/ - список всех котиков
POST /api/cats/ - создать нового котика
GET /api/cats/{id}/ - получить котика
PUT /api/cats/{id}/ - полное обновление
PATCH /api/cats/{id}/ - частичное обновление
DELETE /api/cats/{id}/ - удалить котика
```

### 3. Достижения:
```
GET /api/achievements/ - список достижений
GET /api/achievements/{id}/ - конкретное достижение
Аутентификация (Djoser):
POST /api/auth/token/login/ - получить токен
POST /api/auth/token/logout/ - удалить токен
```

### Автор
Даниил Антонов - Начинающий "backend-developer" 😺
