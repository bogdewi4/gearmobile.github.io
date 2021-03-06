---
title: "Light Explorer - менеджер проектов в Notepad++"
layout: post
categories: notepad
tags: [light explorer, notepad]
share: true
---

> Одним из серьезных недостатков программного блокнота Notepad++ является отсутствие встроенного менеджера файлов.

Например, имеется разрабатываемый проект, в котором имеется несколько папок: `html`, `css`, `images`, `js`. При верстке сайта необходимо вставить в html-код или файл стилей css изображение. Файл вроде бы сохранен в нужной папке, но вот имя его уже забылось.

Открывать тот же Total Commander, чтобы проверить, где располагается нужный файл и имя этого файла? Достаточно неудобно пользоваться сторонней программой, чтобы только удостовериться в месторасположении файлов.

На помощь может прийти плагин Light Explorer. Название плагина отвечает его возможностям - он предоставляет файловую систему диска, на котором хранится проект, в древовидном виде. Приятной особенностью Light Explorer является возможность запоминания той папки, с которой производилась работа в прошлый раз. То есть, когда запускается плагин, файловая система автоматически разворачивается до конкретного проекта включительно.

Установка Light Explorer производится так же, как и других плагинов Notepad++, через менеджер плагинов Plugin Manager:

![Плагин Light Explorer Notepad++]({{site.url}}/images/uploads/2013/11/plugin-lightexplorer.png)

После установки Light Explorer значок плагина появляется в панели инструментов Notepad++, что очень удобно для быстрого доступа к нему. Также плагин можно вызвать стандартным способом, через меню "Плагины - Light Explorer". Для вызова Light Explorer также имеется предустановленное по умолчанию сочетание "горячих клавиш" <kbd>Alt + A</kbd>:

![Значок плагина Light Explorer на панели инструментов Notepad++]({{site.url}}/images/uploads/2013/11/icon-lightexplorer.png)

Запустим плагин Light Explorer. С левой строны окна Notepad++ откроется панель плагина с древовидной файловой системой:

![Панель плагина Light Explorer]({{site.url}}/images/uploads/2013/11/panel-lightexplorer.png)

По контекстному меню на файле доступно несколько команд, таких как "Открыть", "Переименовать", "Удалить", "Свойства файла":

![Контекстное меню плагина Light Explorer]({{site.url}}/images/uploads/2013/11/lightexplorer-contex-menu.png)

Команда "Search from here" открывает диалоговое окно поиска файлов в текущей папке. "Synchronize tree with current document" показывает расположение текущего файла в древовидном списке файловой системы.

Пункт "Standart Menu" открывает вложенное контекстное меню, которое является общесистемным. То есть, это стандартное контекстное меню Проводника Windows.

К сожалению, на этом возможности плагина Light Explorer заканчиваются. А было бы очень неплохо, к примеру, так как это устроено в менеджере проектов Dreamveawer - перетаскивать методом drag'n'drop файлы прямо в окно кода, с автоматическим заполнением файлового пути в атрибуте `src=""` или `href=""`.

На этом все.

---
