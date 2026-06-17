# 1C: Адаптер Kafka - отчеты тестирования

[![Allure Report](https://img.shields.io/badge/Allure-Report-brightgreen)](https://allurereport.org/)
[![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-blue)](https://shadobaai.github.io/kafka-adapter-tests-reports/latest/)

Репозиторий хранит опубликованные HTML-отчеты тестирования
[1C: Адаптер Kafka](https://github.com/ShadobaAI/kafka-adapter).

## Назначение

Репозиторий используется как статическое хранилище общего Allure-отчета, который формируется в release pipeline.

В одном отчете публикуются:

- результаты unit-тестов;
- результаты UI-тестов;
- анализ покрытия unit-тестов;
- анализ покрытия UI-тестов;
- диагностические логи запуска тестов и сбора покрытия.

Опубликованный HTML-отчет можно открыть из summary workflow, из комментария Allure в pull request или по ссылке,
которая добавляется в описание релиза.

## Структура

- `latest/` - последний опубликованный общий отчет тестирования.
- `<run_id>-<run_attempt>/` - отчет конкретного запуска GitHub Actions.

Пример ссылки на отчет:

```text
https://shadobaai.github.io/kafka-adapter-tests-reports/<run_id>-<run_attempt>/
```

Ссылка `latest`:

```text
https://shadobaai.github.io/kafka-adapter-tests-reports/latest/
```

## Публикация

Публикация выполняется автоматически workflow `Release / Tests` в репозитории
[`ShadobaAI/kafka-adapter`](https://github.com/ShadobaAI/kafka-adapter).

Workflow:

1. Выполняет unit-тесты и UI-тесты.
2. Собирает покрытие для unit-тестов и UI-тестов в формате `genericCoverage.xml`.
3. Объединяет результаты тестов, отчеты покрытия и диагностические логи в общий Allure report.
4. Копирует общий отчет в этот репозиторий.
5. Обновляет каталог `latest/`.
6. Удаляет старые каталоги запусков согласно настройке хранения.
7. Добавляет ссылку на опубликованный отчет в описание релиза.

Ручные изменения внутри сгенерированных каталогов отчетов не предполагаются: следующий запуск workflow
может перезаписать или удалить эти файлы.

## GitHub Pages

Для репозитория должен быть включен GitHub Pages:

- source: deploy from a branch;
- branch: `main`;
- folder: `/ (root)`.

## Лицензия

Проект распространяется под лицензией [Apache License 2.0](LICENSE).
