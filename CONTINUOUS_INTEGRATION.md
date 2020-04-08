# Continuous Integration

* [ci.iptv2022.com (TeamCity)](https://ci.iptv2022.com)

## Подключение проекта в teamcity

1. Создаем под-проект (Create subproject) в одном из основных веток (Android, iOS, Backend & Web)
2. Выбираем ручное (Manual) создание, вместо `From GitHub.com`, потому что если выбирать из github, то vcs устнавливается через логин/пароль и `https://` вместо доступа по ssh-ключу `git@`. Это необходимо для git hook-ов.


[Видео-инструкция](https://yadi.sk/i/bYwPSYRCKtN9ww)
