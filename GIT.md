# Работа с git-ом

* Загружаем свой публичный ключ (`~/.ssh/id_rsa.pub`) на github
* Используем [git succesful branching model](https://habr.com/ru/post/106912/) ([оригинал](https://nvie.com/posts/a-successful-git-branching-model/))
* Научиться работать с git-ом через консоль (`git rebase, git pull --rebase` и тп)
* Названия веток: `master`, `develop`, `feature/*`, `fix/*`
* [Пример](https://github.com/dapi/dotfiles/blob/master/gitconfig) глобальных настроек для git-а
* [git flow](https://danielkummer.github.io/git-flow-cheatsheet/index.ru_RU.html) (опционально, +1 в карму)

# Наименование git-сообщения

1. `commit message` это НЕ комментарий. Это сообщение, как в чате. Прогарммисты читают commit history как переписку.
2. commit что-то делает с кодом. Нужно писать что это комит сделает с кодом, когда я его волью.
3. Номер задачи указывается в конце сообщения через квадратные скобки `[#123]`. Номер задачи берётся из пивотала.
4. С заглавной буквы, как правило начинается с глагода.

# Настройка shell для отображения текущей ветки и состояния git-а 

* [bash + git](https://askubuntu.com/questions/730754/how-do-i-show-the-git-branch-with-colours-in-bash-prompt)
