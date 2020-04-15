# Гайды по разработке

## Стандарты

* https://semver.org
* https://12factor.net/ru/

## Рабочее окружение

* Установлен и настроен `direnv`
* Созданы и опубликованы ключи доступа (на github и на сервера)
* Настроен `ssh-agent`
* `gem install semver`
* Настроены `rbenv`, `nvm`, [`goenv`](https://github.com/syndbg/goenv)

# Best practices

* Не использовать относительный пути в зависимостях: `'import { LOCALES } from "./../../../constants/Translation'`. С ними сложно менять организацию файлов.


# Аттестация

* [Карта компетенций](https://docs.google.com/spreadsheets/d/1Tn6utgODiPzc0Z6y_llOYFuxs-kAnD00roAnPkPL2Kc/edit?usp=sharing)

# Impact Mapping

Видео и пост от Александа Бындю

* https://www.youtube.com/watch?v=Gk0Uw93KtFA
* https://habr.com/ru/post/246401/
* https://www.ozon.ru/context/detail/id/141368820/

# Полезные ссылки

* https://makefile.site

# Общие положения, инженерная культура, ментальная модель

Кидаю доклад  Ментальное программирование Кирила Мокевнина. Никаких формул и кодов, смотреть можно на скорости 1.2/1.5. Важно чтобы в течении недели посмотрели все, для того чтобы мы с вами были в одном контекстном поле.

В видосе Кирил представится на момент записи, но сейчас он автор и владелец hexlet онлайн-платформы по обучению программистов,  впрошлом году компанию оценили в 20 млн$. Отличие hexlet-а от других онлайн курсов в том, что он делает именно инженера-программиста, а не просто человека знающего какой-то язык и фреймворк.

Его опыт создания команд разработки самый мощный на рынке, за такой период никто не создавал более крутых команд работающих с проектами такой сложности за такое ограниченное время. К сожалению в прошлом году он из Улска свалил в Калифорнию. Я работал совместно с ним в 2012-2013, и коллективы строил и строю по принципам рожденным именно в его компании. 

* Первая часть (2013  год) https://www.youtube.com/watch?v=EEq1wdM2M2w - 1 час. Есть второй вариант первой части, пардон но я уже не помню чем они отличаются -  https://www.youtube.com/watch?v=eEEHWQNuCLQ
* Вторая часть (2018 год) https://www.youtube.com/watch?v=vkUTX1hruF8 - 1 час.

Включаю этот видос в обязательную программу для всех входяших в наш коллектив разрабов.

* [Инженерная культура](https://www.youtube.com/watch?v=W7GlELjRODw)

## Литература

* [Бизнес с нуля](https://www.litres.ru/erik-ris/biznes-s-nulya-metod-lean-startup-dlya-bystrogo-testirovaniya-ide/)
* [ReWork](https://www.mann-ivanov-ferber.ru/books/luchiernoctar/rework1/)
* [Практика дао Toyota. Руководство по внедрению принципов менеджмента Toyota](https://www.ozon.ru/context/detail/id/142621871/)

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
