# 1C: Адаптер Kafka - отчеты UI-тестов

[![Allure Report](https://img.shields.io/badge/Allure-Report-brightgreen)](https://allurereport.org/)
[![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-blue)](https://shadobaai.github.io/kafka-adapter-tests-ui-reports/)

Репозиторий хранит опубликованные HTML-отчеты UI-тестов
[1C: Адаптер Kafka](https://github.com/ShadobaAI/kafka-adapter).

## Назначение

Репозиторий используется как статическое хранилище Allure-отчетов, которые формируются в release pipeline.

Отчеты публикуются GitHub Actions из репозитория адаптера после выполнения UI-тестов. Опубликованный
HTML-отчет можно открыть в браузере из summary workflow или из комментария Allure в pull request.

## Структура

- `latest/` - последний опубликованный отчет UI-тестов.
- `<run_id>-<run_attempt>/` - отчет конкретного запуска GitHub Actions.

Пример ссылки на отчет:

```text
https://shadobaai.github.io/kafka-adapter-tests-ui-reports/<run_id>-<run_attempt>/
```

## Публикация

Публикация выполняется автоматически workflow `Release / Tests` в репозитории
[`ShadobaAI/kafka-adapter`](https://github.com/ShadobaAI/kafka-adapter).

Workflow:

1. Формирует Allure HTML-отчет по результатам UI-тестов.
2. Копирует отчет в этот репозиторий.
3. Обновляет каталог `latest/`.
4. Удаляет старые каталоги запусков согласно настройке хранения.

Ручные изменения внутри сгенерированных каталогов отчетов не предполагаются: следующий запуск workflow
может перезаписать или удалить эти файлы.

## GitHub Pages

Для репозитория должен быть включен GitHub Pages:

- source: deploy from a branch;
- branch: `main`;
- folder: `/ (root)`.

## Лицензия

Проект распространяется под лицензией [Apache License 2.0](LICENSE).
