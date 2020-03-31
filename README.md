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

## Наименование git сообщения

1. `commit message` это НЕ комментарий. Это сообщение, как в чате. Прогарммисты читают commit history как переписку.
2. commit что-то делает с кодом. Нужно писать что это комит сделает с кодом, когда я его волью.
3. Номер задачи указывается в конце сообщения через квадратные скобки `[#123]`
4. С заглавной буквы, как правило начинается с глагода.

## git + bash (show branch name)

* https://askubuntu.com/questions/730754/how-do-i-show-the-git-branch-with-colours-in-bash-prompt

## Работа с ssh-agent

0. В примерах используется редактор `mcedit`, вы можете использовать любой какой пожелаете.
1. Проверяем конфигурацию ssh: `mcedit ~/.ssh/config` и настраиваем конфигурацию следующим образом:
    ```shell script
    Host *
    ForwardAgent Yes
    ```
    * Так же можно настроить глобально (не обязательно):  `mcedit /etc/ssh/ssh_config` - раскомментировать необходимые строки как выше
2. Проверяем наличие ssh keys: `ssh-add -l` & `ssh-add -L`
    * Вы должны узреть нечто следующее:
    ```shell script
    // 1
   2048 SHA256:ZpgJVijAqVzEGX4WrGSfhXlx0iVgWcwYe26lQY12RnY /home/user/.ssh/id_rsa (RSA)
   
    // 2
   ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCz3h/.../dwkRqDhNLtBs7ZJY/SI9i/5hRXF/home/user/.ssh/id_rsa
    ```
    * Если ключей нет генерируем новые:  `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` все пункты по-дефолту
    * Добавляем в настройки github аккаунта сгенерированный публичный ключ из: `~/.ssh/id_rsa.pub` по адресу: `https://github.com/settings/keys`
    * Чтобы посмотреть ключ воспользуйтесь командой: `cat ~/.ssh/id_rsa.pub`
3. Запустите ssh-agent в фоновом режиме: `eval "$(ssh-agent -s)"`
    * Вы увидите примерно следуещее: `> Agent pid 59566`
4. Добавьте свой закрытый ключ SSH в ssh-agent: `ssh-add` можно так же добавлять определенный ключ, например: `ssh-add ~/.ssh/id_rsa`
5. Выполняем второй пункт еще раз.
6. Коннектимся к удаленному серверу и выполняем команды из второго пункта.
7. Если 6 пункт успешен (т.е. результат как на 2 пункте) вы можете провести тестовый git clone проекта.

#### Troubleshooting

Если у вас ничего не работает, могут возникнуть некоторые проблемы с правами, это не так очевидно. Для SSH права доступа к файлу могут быть слишком открыты. Проверьте: `cd ~/.ssh && ls -ls`
```shell script
// как примерно должены выглядеть правильные права, а не 777 : -rwxrwxrwx

4 -rw------- 1 root root  394 мар 23 11:37 authorized_keys
4 -rw------- 1 root root 1679 мая 17  2019 id_rsa
4 -rw-r--r-- 1 root root  394 мая 17  2019 id_rsa.pub
4 -rw-r--r-- 1 root root 3104 мар 23 13:03 known_hosts
```
Закрытый ключ должен иметь права на чтение и запись только для пользователя и другие разрешения для группы и других.

`chmod 600 ~/.ssh/id_rsa`

Аналогично, открытый ключ не должен иметь права на запись и выполнение для группы и других.

`chmod 644 ~/.ssh/id_rsa.pub`

Это исправление должно помочь исправить ошибку: Permission denied (publickey) в ssh.

#### PS

Для переброски по цепочке нужно на каждом узле активировать forwarding.

## Настрйока безпарольного доступа к серверам

Генерируем ключи:

1. `ssh-keygen`
    * После ввода этой команды вы должны увидеть следующий вывод:
    ```shell script
    enerating public/private rsa key pair.
    Enter file in which to save the key (/home/user/.ssh/id_rsa):
    ```
    * Если ранее вы уже генерировали пару SSH ключей, вы можете увидеть следующий вывод:
    ```shell script
    /home/user/.ssh/id_rsa already exists.
    Overwrite (y/n)?
    ```
    * Если вы выберете перезаписать ключи на диск, вы **не сможете** использовать старые ключи для аутентификации. 
2. Копирование публичного ключа на сервер: 
    `cat ~/.ssh/id_rsa.pub | ssh user@host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"`
    * Здесь создается диреткория `~/.ssh`, если она не существует
    
#### PS
 
Вы можете копировать не только ключи, хранящиеся в id_rsa.pub, но и в других файлах.
Поздравляем у вас настроен вход по ключам SSH, позволяющий заходить на сервер без использования пароля.


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
