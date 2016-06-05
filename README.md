# GIT INSTRUCTION
Шпоргалка по основным командам GIT

**Git** (произн. **«гит»**) — распределённая система управления версиями. Проект был создан Линусом Торвальдсом для управления разработкой ядра Linux, первая версия выпущена 7 апреля 2005 года. На сегодняшний день его поддерживает Джунио Хамано.
**СВК** - это система контроля версий

## Installation

Скачать и установить GIT можно на сайте : (https://git-scm.com/downloads)

### Configuration

Добавить алиасы в ~/.gitconfig file:

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

-`git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist 'log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short'
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'`

Глобальные настройки :

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
- `node_modules/
	src/libs/`

### Файл README.md

Предназначен для описания проекта или инструкций.

## INFO

Просмотр информации и состояние изменения файлов проекта

- `$ git reflog`
Основные логи последних изменений в проекте.

- `$ git diff`
Изменения между предыдущей и последней версии фала.

- `$ git status`
Статус файлов на текущий момент работы.Показывает добавленные файлы в буфер обмена, удаленные файлы из каталога, обновления или изменения файлов.

- `$ git log`

Просмотр логов, историю коммитов, изменений проекта.
Options:
- ` --all` отобразить все.
- ` --color` логи с цветом.
- ` --graph` логи с  ASCII-art графикой слева.
- ` --decorate` логи с branch и tag names.
- ` --stat` логи со статусами.
- ` -p` логи с полными изменениями.
- ` --author=foo` логи с указанием автора комитов.
- ` --after="MMM DD YYYY"`("Jun 20 2008") только commits после заданной даты.
- ` --merge` только коммиты слияний.
- `--pretty=oneline` однострочная история изменений.
- `--since="5 minutes ago"`
- `--until="5 minutes ago"`
