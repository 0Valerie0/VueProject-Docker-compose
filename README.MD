# Dota 2 Heroes Gallery

Интерактивная галерея персонажей Dota 2 с каруселью карточек и плавными анимациями. Vue.js приложение, упакованное в Docker контейнер для гарантированной работы в любом окружении.

## Особенности

- Карусель персонажей с плавными анимациями
- Карточки героев с изображениями и описаниями
- Адаптивный дизайн
- Полностью контейнеризировано — работает одинаково везде

## Быстрый старт

### Предварительные требования
- Docker (версия 20.10+)
- Docker Compose

### Запуск за 3 шага:

1. Клонируйте репозиторий:
   ```bash
   git clone https://github.com/0Valerie0/VueProject-Docker-compose
   cd dota2-heroes-gallery```
   
2. Запустите через Docker Compose:
  docker-compose up --build
  
3. Откройте в браузере:
  http://localhost:9999
  
Структура проекта:

dota2-heroes/
├── Dockerfile
├── docker-compose.yml
├── package.json
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── main.js
│   ├── constants.js
│   ├── App.vue
│   ├── components/
│   ├── assets/
│   ├── router/
│   └── store/
└── README.md

Устранение неполадок 
  Порт 9999 уже занят:

    # Остановить все контейнеры Docker
    docker stop $(docker ps -q)

    # Или изменить порт в docker-compose.yml
    # Замените "9999:8080" на "8080:8080"

  Ошибки при сборке:
    # Полная пересборка
    docker-compose build --no-cache
    docker-compose up
