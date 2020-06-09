## Стили :art:
  ![BOOTSTRAP SASS](https://marioaraque.com/sites/default/files/styles/large/public/field/image/bootstrap-sass.png?itok=Dquizsd9)
  * Стили сайта стоят на двух столпах - [SCSS или SASS](https://sass-scss.ru/) и [Bootstrap-4](https://getbootstrap.com/docs/4.5/).
  * Папка settings - для общих стилей, components для отдельных страниц и компонентов.
  * Bootstrap выступает в качестве основы верстки сайта и дополнительного инструмента для ускорения написания стилей в SCSS.
  * В шаблонах используются Bootstrap компоненты. Классы bootstrap задаются в нужных местах (чаще всего без использования тэгов). Например:<br>
      ```
       .navbar
          'содержимое с новой строки'
      ```
  * Если элемент пользуется Bootstrap классом, как своеобразным конструктором, и, при этом, кастомизирует его, то сначала в верстке должен идти bootstrap класс, затем собственный стиль.
  * Использовать @extend 'Bootstrap стиль' в SCSS только в случае, если он не описывает элемент, например: ```.p-1, .m-1``` - конкретно эти вообще лучше описывать нормальными padding и margin,<br> классы вроде '.navbar' должны быть в slim файлах.
  * Стили - самая важная часть сайта. Максимально стараться избегать JavaScript, пользоваться классами и mixin'ами Bootstrap.
  * При рефакторинге выносить повторяющиеся стили в [placeholder'ы](https://sass-lang.com/documentation/style-rules/placeholder-selectors) SCSS, повторяющуюся логику стилей в [mixin'ы](https://sass-lang.com/documentation/at-rules/mixin) SCSS, повторяющиеся значения в переменные (в settings, чтобы доступ был во всех компонентах SCSS).
  * Использовать [@media](https://developer.mozilla.org/ru/docs/Web/CSS/@media) и [@include media-breakpoint-{} ()](https://getbootstrap.com/docs/4.1/layout/overview/) для управления стилями на экранах с разной шириной.
  * Стили для устройств с touch screen отделяются навешиванием на body классом device--touch и находятся в components/_device--touch.scss.
  * Названия собственных стилей пишутся по стандарту [БЭМ](https://ru.wikipedia.org/wiki/%D0%91%D0%AD%D0%9C).<br>Благодаря этому систематизируется всё в проекте ```.{название slim компонента}__{класс}```.<br>Названия файлов SCSS в styles/components также дублируют конкретные slim компоненты. :copyright:
