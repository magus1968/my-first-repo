# Инструкция для работы с Markdown
*Это в рамках факультативного курса на GeekBrains "Введение в контроль версий"*\
А воообще рекомендую ознакомиться с [GitHub docs](https://docs-github-com.translate.goog/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax?_x_tr_sl=en&_x_tr_tl=ru&_x_tr_hl=ru&_x_tr_pto=rq&_x_tr_hist=true) - понятно и профессионально.

## Выделение текста

*Курсив* : Чтобы выделить текст курсивом необходимо обрамить его звездочками ( * ) или знаком нижнего подчеркивания ( _ ). Например, *вот так* или _вот так_.

**Полужирный** : Чтобы выделить текст полужирным, необходимо обрамить его двойными звездочками (**) или двойные знаки нижнего подчеркивания ( __ ). Например **вот так** или __вот так__.

Альтернативные способы выделения текста жирным или курсивом нужны для того, чтобы мы могли совмещать оба этих способа. Например, _текст может быть выделен курсивом и при этом быть **полужирным**_.

## Списки

Чтобы добавить ненумерованные списки, необходимо пункты выделить звездочкой [ * ] или знаком [ + ]. Например, вот так:
* Элемент 1
* Элемент 2
+ Элемент 3
+ Элемент 4

Чтобы добавить нумерованные списки, необходимо пункты просто пронумеровать. Например, вот так:
1. Первый пункт
2. Второй пункт

## Цититирование

> Первый уровень
>> Второй уровень

## WEB cсылки

Git для новичков [часть 1](https://habr.com/ru/articles/541258/ "Хабр")

Git для новичков [часть 2](https://habr.com/ru/articles/542616/ "Хабр") в кавычках через пробел после ссылки до закрывающей скобки можно вставить "Всплывающую подсказку"

[Git на Attlassian. Настройка репозитория](https://www.atlassian.com/ru/git/tutorials/setting-up-a-repository "Attlassian")


## Работа с изображениями

Чтобы вставить изображение:

! вначале поставить восклицательный знак, далее:\
в [ ] указывается текст - на случай, если изображение не загрузится\
в ( ) указывается имя файла из которого это изображение необходимо "достать".\
Изображение должно лежать в той же папке, что и файл .md

![Тут изображение котика](cat.png "Изображение котика")

## Работа с таблицами
Смотреть в файле `instruction.md` у Дениса Гуляева в репозитории version_control

## Убрать под спойлер
<details>
  Вот так можно убрать под спойлер.
  
  А, как убрать под спойлер, чтобы вместо "Сведения" выводился текст?
</details>

<details>
  <summary><strong>Допустим это заголовок спойлера</strong></summary>
  А вот так

  Смотри на GitUub docs [Organizing information with collapsed sections](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-collapsed-sections)
</details>

<details>
  <summary><strong>А это мой первый pull request</strong></summary>
  Вложил на память и как пример возможности убрать под спойлер изображение
  
  ![А это мой первый pull request](first_pull_request.png "Первый pull request")

</details>
