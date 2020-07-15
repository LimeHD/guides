# Стандарт кода для Android разработчиков.

## Стандарт для View объектов.

### Название id view в разметке xml.
1. Название id должно быть написано в snake_case нотации.
2. Название id должно начинаться с типа объекта. 
3. Название id не может содержать цифр и заглавных букв.

``` xml
 <RelativeLayout
        android:id="@+id/relative_layout_channel_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

 <LinearLayout
        android:id="@+id/linear_layout_root"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>
        
 <TextView
        android:id="@+id/text_view_information_text"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
```

### Имена View переменных

1. Имя переменной должно быть написано в camelCase нотации.
2. Имя переменной должно соответсвовать названию id.

``` java
private RelativeLayout relativeLayoutChannelView;

private LinearLayout linearLayoutRoot;

private TextView textViewInformationText;
```
