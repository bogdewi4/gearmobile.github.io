---
title: Spell check в Sublime Text 3
author: gearmobile
excerpt: Настройка проверки офографии (spell check) русского текста в Sublime Text 3. Подключение русского словаря, настройки проверки орфографии в Settings User.
layout: post
permalink: /spell-check-sublime-text-3/
cleanretina_sidebarlayout:
  - default
ratings_users:
  - 3
ratings_score:
  - 15
ratings_average:
  - 5
categories:
  - Web Tools
tags:
  - spell check
  - sublime text
---
Вопрос настройки орфографии (spell check) в редакторе Sublime Text 3. Этого вопроса никогда бы и не возникло у меня, если бы я не подписался на создание русского перевода книги [Learning Susy][1]. До этого момента все, что я делал в Sublime Text &#8211; это написание кода на HTML & CSS и немного на JavaScript.

Сам вопрос подразумевает настройку проверки **орфографии (spell check) русского текста** в Sublime Text, ибо орфография английского языка включена в этом редакторе по умолчанию (точнее &#8211; есть встроенный словарь английского языка).

## Установка русского словаря в Sublime Text

Чтобы включить возможность проверки (spell check) русского текста в редакторе Sublime Text, необходимо подключить **словарь русского языка**. Готовый к использованию под Sublime Text словарь русского языка можно скачать по ссылке &#8211; [sublime*russian*english_dictonary.zip][2].

После скачивания архива его нужно распаковать. В итоге получиться два файла:

<pre>$ ls
    russian_english.aff
    russian_english.dic
  </pre>

Затем нужно переместить (или скопировать) оба файла в директорию с плагинами Sublime Text. Это можно сделать **тремя способами**.

**Первый способ** &#8211; быстрый и простой, основан на использовании консоли Linux (я не забыл сказать, что пример приведен под Linux Mint 17 Cinnamon?). Для этого **в текущей директории со словарями** открываем терминал и выполняем всего одну команду:

<pre>$ cp * ~/.config/sublime-text-3/Packages/
  </pre>

&#8230; которая произведет копирование всех файлов (в данном случае &#8211; двух) в директорию с плагинами под Sublime Text.

**Второй способ** &#8211; более медленный. Для этого в окне Nemo (в Linux Mint Cinnamon &#8211; это аналог Finder под Mac OS X или Проводник под Windows) в контекстном меню выбираем &#8220;Показать скрытые файлы&#8221;. Отобразятся все скрытые (системные) файлы\директории системы Linux Mint и среди них нужная нам директория &#8211; &#8220;.config&#8221;:<figure id="attachment_1840" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/09/spellcheck_sublime_config-600x510.png" alt="Директория плагинов редактора Sublime Text" width="600" height="510" class="size-medium wp-image-1840" />][3]<figcaption class="wp-caption-text">Директория плагинов редактора Sublime Text</figcaption></figure> 

Переходим по пути &#8220;.config&#8221; &#8211; &#8220;sublime-text-3&#8243; &#8211; &#8220;Packages&#8221; и с помощью клавиш &#8220;Ctrl+C&#8221; & &#8220;Ctrl+V&#8221; производим вставку файлов русского словаря.

**Третий способ** &#8211; с помощью редактора Sublime Text. Для этого в самом редакторе переходим по пути &#8220;Preferences&#8221; &#8211; &#8220;Browse Packages&#8230;&#8221;. Откроется окно с плагинами Sublime Text. Далее &#8211; действовать, как во втором примере.

### Spell check в Sublime Text

После помещения файлов словаря в директорию &#8220;Packages&#8221; желательно перезапустить редактор Sublime Text. Если все прошло успешно, то в меню &#8220;View&#8221; &#8211; &#8220;Dictionary&#8221; под пунктом &#8220;Language &#8211; English&#8221; появиться пункт &#8220;russian-english&#8221; &#8211; это и есть подключенный нами словарь русского языка.

Чтобы осуществить проверку (spell check) на ошибки в русско-язычном тексте в редакторе Sublime Text, нужно выбрать в меню вышеназванный пункт &#8211; &#8220;View&#8221; &#8211; &#8220;Dictionary&#8221; &#8211; &#8220;russian-english&#8221;, тем самым указав редактору, какой словарь использовать для проверки. А затем запустить проверку орфографии (spell check), нажав клавишу F6. Повторное нажатие клавиши отключает проверку орфографии.

### Настройка spell check в Sublime Text

Рассмотренный выше способ проверки орфографии (spell check) в Sublime Text можно назвать **ручным**. Однако, для этого способа требуется много времени и телодвижений, чтобы включить его. Если в Sublime Text пишется в основном русско-язычный текст, то можно включить автоматическую проверку орфографии (spell check) в этом редакторе.

Для этого в пользовательских настройках &#8220;Preferences&#8221; &#8211; &#8220;Settings &#8211; User&#8221; достаточно прописать две строки:

<pre>// Word list to use for spell checking
    "dictionary": "Packages/russian_english.dic",
    // Set to true to turn spell checking on by default
    "spell_check": true
  </pre>

Первая строка указывает редактору Sublime Text месторасположение русского словаря, тем самым говоря ему, что для проверки орфографии (spell check) нужно использовать этот словарь, а не какой-нибудь другой.

Вторая строка включает автоматическую проверку орфографии (spell check) в Sublime Text. Если в тексте много англоязычных слов, или если необходимо на время отключить проверку, то достаточно нажать клавишу F6. Чтобы снова вернуть назад проверку, опять нажимаем F6.

### Заключение

Очень полезная штучка оказалась для меня, возможность проверки орфографии (spell check) в Sublime Text. Открыл для себя с удивлением, сколько же много я ошибок и опечаток делаю в тексте!

Один вопрос в данной теме остался для меня открытым &#8211; как самому вносить правки в русский словарь? Как самому добавлять в него слова? К примеру, чтобы он не &#8220;ругался&#8221; на незнакомое ему слово &#8220;фреймворк&#8221; или &#8220;плагин&#8221;?

Оцените статью:  
<span id="post-ratings-1839" class="post-ratings" data-nonce="cf4ac49f05"><img id="rating_1839_1" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="1 Star" title="1 Star" onmouseover="current_rating(1839, 1, '1 Star');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1839_2" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="2 Stars" title="2 Stars" onmouseover="current_rating(1839, 2, '2 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1839_3" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="3 Stars" title="3 Stars" onmouseover="current_rating(1839, 3, '3 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1839_4" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="4 Stars" title="4 Stars" onmouseover="current_rating(1839, 4, '4 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1839_5" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="5 Stars" title="5 Stars" onmouseover="current_rating(1839, 5, '5 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /> (<strong>3</strong> votes, average: <strong>5,00</strong> out of 5)<br /><span class="post-ratings-text" id="ratings_1839_text"></span></span><span id="post-ratings-1839-loading" class="post-ratings-loading"> <img src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/loading.gif" width="16" height="16" alt="Loading..." title="Loading..." class="post-ratings-image" />Loading...</span>

 [1]: http://zell-weekeat.com/learnsusy/ "Learning Susy"
 [2]: https://www.dropbox.com/s/rug0kg3gae8aha2/sublime_russian_english_dictonary.zip?dl=0 "sublime_russian_english_dictonary.zip"
 [3]: http://localhost:7788/third/wp-content/uploads/2014/09/spellcheck_sublime_config.png