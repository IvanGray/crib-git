# Моя шпаргалка по работе GIT

![alt tag](https://git-scm.com/images/logo@2x.png)

**Git** (произн. **«гит»**) — распределённая система управления версиями. Проект был создан Линусом Торвальдсом для управления разработкой ядра Linux, первая версия выпущена 7 апреля 2005 года. На сегодняшний день его поддерживает Джунио Хамано.

**СВК** - это система контроля версий

1. Установка GIT
 + [Скачать и установить](#Установка-GIT);
2. Кофигурация
 + [Общие-алиасы](#Общие-алиасы);
 + [Глобальные-настройки](#Глобальные-настройки-);
 + [Git-init](#git-init);
 + [Файл gitignore](#Файл-gitignore)
 + [Файл README.md](#Файл-readmemd);
 + [Горизонтальные (разделительные) линии](#Lines).
3. Просмотр информации и состояние изменения файлов проекта
 + [Основные команды](#Просмотр-информации-и-состояние-изменения-файлов-проекта);
 + [git log](#git-log);
4. Основы Git - Запись изменений в репозиторий
 + [Определение состояния файлов ($ git status)](#Определение-состояния-файлов);
 + [Отслеживание новых файлов](#Отслеживание-новых-файлов);
 + [Фиксация изменений](#Фиксация-изменений);
 + [Удаление файлов](#Удаление-файлов);
 + [Перемещение файлов](#Перемещение-файлов);
5. GIT Ветление
 + [Branching](#GIT-Ветление);
 + [Merge - слияние веток](#merge---слияние-веток);
 + [Конфликты](#Конфликты);
6. Работа с удаленными репозиториями
 + [Удаленные гит репозитории](#Работа-с-удаленными-репозиториями);


## Установка GIT

Скачать и установить GIT можно на сайте : https://git-scm.com/downloads

## Кофигурация

###Общие алиасы

**git status, git add, git commit, git checkout** — общие команды, для которых полезно иметь сокращения.
Для пользователей Windows.Добавить алиасы следует в ~/.gitconfig file:

	[alias]
		st = status
		ci = commit
		br = branch
		co = checkout
		df = diff
		dc = diff --cached
		lg = log -p
		lol = log --graph --decorate --pretty=oneline --abbrev-commit
		lola = log --graph --decorate --pretty=oneline --abbrev-commit --all
		ls = ls-files

Выполнить алиасы можно командами:

	git config --global alias.co checkout
	git config --global alias.ci commit
	git config --global alias.st status
	git config --global alias.br branch
	git config --global alias.hist 'log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short'
	git config --global alias.type 'cat-file -t'
	git config --global alias.dump 'cat-file -p'

###Глобальные настройки :


- `$ git config --global user.name 'Vlad Voitovich'`
- `$git config --global user.email info@example.com`

В глобальные настройки прописываем свое имя и email для комитов (commit)

Для просмотра списка конфигов:
- `$ git config --list `


### GIT init:

Чтобы создать git репозиторий в каталоге, выполните команду git init.

- `$ git init`

### Файл .gitignore:

Предназначен для игнорирования файлов, в которых не следует отслеживать изменения. В файле достаточно указать путь к файлам:

- `node_modules/`
- `src/libs/`

### Файл README.md

Предназначен для описания проекта или инструкций.

## Просмотр информации и состояние изменения файлов проекта

- `$ git reflog` - основные логи последних изменений в проекте.

- `$ git diff` - изменения между предыдущей и последней версии фала. ( $ git diff c784s...42asd21)

	- `$ git diff -b` - игнорирование всех изменений в пробелах
	- `$ git diff -w` - игнорирование всех пробелов

- `$ git show d8578edf8458ce06fbc5bb76a58c5ca4a58c5ca4 ` - изменения, сделанные в заданном коммите.

- `$ git blame file.txt ` - изменения, сделанные в заданном коммите.

### GIT log

- `$ git log` - просмотр логов, историю коммитов изменений проекта.

В результате выполнения **git log** в данном проекте, вы должны получить что-то вроде этого:

```git
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

	changed the version number

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

	removed unnecessary test code

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

	first commit
```
По умолчанию, без аргументов, **git log** выводит список коммитов созданных в данном репозитории в обратном хронологическом порядке. То есть самые последние коммиты показываются первыми. Как вы можете видеть, эта команда отображает каждый коммит вместе с его контрольной суммой SHA-1, именем и электронной почтой автора, датой создания и комментарием.

Существует превеликое множество параметров команды **git log** и их комбинаций, для того чтобы показать вам именно то, что вы ищете. Здесь мы покажем вам несколько наиболее часто применяемых.

Один из наиболее полезных параметров — это -p, который показывает дельту **(разницу/diff)**, привнесенную каждым коммитом. Вы также можете использовать **-2**, что ограничит вывод до 2-х.

	options:

	- ` --all` - отобразить все.
	- ` --color` - логи с цветом.
	- ` --graph` - показывать ASCII-граф истории ветвлений и слияний рядом с выводом лога.
	- ` --decorate` - логи с branch и tag names.
	- ` --stat` - для каждого коммита дополнительно выводить статистику по изменённым файлам.
	- ` --shortstat` - показывать только строку changed/insertions/deletions от вывода с опцией --stat.
	- ` --name-only` - показывать список изменённых файлов после информации о коммите.
	- ` --name-status` - выводить список изменённых файлов вместе с информацией о добавлении/изменении/удалении.
	- ` --abbrev-commit` - выводить только первые несколько символов контрольной суммы SHA-1 вместо всех 40..
	- ` -p` - для каждого коммита показывать дельту внесённых им изменений
	- ` --word-diff` - показывать изменения на уровне слов.
	- ` --merge` - только коммиты слияний.
	- `--pretty=oneline` - отображать коммиты в альтернативном формате. Возможные параметры: oneline, short, full, fuller и format (где вы можете указать свой собственный формат).
	- `-(n)` - показать последние n коммитов.
	- `--since, --after` - ограничить коммиты теми, которые сделаны после указанной даты.
	- `--until, --before` - ограничить коммиты теми, которые сделаны до указанной даты.
	- `--author` - показать только те коммиты, автор которых соответствует указанной строке.
	- `--committer` - показать только те коммиты, коммитер которых соответствует указанной строке.
	- ` --reverse` - история изменений в обратном порядке.

Можно использовать универсальную команду:

- `$ git log --oneline --graph --all --decorate`

## Основы Git - Запись изменений в репозиторий

### Определение состояния файлов

- `$ git status` - основной инструмент, используемый для определения, какие файлы в каком состоянии находятся.

### Отслеживание новых файлов

Для того чтобы начать отслеживать (добавить под версионный контроль) новый файл, используется команда git add. Чтобы начать отслеживание файла README, вы можете выполнить следующее:

- `$ git add "file_name"` - добавить в буфер файл.

- `$ git add "folder"` - добавить папку с файлами в буфер.

- `$ git add all` или `$ git add .`  - добавить все файлы в буфер.

Вы можете видеть, что файл проиндексирован по тому, что он находится в секции “Changes to be committed”. Если вы выполните коммит в этот момент, то версия файла, существовавшая на момент выполнения вами команды **git add**, будет добавлена в историю снимков состояния. Как вы помните, когда вы ранее выполнили [Git-init](#git-init), вы затем выполнили **git add** (файлы) — это было сделано для того, чтобы добавить файлы в вашем каталоге под версионный контроль. Команда **git add** принимает параметром путь к файлу или каталогу, если это каталог, команда рекурсивно добавляет (индексирует) все файлы в данном каталоге.

### Фиксация изменений

- `$ git commit -m "file_name"`

- `$ git commit -v` - более подробное напоминание того, что именно было изменено

- `$ git commit --amend или git commit -a -m (-am)` - если у вас есть желание пропустить этап индексирования.

Это приведёт к тому, что в комментарий будет также помещена дельта/diff изменений, таким образом вы сможете точно увидеть всё, что сделано.) Когда вы выходите из редактора, Git создаёт для вас коммит с этим сообщением (удаляя комментарии и вывод diff'а).


### Удаление файлов

Для того чтобы удалить файл из Git'а, вам необходимо удалить его из отслеживаемых файлов (точнее, удалить его из вашего индекса) а затем выполнить коммит. Это позволяет сделать команда git rm, которая также удаляет файл из вашего рабочего каталога, так что вы в следующий раз не увидите его как “неотслеживаемый”.

- `$ git rm <file>`

### Перемещение файлов

- `$ git mv file_from file_to`

Git неявно определяет, что произошло переименование, поэтому неважно, переименуете вы файл так или используя команду mv. Единственное отличие состоит лишь в том, что mv — это одна команда вместо трёх — это функция для удобства. Важнее другое — вы можете использовать любой удобный способ, чтобы переименовать файл, и затем воспользоваться add/rm перед коммитом.


## GIT Ветление

![alt tag](https://git-scm.com/figures/18333fig0301-tn.png)

- `$ git branch ` - получаем список веток, с которыми работаем (вездочкой отмечена текущая ветвь).

- `$ git branch -a` - просмотреть все существующие ветви.

- `$ git branch some_branch` - создать новый бранч (ответвится от текущего).

- `$ git checkout -b` - создать и переключиться на бранч.

- `$ git branch -m` - пере бранча.

- `$ git branch -d some_branch` - удалить бранч  (после мерджа).

- `$ git branch -r` - список всех удаленных брачей.

- `$ git branch -D some_branch` - просто удалить бранч (тупиковая ветвь).

- `$ git checkout some_branch` - переключиться на данную ветку.

### Merge - слияние веток

- `git merge <branch>` - слияние текущей ветки с мастер.

- `git merge <branch> --no-commit`

- `git merge <branch>` -s ours - слияние текущей ветки , но отбрасывая любые изменения в ветвлении, используя текущее дерево, как новое.

- `git merge --no-ff branch` - заставляет сделать коммит слияния.

- `git merge --ff-only` - не делать быстрого слияния.

- `git merge --abort` - оборвать слияние.

### Конфликты

git mergetool

При слиянии могут возникать конфликты. **<HEAD>** указывает на код мастера.Конфликты редактируются в основном вручную.


## Работа с удаленными репозиториями

### GIT хостинг

![alt tag](https://semaphoreci.com/docs/assets/img/adding-new-project/select-github-or-bitbucket.png)

Для работы с удаленными репозиториями нужен GIT хостинг. 2 самых популярных :

	1. Github (https://github.com/)
	 2. Bitbucket (bitbucket.org)

Главное отличие между ними - github.com предоставляет открытый хостинг бесплатно, а для закрытых проектов платные тарифы. В отличии от github , bitbucket предоставляет бесплатно закрытый хостинг.
