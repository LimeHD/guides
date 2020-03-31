# Гайды по разработке

## Стандарты

* https://semver.org
* https://12factor.net/ru/

## Работа с git-ом

* Загружаем свой публичный ключ (`~/.ssh/id_rsa.pub`) на github
* Используем [git succesful branching model](https://habr.com/ru/post/106912/) ([оригинал](https://nvie.com/posts/a-successful-git-branching-model/))
* Научиться работать с git-ом через консоль (`git rebase, git pull --rebase` и тп)
* Названия веток: `master`, `develop`, `feature/*`, `fix/*`
* [Пример](https://github.com/dapi/dotfiles/blob/master/gitconfig) глобальных настроек для git-а
* [git flow](https://danielkummer.github.io/git-flow-cheatsheet/index.ru_RU.html) (опционально, +1 в карму)

### Наименование git-сообщения

1. `commit message` это НЕ комментарий. Это сообщение, как в чате. Прогарммисты читают commit history как переписку.
2. commit что-то делает с кодом. Нужно писать что это комит сделает с кодом, когда я его волью.
3. Номер задачи указывается в конце сообщения через квадратные скобки `[#123]`
4. С заглавной буквы, как правило начинается с глагода.

### Настройка shell для отображения текущей ветки и состояния git-а 

* [bash + git](https://askubuntu.com/questions/730754/how-do-i-show-the-git-branch-with-colours-in-bash-prompt)

# Best practices

* Не использовать относительный пути в зависимостях: `'import { LOCALES } from "./../../../constants/Translation'`. С ними сложно менять организацию файлов.
* https://makefile.site

# Аттестация

* [Карта компетенций](https://docs.google.com/spreadsheets/d/1Tn6utgODiPzc0Z6y_llOYFuxs-kAnD00roAnPkPL2Kc/edit?usp=sharing)

# Impact Mapping

Видео и пост от Александа Бындю

* https://www.youtube.com/watch?v=Gk0Uw93KtFA
* https://habr.com/ru/post/246401/
* https://www.ozon.ru/context/detail/id/141368820/

# Общие положения, инженерная культура, ментальная модель

Кидаю доклад  Ментальное программирование Кирила Мокевнина. Никаких формул и кодов, смотреть можно на скорости 1.2/1.5. Важно чтобы в течении недели посмотрели все, для того чтобы мы с вами были в одном контекстном поле.

В видосе Кирил представится на момент записи, но сейчас он автор и владелец hexlet онлайн-платформы по обучению программистов,  впрошлом году компанию оценили в 20 млн$. Отличие hexlet-а от других онлайн курсов в том, что он делает именно инженера-программиста, а не просто человека знающего какой-то язык и фреймворк.

Его опыт создания команд разработки самый мощный на рынке, за такой период никто не создавал более крутых команд работающих с проектами такой сложности за такое ограниченное время. К сожалению в прошлом году он из Улска свалил в Калифорнию. Я работал совместно с ним в 2012-2013, и коллективы строил и строю по принципам рожденным именно в его компании. 

* Первая часть (2013  год) https://www.youtube.com/watch?v=EEq1wdM2M2w - 1 час. Есть второй вариант первой части, пардон но я уже не помню чем они отличаются -  https://www.youtube.com/watch?v=eEEHWQNuCLQ
* Вторая часть (2018 год) https://www.youtube.com/watch?v=vkUTX1hruF8 - 1 час.

Включаю этот видос в обязательную программу для всех входяших в наш коллектив разрабов.

* [Инженерная культура](https://www.youtube.com/watch?v=W7GlELjRODw)

## Мониторинг

* http://zabbix.iptv2022.com
* [teamcity](https://ci.iptv2022.com)

## Литература

* [Бизнес с нуля](https://www.litres.ru/erik-ris/biznes-s-nulya-metod-lean-startup-dlya-bystrogo-testirovaniya-ide/)
* [ReWork](https://www.mann-ivanov-ferber.ru/books/luchiernoctar/rework1/)
* [Практика дао Toyota. Руководство по внедрению принципов менеджмента Toyota](https://www.ozon.ru/context/detail/id/142621871/)

# Continuous Integration

## Подключение проекта в teamcity

1. Создаем под-проект (Create subproject) в одном из основных веток (Android, iOS, Backend & Web)
2. Выбираем ручное (Manual) создание, вместо `From GitHub.com`, потому что если выбирать из github, то vcs устнавливается через логин/пароль и `https://` вместо доступа по ssh-ключу `git@`. Это необходимо для git hook-ов.

### Maintainers

<table>
<tr>
<td align="center">
<img src="https://avatars1.githubusercontent.com/u/31139?s=460&v=4" width="100px;" alt=""/>
<br /><sub><b>dapi</b></sub></a><br />
</td>
<td align="center">
<img src="https://avatars1.githubusercontent.com/u/23422968?s=460&u=668229465690637b50f6581df0fa9918d7fb6c1e&v=4" width="100px;" alt=""/>
<br /><sub><b>zikwall</b></sub></a><br />
</td>
</tr>
</table>
