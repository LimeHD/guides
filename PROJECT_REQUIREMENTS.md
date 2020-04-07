# Требования к проектам

1. [ ] Установить в проекте единый [пример .editorconfig](https://github.com/LimeHD/guides/blob/master/.editorconfig) [спецификация](https://editorconfig.org)


## Интеграция

1. [ ] Подключить проект к [Continuous Integration](CONTINUOUS_INTEGRATION.md). Два билда - master и pull requests.
2. [ ] Положить в README бейджик со статусом билда master, например – [![Build Status](https://ci.iptv2022.com/app/rest/builds/buildType(id:RecommenderMaster)/statusIcon)](https://ci.iptv2022.com/viewType.html?buildTypeId=RecommenderMaster)
3. [ ] Подключить проект к bugsnag
4. [ ] Включить интеграцию github -> pivotal

## Описание

1. [ ] Описание проекта на github
2. [ ] Написать [README](README_PRACTICES.md) для пользователей

## Backend

1. [ ] Подключить деплой через capistrano
1. [ ] Продумать мониторинг и добавить в zabbix после деплоя
2. [ ] Подключить аналитику influxdb
