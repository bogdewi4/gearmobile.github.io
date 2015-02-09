---
title: 'Что выбрать &#8211; Compass или Bourbon?'
author: gearmobile
excerpt: 'Время от времени в Twitter, Reddit или StackOverflow возникает такой вопрос. Почти каждый, кто работал с Sass хотя бы раз задавал его себе - что выбрать, <a href="http://compass-style.org/" title="Compass">Compass</a> или <a href="http://bourbon.io/" title="Bourbon">Bourbon</a>? В этой статье я выскажу свое мнение по поводу использования Compass или Bourbon.'
layout: post
permalink: /compass-or-bourbon/
cleanretina_sidebarlayout:
  - default
ratings_users:
  - 2
ratings_score:
  - 10
ratings_average:
  - 5
categories:
  - Статьи по CSS
tags:
  - bourbon
  - compass
---
Время от времени в Twitter, Reddit или StackOverflow возникает такой вопрос. Почти каждый, кто работал с Sass хотя бы раз задавал его себе &#8211; что выбрать, [Compass][1] или [Bourbon][2]?

Оба проекта Compass и Bourbon являются фреймворками под Sass. Sass, как вы помните, является препроцессором CSS, не правда ли? Хорошо. Точно также, как если бы вы имели дело с jQuery или Backbone при работе в JavaScript, использование фреймворка для Sass облегчает работу с последним.

В этой статье я выскажу свое мнение по поводу использования Compass или Bourbon. Но, прежде всего, нужно сделать небольшой экскурс в историю.

### История Compass и Bourbon

Compass заявляет о себе как о CSS фреймворке под Sass. Он поддерживается [Chris Eppstein][3], одним из двух разработчиков Sass (Ruby-версия). Compass &#8211; это наполовину Ruby и наполовину Sass, он представляет из себя полный набор миксинов и инструмент под Sass. Более подробно о нем позже.

С другой стороны, Bourbon создан на Sass и для Sass великолепной командой разработчиков [Thoughtbot][4]. Если верить домашней странице проекта, Bourbon &#8211; это скорее библиотека, нежели фреймворк; простая и легковесная библиотека миксинов под Sass.

В итоге мы имеем с одной стороны Ruby/Sass фреймворк, а с другой стороны мы имеем библиотеку Sass. Совершенно разные вещи, не правда ли?

### Миксины Compass и Bourbon

Если спросить пользователя Compass/Bourbon, для какой цели он использует данный инструмент, высоки шансы услышать однозначный ответ: для *кросс-браузерной совместимости*. Возможно, он ответит не совсем так, но ответ будет иметь приблизительно такой же смысл. Как Compass, так и Bourbon являются огромной коллекцией миксинов для создания CSS3-эффектов; благодаря этим миксинам отпадает необходимость детально вникать в браузерные префиксы или CSS-уловки (CSS hacks).

Ниже показан пример миксина `box-sizing` в обоих библиотеках Compass и Bourbon. Как видим, синтаксис и результат работы одинаков:

<pre>// Compass

  .boxsizing {
    @include box-sizing(border-box);
  }

  // Bourbon

  .boxsizing {
    @include box-sizing(border-box);
  }
</pre>

Тот факт, что Compass и Bourbon имеют одинаковый синтаксис для большинства миксинов, делает переход в использовании с Compass на Bourbon и с Bourbon на Compass очень легким.

Существует одно важное различие между этими инструментами: начиная с Compass 1.0 (вышел совместно с Sass 3.3), Compass [получает][5] информацию с сайта [Can I Use][6]. Это означает, что почти всегда данный фреймворк получает самую свежую информацию по браузерным префиксам. В то время как библиотека Bourbon полностью зависит от обновлений, выпускаемых разработчиками данной библиотеки.

Замечание: если вы используете [Autoprefixer][7] для решения вопросов браузерных префиксов, то все вышесказанное не относится к вам.

### Типографика в Compass и Bourbon

Оба &#8211; Compass и Bourbon &#8211; предоставляют набор готовых миксинов, переменных и функций для работы с типографикой. Помимо этого, Compass имеет в своем составе полноценный модуль для создания вертикального ритма, включая набор переменных и пару миксинов:

<pre>// Compass Vertical Rhythm
  $base-font-size: 16px;
  $base-line-height: 1.35;
  $rhythm-unit: em;

  element{
    @include adjust-font-size-to(42px);
  }

  // CSS result
  element{
    font-size: 2.625em;
    line-height: 1.06071em;
  }
</pre>

У Compass также есть возможность поддержки единиц измерения `rem` с откатом к `px`, если вы используете `rem` в качестве значения переменной `$rhythm-unit` вместо `em`. Есть еще [целая куча различных настроек][8], так что если вы являетесь поклонником типографики, Compass сможет ответить всем вашим требованиям.

Библиотека Bourbon обладает менее впечатляющим набором возможностей для работы с типографикой; однако у нее также есть все для быстрого старта разработки. В Bourbon есть не только возможность преобразования пикселей в `em` или `rem`, но также такие великолепные функции, как `golden-ratio()` и `modular-scale()`. Несмотря на то, что эти функции не имеют прямого отношения к типографике, они отлично подходят для создания вертикального ритма в документе.

Собственно, Thoughtbot решили адресовать вопрос с типографикой другому их проекту (который может использоваться совместно с Bourbon) под названием [Bitters][9]. Более подробно о нем будет говориться в конце статьи.

### CSS-сетки в Compass и Bourbon

Разве можно назвать фреймворк полноценным, если у него нет системы сеток (grid system), верно?

Фреймворк Compass имеет в составе систему [Blueprint Grid][10], которая, насколько я знаю, не имеет ничего общего со старым фреймворком под названием Blueprint. Стоит сказать, что система Blueprint фреймворка Compass является неполноценной. Среди всех людей, которые используют Compass и с которыми мне приходилось общаться, только один пробовал работать с Blueprint. Эта система настолько несовершенна, что Chris Eppstein решил убрать ее из Compass начиная с версии 1.0.0 (что соответствует Sass 3.3).

В тоже время библиотека Bourbon предоставляет пару миксинов, с помощью которых можно создать свою собственную сетку. Это [функции][11] `flex-*` (не стоит путать с моделью Flexbox) и `grid-width()`. Помимо этого, у команды Thoughtbot имеется своя собственная, отдельная от Bourbon, система сеток под названием [Neat][12], которая позиционируется как легковесный семантичный фреймворк под Sass и Bourbon. Таким образом, библиотека Bourbon не имеет в своем составе системы сеток (grid system), но можно свободно воспользоваться для этой цели фреймворком Neat.

Если сделать краткий итог по вопросу системы сеток, то можно сказать следующее. Если необходима система сеток с тесной интеграцией Sass-фреймворка, то мое мнение &#8211; это использовать связку Bourbon + Neat. Оба проекта были созданы одними и теми же людьми; в обоих проектах была заложена одна и таже основная идея. Это можно сравнить как два кусочка одного пазла.

> Примечание переводчика: автор статьи упоминает о стороннем проекте Neat (система сеток) для библиотеки Bourbon. Но почему-то ни словом не говорит о проекте [Susy][13]?

### Helpers

Одной интересной вещью Sass-фреймворков являются так называемые *helpers*. *Helpers* &#8211; это предустановленные CSS-правила, которые можно использовать в таблицах стилей как есть, для сокращения времени разработки проекта.

Например, Compass имеет набор *helpers* для [float-clearing][14] (включая несколько способов, как это сделать) и несколько CSS-хаков для старых версий браузера Internet Explorer; сброс стилей (несколько вариантов); несколько способов замещения текста изображением и [многое другое][15].

В Bourbon такие *helpers* называются [add-ons][16], но они выполняют туже работу; правда, в Bourbon их немного меньше, чем в Compass. Стоит сказать, что команда Thoughtbot включила с состав проекта [Bitters][9] большое количество *helpers*. Как было уже сказано выше, Bitters является сторонним проектом, который имеет прекрасную интеграцию с Bourbon и служит для целей создания типографики в проекте.

### Спрайты Compass и Bourbon

Спросите пользователя Compass, почему он из месяца в месяц и из года в год использует эту библиотеку; клянусь, что в ответ услышим что-то о системе создания спрайтов. Это та вещь, которую Compass действительно выполняет хорошо. Благодаря тому, что Compass написан на языке Ruby, он может выполнять некоторые очень интересные вещи с файловой системой. Одной из таких фишек является способность создавать спрайты из коллекции изображений, размещенных в одной папке. Замечательно, не правда ли?

<pre>// Пример создания спрайтов в Compass
  @import "icon/*.png";
  @include all-icon-sprites;
</pre>

Помимо автомагического способа генерации спрайтов, Compass предоставляет пару интересных функций для доступа к файлу изображений прямо из таблицы стилей, наподобие `image-width()`, `image-height()` и даже `inline-image()` для преобразования файла изображения в Base64:

<pre>// Функции Compass доступа к файловой системе
  .logo{
    $image: "path/to/my/logo.png";
    width: image-width($image);
    height: image-height($image);
    background: inline-image($image) no-repeat;
  }
</pre>

Так как Bourbon построен только на Sass, у него нет возможности доступа к файловой системе и эта библиотека не может выполнить таких вещей, какие может Compass. Поэтому, если вы ищете способ динамического создания спрайтов и не хотите заморачиваться с такими менеджерами задач, как [Grunt][17], [Gulp][18] или [Ant][19], то выбор для вас очевиден.

### Резюме

Ниже представлена таблица, в которой суммировано все, о чем говорилось выше:<table style="height: 202px;" width="772px"; border="1px"> 

</table> 

### Итог

И так, что же получаем в итоге &#8211; Compass или Bourbon?

Если спросить об этом меня, то я отвечу: *никакой из них*. Долгое время я был пользователем библиотеки Compass, покуда не отказался от его применения. На сегодняшний день я предпочитаю добавлять в создаваемый Sass-проект свои собственные инструменты, нежели использовать весь фреймворк целиком. Но это что касается меня лично. Я думаю, что в большинстве случаев было бы лучше использовать весь фреймворк, по крайней мере, в случае больших проектов.

Поэтому я считаю, что имеется только два критерия, которые должны решать для вас вопрос выбора. И главным среди этих двух критериев является следующий (*который вы должны задать самому себе*): ***нужны ли мне возможности по обработке изображений (размеры изображений, спрайты и так далее)?***

Библиотека Compass великолепно подходит для этих целей, но она выполняет свою задачу медленно, слишком медленно&#8230; Поэтому, если вас не устраивает такой факт, то посмотрите в сторону Bourbon. Эта библиотека замечательно быстрая хотя бы потому, что состоит из одних Sass-миксинов, выполняющих задачи Sass внутри таблиц стилей Sass.

Если вы решили использовать библиотеку Bourbon, то я бы рекомендовал вам также задействовать другие проекты команды Thoughtbot: [Neat][12] в качестве системы сеток (grid system), [Bitters][9] для типографики и еще не упомянутый до этого момента [Refills][20] (который является полной альтернативой фреймворка [Bootstrap][21]) с полным набором компонентов, готовый для использования в создаваемом проекте.

> Примечание переводчика: в этой статье дан сравнительный обзор двух фреймворков &#8211; Compass и Bourbon. Лично для меня было бы интереснее посмотреть практические примеры использования библиотеки Bourbon.

Оригинал статьи:  
[Sass Frameworks: Compass or Bourbon?][22] от автора [Hugo Giraudel][23].

На этом перевод закончен:  
<span id="post-ratings-1340" class="post-ratings" data-nonce="29238f3c5b"><img id="rating_1340_1" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="1 Star" title="1 Star" onmouseover="current_rating(1340, 1, '1 Star');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1340_2" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="2 Stars" title="2 Stars" onmouseover="current_rating(1340, 2, '2 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1340_3" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="3 Stars" title="3 Stars" onmouseover="current_rating(1340, 3, '3 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1340_4" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="4 Stars" title="4 Stars" onmouseover="current_rating(1340, 4, '4 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1340_5" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="5 Stars" title="5 Stars" onmouseover="current_rating(1340, 5, '5 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /> (<strong>2</strong> votes, average: <strong>5,00</strong> out of 5)<br /><span class="post-ratings-text" id="ratings_1340_text"></span></span><span id="post-ratings-1340-loading" class="post-ratings-loading"> <img src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/loading.gif" width="16" height="16" alt="Loading..." title="Loading..." class="post-ratings-image" />Loading...</span>

 [1]: http://compass-style.org/ "Compass"
 [2]: http://bourbon.io/ "Bourbon"
 [3]: https://twitter.com/chriseppstein "Chris Eppstein"
 [4]: http://thoughtbot.com/ "Thoughtbot"
 [5]: https://twitter.com/chriseppstein/status/468393998734745600 "получает"
 [6]: http://caniuse.com/ "Can I Use"
 [7]: https://github.com/ai/autoprefixer "Autoprefixer"
 [8]: http://compass-style.org/reference/compass/typography/vertical_rhythm/ "целая куча различных настроек"
 [9]: http://bitters.bourbon.io/ "Bitters"
 [10]: http://compass-style.org/reference/blueprint/grid/ "Blueprint Grid"
 [11]: http://bourbon.io/docs/#flex-grid "функции"
 [12]: http://neat.bourbon.io/ "Neat"
 [13]: http://susy.oddbird.net/ "Susy"
 [14]: http://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/ "float-clearing"
 [15]: http://compass-style.org/reference/compass/utilities/general/ "многое другое"
 [16]: http://bourbon.io/docs/#add-ons "Bourbon add-ons"
 [17]: http://gruntjs.com/ "Grunt"
 [18]: http://gulpjs.com/ "Gulp"
 [19]: http://ant.apache.org/ "Ant"
 [20]: http://refills.bourbon.io/ "Refills"
 [21]: http://getbootstrap.com/ "Bootstrap"
 [22]: http://www.sitepoint.com/compass-or-bourbon-sass-frameworks/ "Sass Frameworks: Compass or Bourbon?"
 [23]: http://hugogiraudel.com/ "Hugo Giraudel"