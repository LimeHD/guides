## Преднастройка Базы Данных (Mysql, https://www.digitalocean.com/community/tutorials/mysql-ru)
   ```
   sudo apt-get install mysql-server
   sudo apt install libmysqlclient-dev
   sudo mysql -u root -p
   Пароль root-юзера
   ```
   В консоли mysql:
   ```
   CREATE USER 'newuser'@'localhost' IDENTIFIED BY '';
   GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
   FLUSH PRIVILEGES;
   QUIT;
   ```
   * Если не даёт создать пользователя без пароля:
   <br/><br/>
   ```
   UNINSTALL PLUGIN validate_password;
   SET PASSWORD FOR username@localhost = PASSWORD('');
   FLUSH PRIVILEGES;
   ```

## Создание Базы Данных проекта
   ```
   bundle exec rake db:create
   ```
   (может пригодиться pull)
   ```
   bundle exec cap production db:pull
   ```
