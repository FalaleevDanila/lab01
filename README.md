## Laboratory work I

Данная лабораторная работа посвещена изучению утилит для разработки проектов

## Tasks

- [ ] 1. Ознакомиться со ссылками учебного материала
- [ ] 2. Выполнить инструкцию учебного материала
- [ ] 3. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial
Установка переменных окружения, добавление синонима команды:
```bash
[danila@Dellic ~]$ export GITHUB_USERNAME=FalaleevDanila #создание переменной в окружении GITHUB_USERNAME 
[danila@Dellic ~]$ export GIST_TOKEN=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX #создание переменной в окружении GIST_TOKEN
[danila@Dellic ~]$ alias edit=nano # Создаём синоним команды edit(nano)
```
Создание папки, в которой будет находится рабочая облась:
```ShellSession
[danila@Dellic ~]$ mkdir -p ${GITHUB_USERNAME}/workspace # создание папки в FalaleevDanila/workspace
[danila@Dellic ~]$ cd ${GITHUB_USERNAME}/workspace # переход в папку /FalaleevDanila/workspace
[danila@Dellic workspace]$  pwd #Вывод текущей директории
/home/danila/FalaleevDanila/workspace
[danila@Dellic workspace]$ cd .. # Переход на раздел выше
[danila@Dellic FalaleevDanila]$ pwd # Вывод текущей директории
/home/danila/FalaleevDanila
```
Создание папки в рабочей области:
```ShellSession
[danila@Dellic FalaleevDanila]$  mkdir -p workspace/tasks/ # создание папки
[danila@Dellic FalaleevDanila]$  mkdir -p workspace/projects/ # создание папки
[danila@Dellic FalaleevDanila]$ mkdir -p workspace/reports/ # создание папки
[danila@Dellic FalaleevDanila]$ cd workspace #  Переход в /FalaleevDanila/workspace
```
Скачивание и распаковка node js:
```ShellSession
[danila@Dellic workspace]$ # Debian 
[danila@Dellic workspace]$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz #  Скачать указанный файл
--2019-03-04 18:36:04--  https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
Загружен сертификат CA «/etc/ssl/certs/ca-certificates.crt»
Распознаётся nodejs.org (nodejs.org)… 2606:4700:10::6814:172e, 2606:4700:10::6814:162e, 104.20.22.46, ...
Подключение к nodejs.org (nodejs.org)|2606:4700:10::6814:172e|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 9356460 (8,9M) [application/x-xz]
Сохранение в: «node-v6.11.5-linux-x64.tar.xz»

node-v6.11.5-linux-x64.tar.xz    100%[========================================================>]   8,92M   542KB/s    за 35s     

2019-03-04 18:36:41 (261 KB/s) - «node-v6.11.5-linux-x64.tar.xz» сохранён [9356460/9356460]

[danila@Dellic workspace]$ tar -xf node-v6.11.5-linux-x64.tar.xz # Разархивировать архив
[danila@Dellic workspace]$ rm -rf node-v6.11.5-linux-x64.tar.xz # Удалить архив
[danila@Dellic workspace]$ mv node-v6.11.5-linux-x64 node # Переименовать папку с nodejs
```
Дописываем в PATH путь к node js:
```ShellSession
[danila@Dellic workspace]$ ls node/bin # Вывод директорий и файлов в папке node/bin
node  npm
[danila@Dellic workspace]$ echo ${PATH} # Вывод переменной окружения PATH
/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl
[danila@Dellic workspace]$ export PATH=${PATH}:`pwd`/node/bin # Дописать в PATH папку с node js
[danila@Dellic workspace]$ echo ${PATH} # Вывод переменной окружения PATH
/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/home/danila/FalaleevDanila/workspace/node/bin
[danila@Dellic workspace]$ mkdir scripts # Создать папку /FalaleevDanila/workspace/scripts
[danila@Dellic workspace]$ cat > scripts/activate<<EOF #Запись указанной строки в файл /FalaleevDanila/workspace/scripts/activate
export PATH=\${PATH}:`pwd`/node/bin
> export PATH=\${PATH}:`pwd`/node/bin
> EOF
[danila@Dellic workspace]$ source scripts/activate # Выполнить указанный скрипт
```
Установка пакета gistup в node js:
```ShellSession
[danila@Dellic workspace]$ npm install -g gistup # Установка пакета gistup в node js
/home/danila/FalaleevDanila/workspace/node/bin/gistup -> /home/danila/FalaleevDanila/workspace/node/lib/node_modules/gistup/bin/gistup
/home/danila/FalaleevDanila/workspace/node/bin/gistup-open -> /home/danila/FalaleevDanila/workspace/node/lib/node_modules/gistup/bin/gistup-open
/home/danila/FalaleevDanila/workspace/node/bin/gistup-rename -> /home/danila/FalaleevDanila/workspace/node/lib/node_modules/gistup/bin/gistup-rename
/home/danila/FalaleevDanila/workspace/node/lib
└─┬ gistup@0.1.3 
  ├─┬ optimist@0.3.7 
  │ └── wordwrap@0.0.3 
  └── queue-async@1.2.1 

[danila@Dellic workspace]$ ls node/bin # Вывод директорий и файлов из /FalaleevDanila/workspace/node/bin
gistup  gistup-open  gistup-rename  node  npm
```
Настройка config модуля gistup:
```ShellSession
[danila@Dellic workspace]$ cat > ~/.gistup.json <<EOF # Вывод указанного текста в файл ~/.gistup.json
{
> {
>   "token": "${GIST_TOKEN}"
> }
> EOF
```

## Report

```ShellSession
$ export LAB_NUMBER=01 
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER} 
$ mkdir reports/lab${LAB_NUMBER} 
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md 
$ cd reports/lab${LAB_NUMBER} 
$ edit REPORT.md 
$ gistup -m "lab${LAB_NUMBER}" # enter: yes↵ 
```

## Links

### Unix commands

- [ar](https://en.wikipedia.org/wiki/Ar_(Unix))
- [cat](https://en.wikipedia.org/wiki/Cat_(Unix))
- [cd](https://en.wikipedia.org/wiki/Cd_(command))
- [cp](https://en.wikipedia.org/wiki/Cp_(Unix))
- [cut](https://en.wikipedia.org/wiki/Cut_(Unix))
- [echo](https://en.wikipedia.org/wiki/Echo_(command))
- [env](https://en.wikipedia.org/wiki/Env_(shell))
- [ex](https://en.wikipedia.org/wiki/Ex_(editor))
- [file](https://en.wikipedia.org/wiki/File_(command))
- [find](https://en.wikipedia.org/wiki/Find)
- [ls](https://en.wikipedia.org/wiki/Ls)
- [man](https://en.wikipedia.org/wiki/Man_page)
- [mkdir](https://en.wikipedia.org/wiki/Mkdir)
- [mv](https://en.wikipedia.org/wiki/Mv)
- [nm](https://en.wikipedia.org/wiki/Nm_(Unix))
- [ps](https://en.wikipedia.org/wiki/Ps_(Unix))
- [pwd](https://en.wikipedia.org/wiki/Pwd)
- [rm](https://en.wikipedia.org/wiki/Rm_(Unix))
- [sed](https://en.wikipedia.org/wiki/Sed)
- [touch](https://en.wikipedia.org/wiki/Touch_(Unix))

### Package Managers

- [apt](http://help.ubuntu.ru/wiki/apt) | [dnf](https://en.wikipedia.org/wiki/DNF_(software)) | [yum](https://fedoraproject.org/wiki/Yum/ru)
- [brew](https://brew.sh) | [linuxbrew](http://linuxbrew.sh)
- [npm](https://docs.npmjs.com)

### Software

- [curl](https://www.gitbook.com/book/bagder/everything-curl/details)
- [wget](https://www.gnu.org/software/wget/manual/wget.pdf)
- [clang](https://clang.llvm.org)
- [g++](https://gcc.gnu.org/onlinedocs/gcc-4.0.2/gcc/G_002b_002b-and-GCC.html)
- [make](https://en.wikipedia.org/wiki/Make_(software))
- [open](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/open.1.html)
- [openssl](https://www.openssl.org)
- [nano](https://www.nano-editor.org)
- [tree](https://linux.die.net/man/1/tree)
- [vim](http://www.vim.org)

## Homework

1. Скачайте библиотеку *boost* с помощью утилиты **wget**. Адрес для скачивания `https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz`.
2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0`
3. Подсчитайте количество файлов в директории `~/boost_1_69_0` **не включая** вложенные директории.
4. Подсчитайте количество файлов в директории `~/boost_1_69_0` **включая** вложенные директории.
5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`).
6. Найдите полный пусть до файла `any.hpp` внутри библиотеки *boost*.
7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`.
8. Скомпилирутйе *boost*. Можно воспользоваться [инструкцией](https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html#or-build-custom-binaries) или [ссылкой](https://codeyarns.com/2017/01/24/how-to-build-boost-on-linux/).
9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`.
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
11. Найдите *топ10* самых "тяжёлых".

```
Copyright (c) 2015-2019 The ISC Authors
```
