﻿## Урок 5. Лекция. Углубляемся в контроль версий. Ильнар Шафигулин

1. Создали аккаунт на Github.com
2. Создали локальный репозиторий: создали папку, git init, создали файл -- чтобы был хотя бы один commit -- лучше сразу `.gitignore`.
3. "Подружить" локальный и удаленный репозитории. GitHub при создании нового репозитория подскажет как это можно сделать.
4. Отправить (push) локальный репозиторий в удалённый (на GitHub). При этом возможно нужно будет авторизоваться на удалённом репозитории. Достаточно один раз.
5. Провести изменения "с другого компьютера". В качестве другого компьютера можно сделать непосредственно на GitHub
6. Выкачать (pull) актуальное состояние из удаленного репозитория.

Этих действий достаточно, чтобы настроить совместную работу над репозиторием

---

`13:00` Нажимаем зеленую кнопку `Code` и копируем адрес HTTPS

SVN - Система Контроля Версий

`13:50` Вставляем в терминале скопированную из GitHub ссылку после команды git clone
```sh
git clone https://github.com/magus1968/e-books.git
```
После этого Git скопирует репозиторий с сервиса GitHub в наш локальный репозиторий. 
```sh
! Но перед этим вызовем git status # убедиться, что у нас тут не настроен Git
```
`16:00` По завершении копирования заходим в папку со скопированным репозиторием с помощью команды `cd`

`17:00` C помощью`git status` -- проверяем, что в папке с клонированным репозиторием всё в порядке

`18:15` `git log` -- можем посмотреть какие были изменения

`18:45` `git log --graph` -- какие есть ветки и как происходила работа
```sh
Все остальные действия происходят локально.
Никоем образом с версией на GitHub наши действия не связаны.
```


---

group_903 - это какой-то проект на GitHub аккаунте Ильнара

1. Делаем форк (fork) интересующего нас репозитория
2. Делаем git clone для нашей версии этого репозитория
3. Создаем ветку с предлагаемыми изменениями
4. Производим все изменения только в этой ветке
5. Отправляем эти изменения на свой аккаунт (push), причем git подскажет, что нужно отправить git push --set-upstream origin description: copy-past
6. В окне на GitHub появляется возможность отправить pull request

**ИДЕЯ**: можно таким образом *попробовать* вести версионность, например, ФИНаналитики

---

## Урок 6. Семинар. Работа с удалёнными репозиториями

`27:50` На удаленном репозитории GitHub ветка *new_branch* не удалилась. Она у нас не используется, т.к. мы уже произвели слияние этой ветки с *main*. Можно через браузер эту ветку удалить. Выбрать в раскрывающемся списке main `View all branches` и нажать на корзину для *new_branch*.

`28:20` Можно это же удаление сделать с помощью команды в локальном репозитории:
```sh
git push origin --delite new_branch
```

### Разрешаем конфликт

`29:54` Заходим в GitHub, вибираем файл и через редактирование (значек карандаша) добавляем текст.

По окончании редактирования нажимаем `Commit changes...`, добавляем коммит и подтверждаем изменения.

`30:20` Локально: вносим изменения в тот же файл, который только что редактировали на GitHub -- то есть добавили **локальный конфликт**

После второго добавления текста в GitHub -- добавляем текст в локальный файл. Разрешаем конфликт локальный

`31:05` Пробуем отправить локальные изменения на удаленный сервер GitHub привычным `git push` и получаем сообщение:
```sh
[rejected] --> отказано
```
Мы не можем вытолкнуть текущие изменения.
```sh
! Перед тем как внести какие-то локальные изменения <— нужно сначала забрать то что есть на сервере.
```

ОК, разруливаем ситуацию. Перед тем как отправить изменения на сервер, мы должны выполнить команду
```sh
git pull --rebase
```
Ключ `--rebase` говорит о том, что мы скачиваем репозиторий с сервера, а все наши локальные изменения потом туда пытаемся слить. Таким образом git pull произведет выкачку с сервера и слияние (Auto-merging) с нашими текущими изменениями.

Получаем сообщение, что при Auto-merging произошел CONFLICT. Мы не можем наши текущие изменения слить вместе с удаленным текстом.

`32:40` Открываем VSCode и смотрим что происходит. Видим обычный merge, только с удалённым репозиторием. Перед тем как произвести слияние -- `мы должны выбрать какую-то одну из версий`, которую хотим принять.

В VSCode можем: принять текущие изменения `Accept Current Change`, принять входящие изменения `Accept Incoming Change`, принять оба `Accept Both Change`, сравнить `Compare Change`.

А можно отредактировать вручную и сохранить как обычно. Дальше смотрим git status и видим, что у нас был конфликт
```sh
interactive rebase in progress; onto 36ecbbb
. . .
both modified:   README.md
```
Теперь наш файл нужно добавить и закоммитить... *Но Денис Enter не нажал, а я нажал и расхлебывал последствия уже самостоятельно*. Поэтому совет мне: `попробуй без правки вручную` и:
```sh
! Пользуйся кнопкой Resolve Editor
```
`34:20` Заходим в GitHub (браузер). Снова редактирум файл. После этого вносим изменения в локальный файл. Сохраняем локальный, коммитим. Видим снова `[rejected]`. Выполняем уже известный `git pull --rebase`. Редактируем вручную файл в VSCode, сохраняем, git status, git add, git status и видим подсказку, что для продолжения rebase нужно ввести:
```sh
git rebase --continue
```
Что-то этот полезный ключик конечно сделал. Но только текст сохранился не полностью. Лан, разберёмся. 






## Полезно

### # Удалить репозиторий через GitHub
— Eдинственный нормальный способ удаления GitHub-репозиториев делается через профиль: нужно зайти на сайт, нажать кнопку «Удалить» и подтвердить удаление [ссылка](https://skillbox.ru/media/code/kak-v-github-udalit-i-vosstanovit-repozitoriy/) на источник

#### 1. Находим репозиторий

Все созданные проекты расположены слева. Или нажав кнопку `Show more` перейти на вкладку `Your repositories`

#### 2. Переходим в настройки репозитория
Открываем вкладку `Settings` –> пролистываем вниз до раздела `Danger Zone` –> нажимаем кнопку `Delete this repository`

#### 3. Подтверждаем удаление

Появляется окно с подтверждением действия и `поле для ввода`, в котором нужно ввести полное название репозитория — имя вашего аккаунта и проекта. Например, `DavisWalkers/my_first_repo`

После этого становится доступной кнопка окончательного удаления `I understand the consequences, delete this repository`. Жмем –> нас перебрасывает в профиль –> появляется уведомление об успешном удалении репозитория. 
```sh
Your repository "DavisWalkers/my_first_repo" was successfully deleted
```
`Done`

---

>? Остался вопрос: как удалить файл из GitHub ?

*У меня один русскоязычный файл (книга .pdf) локально удалён, а на GitHub почему-то остался -- не смотря на то, что корзину в GitHub на файле тоже нажимал. Найти и разобраться.*

### # Обновить Git



### # Устранить проблемы с кирилизацией
После выполнения этой команды, при вызове git status получите нормальное имя файла на русском языке, а не что-то такое в формате nnn nnn



### # Как переименовать аккаунт: локально в Git и на GitHub ?
