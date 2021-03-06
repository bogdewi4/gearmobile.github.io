---
title: "Проверка орфографии в Sublime Text"
layout: post
categories: sublime
tags: [sublime, spellcheck]
share: true
---

> Вопрос настройки орфографии (spellcheck) в редакторе Sublime Text 3.

Сам вопрос подразумевает настройку проверки орфографии (spellcheck) русского текста в Sublime Text, ибо орфография английского языка включена в этом редакторе по умолчанию (точнее - есть встроенный словарь английского языка).

## Установка русского словаря

Чтобы включить возможность проверки (spellcheck) русскаго текста в редакторе Sublime Text, необходимо подключить словарь русского языка. Готовый к использованию под Sublime Text словарь русского языка можно скачать по ссылке - [sublime_russian_english_dictonary.zip][1].

После скачивания архива его нужно распаковать. В итоге получиться два файла:

{% highlight powershell %}
$ ls
  russian_english.aff
  russian_english.dic
{% endhighlight %}

Затем нужно переместить (или скопировать) оба файла в директорию с плагинами Sublime Text. Это можно сделать тремя способами.

**Первый способ** - быстрый и простой, основан на использовании консоли Linux (я не забыл сказать, что пример приведен под Linux Mint 17 Cinnamon?). Для этого в текущей директории со словарями открываем терминал и выполняем всего одну команду:

{% highlight powershell %}
$ cp * ~/.config/sublime-text-3/Packages/
{% endhighlight %}

... которая произведет копирование всех файлов (в данном случае - двух) в директорию с плагинами под Sublime Text.

**Второй способ** - более медленный. Для этого в окне Nemo (в Linux Mint Cinnamon - это аналог Finder под Mac OS X или Проводник под Windows) в контекстном меню выбираем "Показать скрытые файлы".

Отобразятся все скрытые (системные) файлы\директории системы Linux Mint и среди них нужная нам директория - ".config":

![Директория плагинов редактора Sublime Text]({{site.url}}/images/uploads/2014/09/spellcheck_sublime_config.png)

Переходим по пути `.config` - `sublime-text-3` - `Packages` и с помощью клавиш <kbd>Ctrl+C</kbd> + <kbd>Ctrl+V</kbd> производим вставку файлов русского словаря.

**Третий способ** - с помощью редактора Sublime Text. Для этого в самом редакторе переходим по пути "Preferences" - "Browse Packages...". Откроется окно с плагинами Sublime Text. Далее - действовать, как во втором примере.

## Spellcheck в Sublime Text

После помещения файлов словаря в директорию "Packages" желательно перезапустить редактор Sublime Text. Если все прошло успешно, то в меню "View" - "Dictionary" под пунктом "Language - English" появиться пункт "russian-english" - это и есть подключенный нами словарь русского языка.

Чтобы осуществить проверку (spellcheck) на ошибки в русско-язычном тексте в редакторе Sublime Text, нужно выбрать в меню вышеназванный пункт - "View" - "Dictionary" - "russian-english", тем самым указав редактору, какой словарь использовать для проверки. А затем запустить проверку орфографии (spellcheck), нажав клавишу <kbd>F6</kbd>. Повторное нажатие клавиши отключает проверку орфографии.

## Настройка spellcheck в Sublime Text

Рассмотренный выше способ проверки орфографии (spellcheck) в Sublime Text можно назвать ручным. Однако, для этого способа требуется много времени и телодвижений, чтобы включить его.

Если в Sublime Text пишется в основном русско-язычный текст, то можно включить автоматическую проверку орфографии (spellcheck) в этом редакторе.

Для этого в пользовательских настройках "Preferences" - "Settings - User" достаточно прописать две строки:

{% highlight json %}
// Word list to use for spellchecking
"dictionary": "Packages/russian_english.dic",

// Set to true to turn spellchecking on by default
"spell_check": true
{% endhighlight %}

Первая строка указывает редактору Sublime Text месторасположение русского словаря, тем самым говоря ему, что для проверки орфографии (spellcheck) нужно использовать этот словарь, а не какой-нибудь другой.

Вторая строка включает автоматическую проверку орфографии (spellcheck) в Sublime Text. Если в тексте много англоязычных слов, или если необходимо на время отключить проверку, то достаточно нажать клавишу <kbd>F6</kbd>. Чтобы снова вернуть назад проверку, опять нажимаем <kbd>F6</kbd>.

## Заключение

Очень полезная штучка оказалась для меня, возможность проверки орфографии (spellcheck) в Sublime Text. Открыл для себя с удивлением, сколько же много я ошибок и опечаток делаю в тексте!

Один вопрос в данной теме остался для меня открытым - как самому вносить правки в русский словарь? Как самому добавлять в него слова? К примеру, чтобы он не "ругался" на незнакомое ему слово "фреймворк" или "плагин"?

---

[1]: https://www.dropbox.com/s/rug0kg3gae8aha2/sublime_russian_english_dictonary.zip?dl=0 "sublime_russian_english_dictonary.zip"
