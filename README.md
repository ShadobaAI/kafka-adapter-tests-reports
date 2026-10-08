# 1C: Адаптер Kafka — отчёты тестирования

[![Allure Report](https://img.shields.io/badge/Allure-Report-brightgreen)](https://allurereport.org/)
[![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-blue)](https://shadobaai.github.io/kafka-adapter-tests-reports/latest/)

Репозиторий хранит опубликованные HTML-отчёты тестирования проекта [1C: Адаптер Kafka](https://github.com/ShadobaAI/kafka-adapter). Отчёты доступны через GitHub Pages.

## Состав отчёта

Для каждого запуска release pipeline публикуются:

- [Allure UI](https://allurereport.org/) — результаты UI-тестов;
- [Allure Unit](https://allurereport.org/) — результаты unit-тестов;
- статический отчёт SonarQube.

Доступные отчёты публикуются независимо друг от друга, в том числе при аварийном завершении тестов. Для отсутствующего отчёта создаётся страница-заглушка со ссылкой на логи и артефакты запуска CI. Отсутствие отчёта не означает успешного прохождения тестов.

## Структура

- `latest/` — копии отчётов последнего опубликованного запуска;
- `<run_id>-<run_attempt>/` — отчёты конкретного запуска GitHub Actions.

Внутри каждого каталога запуска расположены:

- `allure-ui/`;
- `allure-unit/`;
- `sonar/`.

Примеры ссылок:

```text
https://shadobaai.github.io/kafka-adapter-tests-reports/<run_id>-<run_attempt>/allure-ui/
https://shadobaai.github.io/kafka-adapter-tests-reports/<run_id>-<run_attempt>/allure-unit/
https://shadobaai.github.io/kafka-adapter-tests-reports/<run_id>-<run_attempt>/sonar/
```

Последние опубликованные отчёты:

- [Все отчёты последнего опубликованного запуска](https://shadobaai.github.io/kafka-adapter-tests-reports/latest/).
- [Allure UI — интерфейсные тесты](https://shadobaai.github.io/kafka-adapter-tests-reports/latest/allure-ui/).
- [Allure Unit — модульные тесты](https://shadobaai.github.io/kafka-adapter-tests-reports/latest/allure-unit/).
- [SonarQube — статический анализ и покрытие](https://shadobaai.github.io/kafka-adapter-tests-reports/latest/sonar/).

## Публикация

Публикацию выполняет вызываемый workflow `Release / Publish Reports` из репозитория [`ShadobaAI/kafka-adapter`](https://github.com/ShadobaAI/kafka-adapter).

Workflow загружает артефакты `allure-ui-report`, `allure-unit-report` и `sonar-static-report`, затем:

1. Копирует доступные отчёты и заглушки для отсутствующих в каталог запуска и в `latest/`. Последний содержит результат последнего завершившего публикацию запуска.
2. Удаляет отчёты старых запусков, сохраняя последние 30.
3. Публикует изменения в ветку `main` этого репозитория.
4. Добавляет ссылки на отчёты в summary workflow и публикует Allure summaries.

Каталоги отчётов генерируются автоматически. Ручные изменения в них будут перезаписаны либо удалены при следующей публикации.

## GitHub Pages

Для репозитория должен быть включён GitHub Pages:

- source: deploy from a branch;
- branch: `main`;
- folder: `/ (root)`.

## Лицензия

Проект распространяется под лицензией [Apache License 2.0](LICENSE).
