---
title: 'Rupture &#8211; система breakpoint под Stylus'
author: gearmobile
excerpt: 'Rupture - простая и гибкая система контрольных точек (breakpoints) под Stylus. Установка Rupture, обзор нужных миксинов. Несколько интересных возможностей.'
layout: post
permalink: /rupture-breakpoints-stylus/
ratings_users:
  - 2
ratings_score:
  - 10
ratings_average:
  - 5
categories:
  - Кодинг
tags:
  - breakpoint
  - rupture
  - stylus
---
> Краткое знакомство с системой контрольных точек Rupture под препроцессор Stylus.

Ниже приведено краткое и сбивчивое <img src="http://localhost:7788/third/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" /> описание (*знакомство*) с системой breakpoints под препроцессор Stylus. Оно основано на двух материалах, оба являющихся официальными:

  * [rupture on GitHub][1]
  * [Rupture &#8211; official project][2]

А больше в Сети материалов по Rupture и нет, даже на английском языке. Есть, правда, очень краткий &#8211; на французском, которым я совсем не владею <img src="http://localhost:7788/third/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />

Rupture был создан на примере плагина [Breakpoint Slicer][3] под препроцессор Sass.

### Шкала Rupture

Основа Rupture &#8211; шкала значений breakpoints, которая так и называется &#8211; `scale`. Фактически `scale` &#8211; это объект со своими свойствами и методами. Перечень контрольных точек (breakpoints) &#8211; это массив значений, передаваемых объекту `scale`.

Ниже представлена `scale` по умолчанию (*но которую можно легко изменить при необходимости*):

<pre>scale = 0 400px 600px 800px 1050px 1800px</pre>

Количество этих значений &#8211; `0, 400px, 600px 800px, 1050px` &#8211; может быть необязательно равно 5 (пяти). Их может быть неограниченное количество &#8211; столько, сколько нужно.

Перечень значений breakpoints, показанных выше, можно представить в виде диапазонов; каждому диапазону можно присвоить порядковый номер `slice number` и &#8220;обозвать&#8221; как `slice`:<figure id="attachment_2206" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2015/01/scale_rupture-600x102.png" alt="Rupture Scale" width="600" height="102" class="size-medium wp-image-2206" />][4]<figcaption class="wp-caption-text">Rupture Scale</figcaption></figure> 

Подключать библиотеку Rupture в проект **нет необходимости**. Достаточно установить библиотеку командой:

<pre>$ sudo npm install rupture --global</pre>

После этого Rupture готова к использованию. Можно запустить компиляцию из командной строки (*не рекомендуется*):

<pre>$ stylus -u rupture -c example.styl</pre>

Здесь `-c` &#8211; это сокращение от `--compress`, то есть &#8211; минифицировать CSS-код на выходе. Почему не рекомендуется использовать командную строку? Просто для этих целей лучше (*и целесообразнее*) использовать Gulp.

### Миксины Rupture

В Rupture все управляется **миксинами**. Есть заранее созданный набор миксинов, которые необходимо применять для определенного случая (breakpoints).

Все миксины Rupture делятся на **два вида**:

  * **простые миксины** для практического использования каждый день
  * **сложный набор миксинов**, которые фактически представляют из себя grid sistem

В этом кратком обзоре я буду рассматривать только &#8220;практические&#8221; миксины. Более сложные &#8211; нет, ибо &#8220;не зачем&#8221;.

#### Набор практических миксинов Rupture

Первые три миксина &#8211; **наиболее применимые** и удобные на практике.

**+above(measure)**  
&#8211; если размер окна браузера **больше** указанного значения (`> measure`), то применить стили  
&#8211; `+from-width(measure)` &#8211; это алиас миксина **+above(measure)**

**+below(measure)**  
&#8211; если размер окна браузера **меньше** указанного значения (`< measure`), то применить стили  
- `+to-width(measure)` - это алиас миксина **+below(measure)**

**+between(measure1, measure2)**  
- если размер окна браузера находится в указанных пределах (`measure1 <= between <= measure2`), то применить стили

Дальше пошли миксины - "по обстоятельствам".

**+at(measure)**  
- если размер окна браузера `>=` указанного значения, то применить стили

**+mobile()**  
- если размер окна браузера `<= 400px`, то применить стили  
- `rupture.mobile-cutoff` - переменная, в которой хранится значение для миксина mobile()

**+tablet()**  
- если размер окна браузера находится в пределах `>= 1050px` и `< 400px`, то применить стили

**+desktop()**  
- если размер окна браузера `> 1050px`, то применить стили  
- `rupture.desktop-cutoff` - переменная, в которой хранится значение для миксина desktop()

**+hd()**  
- если размер окна браузера `>=` 1800px, то применить стили  
- `rupture.hd-cutoff` - переменная, в которой хранится значение для миксина hd()

**+retina()**  
- если плотность размещения пикселей больше 1.5 (retina display), то применить стили

**+landscape()**  
- если у окна браузера **высота меньше, чем ширина**, то применить стили

**+portrait()**  
- если у окна браузера **высота больше, чем ширина**, то применить стили

### Настройка Rupture

Как любая система, Rupture имеет свои собственные настройки. Которые можно задавать в файле проекта в виде **переменных** с их значениями.

К примеру, Rupture имеет возможность **автоматического конвертирования** значений breakpoints из пикселей (px) в em. Как говорится в официальном руководстве, в веб-разработке существует мнение, что задавать контрольные точки в em - это хорошая практика.

Поэтому, такой пример иллюстрирует **включение автоматической конвертации** из px в em; и задание базового размера шрифта в 18px (*базовый размер шрифта равен 16px*):

<pre>// Stylus

rupture.enable-em-breakpoints = true
base-font-size = 18px
</pre>

**rupture.scale** - одна из **важнейших переменных** Rupture. В этой переменной можно в виде массива переопределить значения breakpoints.

Например, таким образом:

<pre>rupture.scale = 0 380px 768px 1200px</pre>

### Пример работы Rupture

Перейдем от теории к практике и рассмотрим маленький рабочий пример - как будет *отрабатывать* Rupture:

<pre>// Jade

div.wrapper
  div.left
  div.right
</pre>

<pre>// Stylus

@import 'nib'
@import 'jeet'

// Partials
@import 'partials/*.styl'

rupture.enable-em-breakpoints = true

.wrapper
  center()

.left
  col(1/3)
  height 20vh
  background-color lighten($color,10%)
  +below(800px)
    col(1/4)
    background-color lighten($color,20%)
  +below(400px)
    stack()
    margin-bottom 10px

.right
  col(2/3)
  height 20vh
  background-color lighten($color,20%)
  +below(800px)
    col(3/4)
    background-color lighten($color,30%)
  +below(400px)
    stack()
</pre>

Комментировать вышеприведенный код мне как-то не особого желания. Он очень простой и наглядный - слова тут излишни.

Кроме одного вопроса, который чуть не забыл упомянуть! В этом коде (*и всех примерах выше*) применялось точное значение для миксинов - `+below(400px)`, к примеру.

Но ничто не мешает использовать любые **произвольные переменные**, в которые можно "загружать" нужные значения. К примеру, код выше можно преобразовать таким образом:

<pre>// Stylus

@import 'nib'
@import 'jeet'

// Partials
@import 'partials/*.styl'

// Breakpoint Variables
$bp1 = 800px
$bp2 = 400px

rupture.enable-em-breakpoints = true

.wrapper
  center()

.left
  col(1/3)
  height 20vh
  background-color lighten($color,10%)
  +below($bp1)
    col(1/4)
    background-color lighten($color,20%)
  +below($bp2)
    stack()
    margin-bottom 10px

.right
  col(2/3)
  height 20vh
  background-color lighten($color,20%)
  +below($bp1)
    col(3/4)
    background-color lighten($color,30%)
  +below($bp2)
    stack()
</pre>

### Заключение Rupture

Вот я и познакомился с Rupture. Что можно сказать - система мне (*в очередной раз - все из мира Stylus*) понравилась, она очень проста и наглядна. Достаточно полчаса, чтобы ознакомиться с ее возможностями и начать применять на практике.

Оцените статью:  
<span id="post-ratings-2205" class="post-ratings" data-nonce="95e4bccd2e"><img id="rating_2205_1" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="1 Star" title="1 Star" onmouseover="current_rating(2205, 1, '1 Star');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_2205_2" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="2 Stars" title="2 Stars" onmouseover="current_rating(2205, 2, '2 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_2205_3" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="3 Stars" title="3 Stars" onmouseover="current_rating(2205, 3, '3 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_2205_4" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="4 Stars" title="4 Stars" onmouseover="current_rating(2205, 4, '4 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_2205_5" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="5 Stars" title="5 Stars" onmouseover="current_rating(2205, 5, '5 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /> (<strong>2</strong> votes, average: <strong>5,00</strong> out of 5)<br /><span class="post-ratings-text" id="ratings_2205_text"></span></span><span id="post-ratings-2205-loading" class="post-ratings-loading"> <img src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/loading.gif" width="16" height="16" alt="Loading..." title="Loading..." class="post-ratings-image" />Loading...</span>

 [1]: http://jenius.github.io/rupture/ "rupture"
 [2]: https://github.com/jenius/rupture "Rupture"
 [3]: https://github.com/lolmaus/breakpoint-slicer "Breakpoint Slicer"
 [4]: http://localhost:7788/third/wp-content/uploads/2015/01/scale_rupture.png