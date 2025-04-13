﻿## Урок 5. Лекция. Углубляемся в контроль версий. Ильнар Шафигулин

1. Создали аккаунт на Github.com
2. Создали локальный репозиторий: создали папку, git init, создали файл -- чтобы был хотя бы один commit -- лучше сразу `.gitignore`.
3. "Подружить" локальный и удаленный репозитории. GitHub при создании нового репозитория подскажет как это можно сделать.
4. Отправить (push) локальный репозиторий в удалённый (на GitHub). При этом возможно нужно будет авторизоваться на удалённом репозитории. Достаточно один раз.
5. Провести изменения "с другого компьютера". В качестве другого компьютера можно сделать непосредственно на GitHub
6. Выкачать (pull) актуальное состояние из удаленного репозитория.

Этих действий достаточно, чтобы настроить совместную работу над репозиторием

---

### 5.1 Клонировать репозиторий с GitHub

`13:00` Нажимаем зеленую кнопку `Code` и копируем адрес HTTPS

SVN - Система Контроля Версий

`13:50` Вставляем в локальном терминале скопированную из GitHub ссылку после команды git clone
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

### 5.2 Отправить локальный репозиторий в GitHub
Вариант `...or push an existing repository from the command line`

`20:45` Локально: создаем в новой папке новый репозиторий и файл в нём

`22:20` На GitUub: создаем репозиторий выбрав через [+] `New repository`. Задаем имя и жмем `Create repository`. GitHub предлагает три варианта что можно сделать, чтобы с созданным репозиторием можно начать работать.

`23:45` Поскольку у нас уже создан новый локальный репозиторий, выбираем второй вариант `...or push an existing repository from the command line`
```sh
git remote add origin <ссылка> # ссылка на созданный репозиторий в GitHub
git branch -M main
git push -u origin main
``` 
`25:50` Копируем первую строку и вводим в наш локальный терминал
```sh
git remote add origin https://github.com/magus1968/e-books.git
# Связали локальный репозиторий с репозиторием на GitHub
```
`26:15` Вторая строка укажет какая ветка является у нас основной
```sh
git branch -M main
# Переименовываем ветку master в main т.к. в GitHub название основной ветки main
```
`26:25` Третья направит в GitHub наш репозиторий
```sh
git push -u origin main
```
`27:50` Обновляем страницу в браузере и видим что в репозитории на GitHub появился созданный локально наш файл

`32:05` Работаем локально, вносим какие-то изменения. Поскольку мы уже привязали удалённый репозиторий к нашему локальному <--> т.е. Git подружился между двумя репозиториями, делаем:
```sh
git push
# Отправляем в GitHub сделанные локально изменения
```
```sh
! Инсайт ! В этом варианте: название созданной локальной папки не совпадает
с названием созданного репозитория на GitHub. И видимо не обязано :)
```
`33:10` Изменяем файл напрямую в GitHub, нажав на карашдаш `Edit this file`

`33:35` Перед сохранением добавляем в GitHub commit и жмем кнопку `Commit change`

`34:25` Историю версий на GitHub можем посмотреть нажав на `Commits` в репозитории или на `History` в файле. Также можем переключаться между ветками.
```sh
Initial commit # Так принято идентифицировать первый коммит
```
`35:20` Чтобы получить изменения с GitHub на локальный компьютер, нужно взять актуальную версию с GitHub -- синхронизировать локальный репозиторий с удалённым:
```sh
git pull
```
`35:35` Важно: `git pull` является составной командой: она не только подгрузит все изменения, но и попытается *смёржить* наши ветки: сделать merge состояния, которое было на GitHub с состоянием которое у нас происходит локально.

---

### 5.3 Совместная работа над проектом (fork, pull request)

1. Делаем копию `fork` интересующего нас репозитория себе в GitHub
2. Создаем локальный репозиторий: через git clone берем из созданной копии на GitHub в свой локальный компьютер
3. Создаем ветку для изменений, которые хотим предложить
4. Производим все изменения только в этой ветке
5. Отправляем эти изменения на свой аккаунт в GitHub (push), причем git подскажет, что нужно отправить `git push --set-upstream origin description`
6. На GitHub появляется возможность отправить pull request: выбрав нашу ветку появляется кнопка `Contribute`, в которой жмём `Open pull request`

---

`44:00` Находим репозиторий на GitHub

`45:10` Если мы хотим поучаствовать в чьем-то проекте на GitHub, то вначале должны сделать отдельную копию этого репозитория с помощью кнопки
```sh
Fork
# Делаем в GutHub отдельную полную копию "чужого" репозитория на своём аккаунте
```

`45:40` У нас появляется точно такой же репозиторий, только уже на своём аккаунте

`45:55` С этой копией репозитория уже можем делать всё, что нам заблагорассудится. У нас есть к нему полный доступ, как-будто мы сами его создали

`46:30` С нашего аккаунта этот репозиторий уже можем забрать: копируем ссылку на репозиторий уже с нашего аккаунта и клонируем репозиторий уже в нашу локальную папку

`48:20` На GitHub принято, чтобы у каждого проекта был файл README c описанием проекта
```sh
Когда мы хотим предложить внести изменения в чей-то проект -
- это всегда делается в отдельной ветке
```

`48:35` Создаем отдельную ветку -- в которой создаем файл со своим предложением. Сохраням и коммитим как обычно.

`51:45` Сделанное отправляем в наш репозиторий на GitHub - Git подсказывает, что вместо `git push` нужно набрать
```sh
git push --set-upstream origin description
# потому что отправляем из соседней (новой) ветки
```
Копируем - вставляем - отправляем.

`52:15` Обновляем браузер: в списке веток появляется наша новая ветка и главное - появляется новая кнопка
```sh
Compare & pull request
# Сравни и отправь запрос на вливание того что сделали в основной (форкнутый) репозиторий
```

ПРИМЕЧАНИЕ: в настоящей версии этой кнопки уже нет. Появляются две кнопки `Contribute` и `Sync fork`. Причем команда (кнопка) `Open pull request` появляется только в новой ветке, в которой мы сформировали файл со своим предложением.

`53:00` Из нашей новой ветки нажимаем `Open pull request`. GitHup анализирует то что мы сделали и выдает сообщение `Able to merge` - о возможности слить то что сделали мы с тем что есть в основном (форкнутом) репозитории.

`53:25` Добавляем описание нашего предложения для владельца форкнутого репозитория.

`53:40` Нажимаем `Create pull request` чтобы отправить pull request в аккаунт владельца исходного репозитория.

Владелец посмотрит наше предложение и если они его устроят, он может влить нашу ветку в свой основной репозиторий

---

## Урок 6. Семинар. Работа с удалёнными репозиториями. Денис Гуляев

### 6.1 Клонируем репозиторий с GitUub (нюансы от Дениса)

`03:40` Репозиторий с GitHub можно в принципе просто скопировать: `Code` -> `Download ZIP`

`04:00` Мы сделаем грамотно: скопируем ссылку `HTTPS` и клонируем себе на компьютер (как в Уроке 5)
```sh
git clone https://github.com/gulden-geekbrains/version_control.git
```

`04:40` Отображаем листинг текущей директории с помощью команды `ls` или `dir` (Windows) -> видим, что у нас появилась папка, имя которой совпадает с именем репозитория на GitHub -> переходим в эту папку с помощью `cd` -> `git status` отобразит статус текущего репозитория: находимся на основной ветке `main`; ветка обновлена `up to date`; появляется слово `origin` - по умолчанию синоним удалённого репозитория, который мы склонировали.

`06:05` Смотрим какие были в нём коммиты
```sh
git log --oneline
git log --ontline --graph # Визуализируем ветки и их слияния
```

### 6.2 Создаем репозиторий на GitHub. Связываем с локальным
Вариант `...or create a new repository on the command line`

`08:05` Создаем репозиторий на GitHub: на вкладке `Repositories` -> кнопка `New` -> задаем имя репозитория в поле `Repository name *` -> оставляем параметр `Public` -> нажимаем `Create repository`

`08:40` Поскольку предварительно не создавали локальный репозиторий как в уроке 5, используем подсказки по первому варианту
```sh
echo "# test_repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/magus1968/test_repo.git
git push -u origin main
```
`09:00` В локальной консоли (терминале) переходим на уровень выше с помощью `cd ..` -> создаем папку `mkdir <имя_папки>`, где имя_папки как у имени созданного репозитория на GitHub -> переходим в созданную папку `cd <имя_папки>/` -> следуем инструкции

`09:30` Создаем файл README.md
```sh
echo "# test_repo" >> README.md
```
Открываем VSCode, чтобы было видно что там происходит -> вносим изменения в созданный README.md -> не забываем сохранять `Ctrl + S`

`10:20` Смотрим подсказку GitHub: далее необходимо инициализировать локальный репозиторий
```sh
git init
git add README.md
git commit -m "first commit"
```
`git status` - видим, что есть один непроиндексированный файл README.md -> добавляем к индексации `git add` -> `git status` - видим, что файл добавили к индексации (стал зеленым) -> коммитим `git commit -m "Initial commit"`

`11:15` Следующим шагом: GitHub предлагает переименовать локальную основную ветку `master` в `main` -> переименовываем
```sh
git branch -M main
```

`11:45` Связываем локальный репозиторий с репозиторием на GitHub
```sh
git remote add origin https://github.com/magus1968/test_repo.git
```

`12:30` Проверяем в консоли созданную связку
```sh
git remote show
# Покажет, что origin репозиторий задан - ОК
```

`13:25` По необходимости, вносим изменения в README.md (с последующим сохранением, индексацией и коммитом)

`14:15` Отправляем наш локальный репозиторий -> в репозиторий на GitHub
```sh
git push -u origin main
# Вытолкнуть все изменения в удаленный репозиторий origin в ветку main
```

`16:40` Убедимся, что у нас **привязан** удаленный репозиторий `origin` и посмотрим **как** он привязан 
```sh
git remote -v
```
Увидим
```sh
origin  https://github.com/magus1968/test_repo.git (fetch)
# fetch - репозиторий, который соответствует для считывания
origin  https://github.com/magus1968/test_repo.git (push)
# push - репозиторий, который соответствует для записи
```
`17:30` Более подробную информацию об удаленном репозитории вызываем с помощью
```sh
git remote show origin
```
`18:00` Переходим в браузер: отредактируем README.md в GitHub. Жмем на `[карандаш]` -> редактируем -> по завершении жмем `Commit changes...` -> коммитим в поле `Commit message` -> проверяем, что отмечена ветка `main` -> подтверждаем нажав `Commit changes`

`19:00` Чтобы произведенные на GitHub изменения появились в локальном репозитории - запрашиваем в консоли изменения с сервера
```sh
git pull
```
`19:55` C помощью `git log` посмотрим количество коммитов; кто автор коммитов; что голова `HEAD` указывает на ветку `main` и удаленный репозиторий `origin` тоже указывает на ветку `main`

`20:30` Внесем теперь локальные изменения: добавим текст в README.md локально 

`21:45` Чтобы локальные изменения появились на GitHub: отправляем с помощью
```sh
git push
```

Поработали локально -> "появился" интернет -> отправили в GitHub.

### 6.3 Отправляем в GitHub новую ветку newbranch

`22:45` Промоделируем ветку: создадим новую ветку `newbranch`, чтобы вытолкнуть на GitHub *только её*.

`23:45` Перейдем в созданную ветку и внесем изменения в файл (сохраним, добавим, закоммитим).

`24:40` Вернемся обратно в `main` и попробуем сделать `git push` -> получили `Everything up-to-date`: т.к. мы находились в ветке `main` - `git push` ничего не вытолкнул.

`25:05` Переключаемся обратно в `newbranch` и набираем `git push` -> получаем сообщение, что текущая ветка не привязана к удаленному репозиторию и подсказку - что нужно сделать, чтобы её тоже выталкивать на GitHub
```sh
fatal: The current branch newbranch has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin newbranch
```

`25:35` Копируем - вставляем - пушим
```sh
git push --set-upstream origin newbranch
```

`25:40` Заходим в браузер -> обновляем страницу -> открываем ветки -> видим новую ветку `newbranch` -> выбираем её -> видим наши изменения в файле. В ветке `main` изменений нет

`26:05` Переключаемся в консоли на ветку `main` и сделаем слияние `git merge newbranch`. Слияние произошло - смотрим `git log --oneline --graph`: main и newbranch на одном уровне. Отлично

`27:20` В принципе ветка `newbranch` уже не нужна, поэтому её можно удалить `git branch -d newbranch` -> после удаления делаем `git push` - выталкиваем основную ветку тоже на удаленный репозиторий

`27:45` Переходим в браузер обновляем страницу

`27:50` На удаленном репозитории GitHub ветка `new_branch` не удалилась. Она у нас не используется, т.к. мы уже произвели слияние этой ветки с `main`.

`28:05` Можно эту ветку удалить *через браузер*: выбрать в раскрывающемся списке main `View all branches` и нажать на корзину для `new_branch`.

`28:20` Это же удаление можно сделать *в консоли* из локального репозитория:
```sh
git push origin --delete \newbranch

# У Дениса в уроке ошибка - отсутствует перед веткой косой слэш \
```
Получим сообщение об успешном удалении
```sh
To https://github.com/magus1968/test_repo.git
 - [deleted]         newbranch
```


### 6.4 Разрешаем конфликт

`28:55` Теперь разберем конфликтную ситуацию: через браузер внесем изменения в файл и в этот же файл внесем изменения локально. И если мы локально попытаемся вытолкнуть изменения, то git нам скажет, что он не может этого сделать: у вас отличается версия локального репозитория от того, что уже в браузере - там тоже произошли изменения в этот же файл, поэтому нельзя сделать push.

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

---

`38:20` - ПРОДОЛЖИТЬ



---

## Полезно

### # Удалить репозиторий через GitHub
— Eдинственный нормальный способ удаления GitHub-репозиториев делается через профиль: нужно зайти на сайт, нажать кнопку «Удалить» и подтвердить удаление [ссылка](https://skillbox.ru/media/code/kak-v-github-udalit-i-vosstanovit-repozitoriy/) на источник

1. Находим репозиторий

Все созданные проекты расположены слева. Или нажав кнопку `Show more` перейти на вкладку `Your repositories`

2. Переходим в настройки репозитория

Открываем вкладку `Settings` –> пролистываем вниз до раздела `Danger Zone` –> нажимаем кнопку `Delete this repository`

3. Подтверждаем удаление

Появляется окно с подтверждением действия и `поле для ввода`, в котором нужно ввести полное название репозитория — имя вашего аккаунта и проекта. Например, `DavisWalkers/my_first_repo`

После этого становится доступной кнопка окончательного удаления `I understand the consequences, delete this repository`. Жмем –> нас перебрасывает в профиль –> появляется уведомление об успешном удалении репозитория. 
```sh
Your repository "DavisWalkers/my_first_repo" was successfully deleted
```
`Done`

---

### # Обновить Git
Выполняется из Git Bash
```sh
git update-git-for-windows
```

### # Устранить проблемы с кирилизацией
```sh
git config --global core.quotepath false
```
После выполнения этой команды, при вызове git status получите нормальное имя файла на русском языке, а не что-то такое в формате nnn nnn

### # Как переименовать user.name: локально в Git ?
