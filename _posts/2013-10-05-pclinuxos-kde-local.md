---
title: "PCLinuxOS KDE - локализация дистрибутива"
layout: post
categories:
tags: [addlocale, pclinuxos]
share: true
---

> С недавнего времени открыл для себя дистрибутив PCLinuxOS. До этого момента сталкивался с ним только по работе. Дело в том, что я пишу статьи и переводы по тематике Linux, и часто приходится переводить статьи из журнала PCLinuxOS Magazine, который освещает вопросы, связанные с работой этого дистрибутива.

Для перевода статьи по установке локального сервера LAMP под PCLinuxOS мне потребовались русскоязычные скриншоты. Естественно, для этого необходимо иметь локализованную операционную систему. То есть, нужно установить поддержку русского языка в системе.

Первоначально поступил стандартно - скачал свежий дистрибутив PCLinuxOS KDE и установил его под виртуальной машиной VirtualBox. Однако, установленная таким образом операционка так сильно тормозила, что мне пришлось устанавливать дистрибутив "по настоящему". Благо, на тот момент на моем жестком диске имелся свободный раздел.

Установка прошла успешно. Но интерфейс операционной системы был на английском языке. Надо сказать, что по умолчанию в PCLinuxOS встроен только английский язык, а поддержка дополнительных языков устанавливается отдельно. Причем, дополнительные языки инсталлируются не совсем так, как например, в Ubuntu/Debian или других дистрибутивах. Не с помощью менеджера пакетов, а с помощью специального скрипта `addlocale`.

Итак, ниже привожу пошаговое руководство по установке русского языка в PCLinuxOS.

## Обновление системы

После установки дистрибутива необходимо сразу же произвести его обновление. Даже несмотря на то, что он был только что скачан и по идее должен быть самым свежим. Дело в том, что PCLinuxOS относится к классу `rolling-release`, то есть, его обновление производится бесшовно. К такому классу также относятся известные Gentoo Linux, ArchLinux.

Запускаю менеджер пакетов Synaptic. И последовательно нажимаю кнопку "Reload" для обновления списка репозиториев, затем "Mark All Upgrades" - для выделения всех пакетов, доступных для обновления, и затем кнопку "Apply" - чтобы применить два предыдущих действия. Synaptic скачает отмеченные пакеты и произведет их установку в систему:

![Обновление дистрибутива PCLinuxOS]({{site.url}}/images/uploads/2013/11/pclinuxos_localization_1.jpg)

Не закрываю менеджер пакетов, так как в нем необходимо выполнить еще несколько действий.

## Изменение репозиториев PCLinuxOS

Для правильной работы скрипта `addlocale` необходимо, чтобы в менеджере пакетов Synaptic был подключен только один репозиторий. Иначе скрипт просто откажется устанавливать дополнительные языковые пакеты, в том числе и русский язык.

По умолчанию после инсталляции дистрибутива в Synaptic подключены два репозитория: [http://ftp.vim.org/ibiblio/disributions/pclinuuxos/main][1] и [http://ftp.vim.org/ibiblio/disributions/pclinuuxos/policy][2]. Перехожу в менеджере пакетов в меню "Settings - Repositories". Откроется окно, в котором производится настройка репозиториев.

Здесь можно добавить, удалить, переместить или отключить репозиторий. Для просмотра всего списка служит полоса прокрутки. Отключаю репозиторий [http://ftp.vim.org/ibiblio/disributions/pclinuuxos/main][1] (*он находится самым первым в списке*) и вместо него активирую репозиторий [http://ftp.heanet.ie/pub/pclinuxos/apt/][3].

Затем прокручиваю полосу прокрутки вниз и отключаю репозиторий [http://ftp.vim.org/ibiblio/disributions/pclinuuxos/policy][2]. Нажимаю кнопку <kbd>ОК</kbd>, чтобы сохранить изменения и выйти из этого окна. В основном окне Synaptic снова нажимаю кнопку "Reload", чтобы обновить репозитории. Впрочем, система сама предложит вам выполнить это действие:

![Обновление репозиториев PCLinuxOS]({{site.url}}/images/uploads/2013/11/pclinuxos_localization_1-1.jpg)

Теперь менеджер пакетов можно закрыть.

## Запуск скрипта addlocale

Как уже говорилось ранее, скрипт `addlocale` в системе PCLinuxOS служит для установки дополнительных языков, в том числе и русского. Запускаю его, используя стандартную возможность системы Linux - нажимаю комбинацию клавиш <kbd>Alt+F2</kbd>.

В верхней части Рабочего стола появится строка для ввода команд:

![Запуск скрипта addlocale]({{site.url}}/images/uploads/2013/11/pclinuxos_localization_2.jpg)

Вбиваю имя скрипта addlocale и нажимаю Enter.

## Установка русского языкового пакета с помощью addlocale

Откроется окно, в котором будет сообщаться, что в системе обнаружена более старая версия скрипта, которая и была успешно удалена. Далее пользователя просят перезапустить скрипт `addlocale`.

Если же при повторном запуске данное сообщение появиться вновь, то необходимо выполнить последовательность действий: под учетной записью `root` удалить файл `/tmp/xsuaddlocale`; под учетной записью обычного пользователя запустить "Менеджер Локализации" (Localization Manager).

Это другое название скрипта `addlocale`:

![Проверка версии скрипта addlocale]({{site.url}}/images/uploads/2013/10/pclinuxos_localization_3.jpg)

Оглашаюсь со скриптом и нажимаю кнопку <kbd>OK</kbd>. Затем снова запускаю скрипт, как это было описано в предыдущем шаге. Появится информационное окно, в котором описывается, для чего предназначен скрипт `addlocale` и описывается его возможности, принцип работы:

![Информация о скрипте addlocale]({{site.url}}/images/uploads/2013/10/pclinuxos_localization_3-1.jpg)

Запуститься окно со списком доступных языковых пакетов. По умолчанию выбран пакет английского языка. Мне необходим русский язык, поэтому прокручиваю список вниз и отмечаю `Russian`:

![Выбор языкового пакета PCLinuxOS]({{site.url}}/images/uploads/2013/10/pclinuxos_localization_4.jpg)

Все несложные действия выполнены, дальше скрипт выполнит все сам. Нажимаю кнопку <kbd>ОК</kbd>. `Addlocale` проверит все зависимости и возможные обновления:

![Проверка зависимостей скриптом addlocale]({{site.url}}/images/uploads/2013/10/pclinuxos_localization_4-2.jpg)

Система переспросит, уверен ли я в том, что хочу установить дополнительные пакеты:

![Подтверждение выбранного действия]({{site.url}}/images/uploads/2013/10/pclinuxos_localization_4-1.jpg)

Начнется процесс скачивания и установки пакетов локализации:

![Установка пакетов локализации]({{site.url}}/images/uploads/2013/10/pclinuxos_localization_5.jpg)

После успешной инсталляции языкового пакета появится сообщение о том, что можно перезагрузить операционную систему, чтобы изменения автоматически вступили в силу. Перезагружаюсь и "получаю" следующее сообщение:

![Локализация системы PCLinuxOS]({{site.url}}/images/uploads/2013/10/pclinuxos_localization_5-1.jpg)

Последует целая серия вопросов, связанных с установкой русского языка в PCLinuxOS и изменения различных настроек, в том числе единиц исчисления, пути директорий в домашней папке пользователя. Трудностей с ответом на эти вопросы возникнуть не должно, поэтому скриншотов не привожу.

Единственное, отмечу, что для себя я оставил англоязычные названия папок в моей домашней папке пользователя. Мне так удобнее и я был приятно удивлен возможностью выбора, так как в той же Ubuntu мне такого выбора не предоставлялось.

В заключение хочу сказать, что дистрибутив PCLinuxOS произвел на меня очень приятное впечатление. Казалось бы, все тоже самое, что и в других ему подобных операционных системах. Но вот законченность в мелочах, выверенный дизайн интерфейса покорили меня. В результате простого эксперимента по локализации PCLinuxOS последняя осталась у меня на компьютере.

На этом вопрос о добавлении русского языка в систему PCLinuxOS можно считать закрытым.

[1]: http://ftp.vim.org/ibiblio/disributions/pclinuuxos/main "Main"
[2]: http://ftp.vim.org/ibiblio/disributions/pclinuuxos/policy "Policy"
[3]: http://ftp.heanet.ie/pub/pclinuxos/apt/ "Apt"
