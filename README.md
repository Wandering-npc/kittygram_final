## Описание проекта

Киттиграм - это сайт на котором пользователи могут выкладывать фотографии котиков и описывать их характеристики и достижения. 

#  Как работать с репозиторием финального задания

## Что нужно сделать

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

## Как проверить работу с помощью автотестов

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.

## Чек-лист для проверки перед отправкой задания

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.

## Как запустить проект. 

1. Склонируйте форкнутый репозиторий 
```yaml
git@github.com:username/kittygram_final.git
```
2. Установите докер
```
sudo apt update
sudo apt install curl
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo apt install docker-compose
```
3. Создайте и заполните файл .env 

4. В файле main.yml измените значения с оригинальным логином на ваш(логины докерхаб и гитхаб)

5. Измените настройки внешнего Nginx 
```
location / {
    proxy_set_header Host $http_host;
    proxy_pass http://127.0.0.1:9000;
}
```
6. Добавьте секреты в GitHub Actions:
```
DOCKER_USERNAME                # имя пользователя в DockerHub
DOCKER_PASSWORD                # пароль пользователя в DockerHub
HOST                           # IP-адрес сервера
USER                           # имя пользователя
SSH_KEY                        # содержимое закрытого SSH-ключа
SSH_PASSPHRASE                 # пароль для SSH-ключа

TELEGRAM_TO                    # ID телеграм-аккаунта (@userinfobot, команда /start)
TELEGRAM_TOKEN                 # токен бота (@BotFather, команда /token, имя бота)
```