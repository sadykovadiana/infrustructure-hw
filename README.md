# Домашнее задание ШРИ: Инфраструктура

Настройка скриптов для автоматизации релизов

## Реализация

Задача реализована с помощью Github Actions
В корне настроен конфиг Dockerfile
Все фичи реализованы в отдельных jobs в yaml файле /infrastructure-hw/.github/workflows/ci.yml

- job "release" - реализовано создание релизного тикета со всей необходимой информацией в описании и его обновление, а также добавление комментариев при fix коммитах в текущий релиз
- job "buildDockerImage" - создание докер образа (https://hub.docker.com/repository/docker/sadykovadiana/demo-app) и сохранение комментария в релизный тикет о результатах
- job "testing" - запуск автотестов и сохранение комментария о результатах тестирования

## Примерный сценарий

Запушить в репозиторий пару коммитов
Запушить новый тег с номером версии, например v3.0.0

- В трекере сформируется релизный тикет (Release ticket v3.0.0) с информацией о новом релизе и комитами сделанными ранее в changelog списке
- В комментариях к тикету добавится информация о сборке Docker image и результатах прохождения тестов
  Сломать какой-нибудь тест и запушить изменения в github
- В комментариях, к ранее созданному тикету, появится информация о новом коммите, также отдельным комментарием информация о непройденных тестах
  Починить тест
- В комментариях отразится информация о фиксе и результат повторного прохождения тестов, сборке нового Docker image
