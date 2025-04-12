# Подсказки по командной строке

#### Quit - клавиша позволяющая выйти из какого-то отображения
PS: мне понадобилась после вывода большого количества log'a
```sh
Q
```

#### Команда смены директории
```sh
cd c:\folder_name
```

#### Создать папку с указанным именем
```sh
mkdir <folder_name>
```

#### Команда отображения листинга текущей директории
```sh
dir
```

#### Команда очистки терминала
```sh
clear
```

#### Удаление файла
```sh
del filename
```
*посмотреть как удалять папку folder_name*

#### Просмотр версии Git
```sh
git --version
```

#### Первичная настройка -- представляемся системе
```sh
git config --global user.name "Name Surname"
git config --global user.email "your@email"
```
Имя и Фамилия обязательно английскими буквами. Подробнее [git config](https://www.atlassian.com/ru/git/tutorials/setting-up-a-repository/git-config)

#### Просмотр имени пользователя и e-mail
```sh
git config user.name
git config user.email
```

#### Вывод всех настроек профиля
```sh
git config --list
```

### 1. Инициализация репозитория
Чтобы Git начал отслеживать папку - её нужно инициализировать. Команда [git init](https://www.atlassian.com/ru/git/tutorials/setting-up-a-repository/git-init) делает из нашей папки - Репозиторий.

 *При этом создается скрытая папка .git*
```sh
git init
```

### 2. Что Git думает о нашем репозитории
*О содержимом нашей папки, что в ней происходит - рассажет [git status](https://www.atlassian.com/ru/git/tutorials/inspecting-a-repository)*
```sh
git status
```

### 3. Добавить файл к отслеживанию
Чтобы Git начал отслеживать изменения в файле - его нужно добавить [git add](https://www.atlassian.com/ru/git/tutorials/saving-changes)
* *Начните набирать имя файла и нажмите клавишу TAB -- Git предложит заполнить недостающие символы*
* *Чтобы не набирать предыдущие команды -- удобно пользоваться стрелками*
```sh
git add filename.ext
```
После нажатия Enter команда примет вид `git add .\filename.ext`

### 4. Сохранить версию файла
*Сохраняем наши изменения с параметром *-m* [message] и "комментируем изменения в кавычках". Т.е. сохраняем текущее состояние как **save** в игре*
```sh
git commit -m "Создали новый файл"
# Вариант "Initial commit"
```
---

ПОМНИТЬ: [git add](https://www.atlassian.com/ru/git/tutorials/saving-changes) всегда идёт в связке с [git commit](https://www.atlassian.com/ru/git/tutorials/saving-changes/git-commit) :

`git add filename` - вначале индексируем

`git commit -m "message"` - затем тут же фиксируем

> *Перед индексированием файла -- его нужно сохранить. Если не сохраним -- Git не поймёт, что файл изменился*

### 5. Просмотр журнала изменений
```sh
git log
```
выводит журнал в подробном объемном представлении

#### 5.1. Просмотр журнала изменений в кратком виде
```sh
git log --oneline
```
с параметром `--oneilne` выводит _**log**_ в одну строку

#### 5.2. Визуализация веток
```sh
git log --graph
```
с параметром `--graph` визуализирует все имеющиеся ветки в _**log**_

#### 5.3. Визуализация веток с двумя параметрами
```sh
git log --oneline --graph
```
параметр `--graph` работает вторым ключем в связке с параметром `--oneline`

#### 5.4. Просмотр всех коммитов во всех ветках
```sh
git log --branches=*
git log --branches=* --oneline
```

#### 5.5. Просмотр журнала коммитов в выбранной ветке из другой
```sh
git log <name_branch>
git log <name_branch> --oneline
git log <name_branch> --oneline --graph
```
находясь в одной ветке, посмотреть что в другой без переключения весьма удобно; подробнее [ссылка](https://www.atlassian.com/ru/git/tutorials/undoing-changes)

### 6. Переход к состоянию по хэшу (идентификатору)
```sh
git checkout [numbers]
```
`numbers` - первые семь символов идентификатора (хэша) из сохранённого коммита



### 7. Разница между текущим состоянием и сохранённым по хэшу
```sh
git diff
git diff 1e8c57f 0992644
```
Добавив через пробел идентификаторы -- можем увидеть различие между состояниями содержимого.
Идентификаторы удобнее вставлять -- от раннего к позднему (имхо)

### 8. Вернуться к предудыщей фиксации
`!` При этом все текущие изменения пропадут
```sh
git restore
```

### 9. Создание ветки `branch`
```sh
git branch <name_branch>
```
*`name_branch` - имя ветки без пробелов*

#### 9.1. Удаление ветки
```sh
git branch -d <name_branch>
```
*удаление ветки производится с параметром `-d`*

#### 9.2. Вывод списка веток
```sh
git branch
```
[git branch](https://www.atlassian.com/ru/git/tutorials/using-branches) -- *выводит список всех существующих веток и отмечает звездочкой `*` name_branch - активную (текущую) ветку*

### 10. Переход в ветку `checkout`
```sh
git checkout <name_branch>
```
в данном контексте [git checkout](https://www.atlassian.com/ru/git/tutorials/using-branches/git-checkout) переключает на выбранную ветку *name_branch*

#### 10.1. Возврат в последнее актуальное состояние файла
```sh
git checkout master
```

### 11. Объединение, слияние `merge`
Находясь в "чистовике" `master` добавляем то, что делали в соседней ветке. Важно: [git merge](https://www.atlassian.com/ru/git/tutorials/using-branches/git-merge) вызывается *оттуда* <-- *куда* хотим добавить изменение.
```sh
git merge <name_branch>
```


### 12. Игнорирование файлов в репозитории `.gitignore`
Производится созданием файла [.gitignore](https://www.atlassian.com/ru/git/tutorials/saving-changes/gitignore) и прописыванием в нем имен файлов, которые нам не требуется отслеживать (например, файлов изображений).

[.gitignore](https://www.atlassian.com/ru/git/tutorials/saving-changes/gitignore) добавляем в отслеживание привычным способом
```sh
git add .gitignore
git commit -m "Добавили .gitignore файл"
```

---
---

### # Специальный раздел для изучения конфликтов
Создан в ветке `final_branch`

Полезная статья про конфликты на Atlasian: [Конфликты слияния в Git](https://www.atlassian.com/ru/git/tutorials/using-branches/merge-conflicts)