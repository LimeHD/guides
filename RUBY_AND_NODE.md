# Подготовка к работе с ruby и nodejs

1. Предварительно устновите из под рута в систему часто требуемые пакеты из [списка](https://github.com/LimeHD/ansible/blob/master/ruby.yml#L10-L20)

2. Установка rbenv и ruby (https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-16-04)
   ```
   sudo apt-get install autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm3 libgdbm-dev
   git clone https://github.com/rbenv/rbenv.git ~/.rbenv
   ```
   Добавление rbenv в терминал:
      * Добавить нижеуказанный скрипт в profile используемой консоли (~/.bash_profile, ~/.zshrc, ~/.profile, or ~/.bashrc).
      <br/><br/>
      ```
      export PATH="$HOME/.rbenv/bin:$PATH"
      eval "$(rbenv init -)"
      ```
   Загрузка плагина ruby-build:
   ```
   git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
   ```
   Установить версию ruby из .ruby-version
   ```
   rbenv install "версия ruby"
   ```
   * Сделать ruby-версию версией по умолчанию (Опционально)
      <br/>
      ```
      rbenv global "версия ruby"
      ```

Если вы все настроили правильно, то при смене текущего каталога в shell, будет меняться версия руби на ту, которая указана в файле `.ruby-version`

```
> echo 2.7.0 > .ruby-version
> ruby -v
ruby 2.7.0
```

3. Также локально установите `nvm` (для справки: <br/>https://github.com/nvm-sh/nvm или https://digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04)
    <br/><br/>
    ```
    wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
    ```
    Добавление nvm в терминал:
    * Добавить нижеуказанный скрипт в profile используемой консоли (~/.bash_profile, ~/.zshrc, ~/.profile, or ~/.bashrc).
    <br/><br/>
    ```
    export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
    ```
    ***Далее: зайти в репозиторий***
    ```
    nvm install "версия из .nvmrc"
    nvm use
    ```

4. Установка yarn (рекомендуется)
   ```
   npm install -g yarn
   ```

5. Установка node-js-пакетов
   ```
   npm install
   ```
   или
   ```
   yarn install
   ```

6. Установка ruby gem'ов
   ```
   gem install bundler
   bundle install
   ```
