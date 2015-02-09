---
title: Pattern в качестве фонового изображения
author: gearmobile
excerpt: Использование pattern в Photoshop для правильного вырезания фонового изображения из psd-макета. Три способа вырезания изображения из макета в качестве фоновой картинки для HTML-шаблона.
layout: post
permalink: /pattern-photoshop/
cleanretina_sidebarlayout:
  - default
ratings_users:
  - 3
ratings_score:
  - 12
ratings_average:
  - 4
categories:
  - Photoshop для кодера
tags:
  - pattern
  - photoshop
---
Недавно познакомился с **тремя способами вырезания фонового изображения** на макете. До недавнего времени знал о существовании только одного способа, с которым познакомился еще на сайте htmlbook.ru.

Чтобы было яснее, рассмотрим пример psd-макета страницы:<figure id="attachment_1865" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/background_page-600x446.png" alt="Страница с фоновым изображением" width="600" height="446" class="size-medium wp-image-1865" />][1]<figcaption class="wp-caption-text">Страница с фоновым изображением</figcaption></figure> 

Видим, что на странице имеются множественные фоновые изображения. И как вы думаете, каким образом нужно вырезать такое изображение? Чтоб потом замостить им фон страницы или фон блока-контейнера?

До недавнего времени я бы сделал так. Попытался **визуально отыскать повторяющиеся фрагменты в фоне**, одном и втором. Если бы **удалось обнаружить** таковой фрагмент, то вырезал бы его с помощью инструмента Crop. Если бы фрагмент **не обнаружил**, то просто бы вырезал кусок фона размером побольше (что называется &#8211; *на глазок*), опять-таки, с помощью инструмента Crop.

Благодаря [Николаю Громову][2] (а немного позже &#8211; и <a href="http://www.adipurdila.com/" title="Adi Purdila" target="_blank">Adi Purdila</a>) я узнал, что существует **три подхода** к вырезанию фоновой картинки для будущего HTML-шаблона. Первые два способа &#8211; **простые** и **неточные**. Третий способ &#8211; более медленный, но **точный**.

Ниже последовательно рассмотрим все три способа, начиная с самого простого и заканчивая самым трудоемким.

Описание выполняемых действий приведено в локализованной версии Photoshop.

### Простое вырезание фона

Фон страницы на psd-макете представляет из себя растровое изображение, у которого имеется всего один слой. И при этом **визуально не получается выделить повторяющиеся фрагменты в этом фоне**.

В этом случае нужно поступить **только одним способом**.

**Свести воедино** все видимые слои с помощью сочетания клавиш **Shift+Ctrl+E**.

Инструментом **Crop** с зажатой клавишей Shift (чтобы получился квадрат) выделяем на фоне psd-макета квадрат побольше, размера 50x50px или 100x100px. Размер должен быть побольше именно для того, чтобы гарантировать бесшовность такого рисунка в фоне.

Затем экспортируем его в Web и используем в CSS для установки в качестве фонового изображения.

### Вырезание фрагмента фона

**Второй способ** отличается от первого лишь только тем, что на этот раз **удалось обнаружить** в рисунке фона макета **повторяющиеся фрагменты**. При этом фон макета все также является растровым изображением.

Инструментом **Crop** вырезаем из фона **обнаруженный фрагмент**, сохраняем его для Web и используем по назначению в CSS.

### Pattern в Photoshop

**Третий способ** основан на понятии **pattern** в Photoshop. Этот способ самый **точный** и **надежный**. В нем мы как-бы &#8220;опираемся&#8221; на силы самого Photoshop, который должен **помочь нам обнаружить pattern** в нарисованном дизайнером psd-макете. Я не дизайнер (и никогда им не буду), поэтому могу сказать по поводу того, что такое pattern **в двух словах**.

Это образец узора какого-то определенного размера (который может быть любым) &#8211; 102x102px, 20x20px или же 5x5px. Этот образец узора может быть любого рисунка (завитушки, полосочки, цветочки и т. д.). Вся задача pattern&#8217;а &#8211; служить образчиком, которым дизайнер выполняет **заливку слоя**. То есть, ситуация получается в точности такая, как у верстальщика. Имеется маленький кусочек рисунка, которым дизайнер &#8220;мостит&#8221; весь слой.

Задача верстальщика при нарезке psd-макета &#8211; выделить этот pattern из psd-макета в отдельное изображение. Чтобы увидеть, что в данном слое используется pattern, достаточно открыть палитру &#8220;Слои&#8221; и активировать нужный слой. В качестве примененных к слою эффектов должно стоять &#8220;Наложение узора&#8221;:<figure id="attachment_1867" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/bakground_layer_with_pattern-600x383.png" alt="Фоновый слой с pattern" width="600" height="383" class="size-medium wp-image-1867" />][3]<figcaption class="wp-caption-text">Фоновый слой с pattern</figcaption></figure> 

Все! Наша задача наполовину выполнена &#8211; мы знаем, что для этого слоя дизайнер применил pattern в качестве заливки каким-то там рисунком. Осталось только найти этот pattern, что является задачей чисто технической. И нам в этом поможет сам Photoshop.

Дважды кликаем мышкой по выбранному слою с фоновым рисунком. Откроется окно &#8220;Стиль слоя&#8221;, в котором активируем пункт &#8211; &#8220;Наложение узора&#8221;. В правой части окна будет показан конкретный pattern, с помощью которого дизайнер выполнял заливку данного слоя.

То есть, Photoshop показал, какой pattern использовал дизайнер в анализируемом нами слое. Нам осталось &#8220;вычленить&#8221; этот pattern и в этом нам снова поможет Photoshop:<figure id="attachment_1868" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/background_pattern-600x342.png" alt="Pattern для выбранного слоя" width="600" height="342" class="size-medium wp-image-1868" />][4]<figcaption class="wp-caption-text">Pattern для выбранного слоя</figcaption></figure> 

В этом же окне нужно навести курсор мыши на окошко с pattern&#8217;ом (окно &#8220;Узор&#8221;) и немного подождать, пока рядом с курсором мыши не появиться всплывающий tooltip, в котором будут показаны **размеры** данного pattern&#8217;а. Запоминаем (или записываем на листике бумаги <img src="http://localhost:7788/third/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> ) эти размеры &#8211; они нам понадобятся в дальнейшем.

Щелчком мыши на маленькой стрелочке справа от окна с образцом pattern&#8217;а открываем **палитру паттернов** (patterns):<figure id="attachment_1869" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/panel_patterns-600x343.png" alt="Палитра паттернов (patterns)" width="600" height="343" class="size-medium wp-image-1869" />][5]<figcaption class="wp-caption-text">Палитра паттернов (patterns)</figcaption></figure> 

В этой палитре нам необходимо **добавить** выбранный нами pattern в свою коллекцию паттернов. Это нужно для того, чтобы потом использовать этот pattern в своих &#8220;коварных&#8221; целях. Для этой цели кликаем на круглой кнопочке со стрелкой &#8211; *далее можно разобраться, что и как добавлять*.

Закрываем окно &#8220;Стиль слоя&#8221; и создаем новый документ (Ctrl+N) с размерами, как у нашего pattern&#8217;а:<figure id="attachment_1870" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/new_image-600x284.png" alt="Новое изображение с размерами pattern&#039;а" width="600" height="284" class="size-medium wp-image-1870" />][6]<figcaption class="wp-caption-text">Новое изображение с размерами pattern&#8217;а</figcaption></figure> 

Здесь самое главное &#8211; правильно **указать размеры** будущего документа (как правило, все pattern&#8217;ы имеют форму квадрата), все остальное для нас неважно. Создаем новый документ.

Затем в меню Photoshop переходим по пути &#8220;Слои&#8221; &#8211; &#8220;Новый слой-заливка&#8221; &#8211; &#8220;Узор &#8230;&#8221;. И в открывшемся окошке &#8220;Новый слой&#8221; просто кликаем по кнопке ОК, все остальное для нас опять неважно:<figure id="attachment_1871" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/new_layer_pattern-600x151.png" alt="Заливка нового слоя с помощью pattern&#039;а" width="600" height="151" class="size-medium wp-image-1871" />][7]<figcaption class="wp-caption-text">Заливка нового слоя с помощью pattern&#8217;а</figcaption></figure> 

Откроется еще одно окошко, в котором выбираем нужный нам pattern:<figure id="attachment_1872" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/select_pattern_for_layer-600x308.png" alt="Выбор pattern&#039;а для заливки слоя" width="600" height="308" class="size-medium wp-image-1872" />][8]<figcaption class="wp-caption-text">Выбор pattern&#8217;а для заливки слоя</figcaption></figure> 

Как результат получаем новый документ с заливкой слоя выбранным нами pattern&#8217;ом. Это хорошо заметно чисто визуально, в основном окне. В палитре &#8220;Слои&#8221; также видно, что к слою была применена **заливка узором**:<figure id="attachment_1873" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/10/new_image_background_ready-600x348.png" alt="Готовое изображение для фоновой заливки" width="600" height="348" class="size-medium wp-image-1873" />][9]<figcaption class="wp-caption-text">Готовое изображение для фоновой заливки</figcaption></figure> 

Картинка для фоновой заливки готова! Осталось только **экспортировать** ее для Web и применить на странице силами CSS.

Например, таким образом:

<pre>background-position: 0 0;
  background-repeat: repeat;
  background-image: url(../images/bg_body.png);
  </pre>

Все &#8211; задача выполнена!

### Заключение

Вот мы и познакомились с **тремя способами** вырезания фонового изображения из psd-макета.

Оцените статью:  
<span id="post-ratings-1863" class="post-ratings" data-nonce="055a5b86f4"><img id="rating_1863_1" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="1 Star" title="1 Star" onmouseover="current_rating(1863, 1, '1 Star');" onmouseout="ratings_off(4, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1863_2" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="2 Stars" title="2 Stars" onmouseover="current_rating(1863, 2, '2 Stars');" onmouseout="ratings_off(4, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1863_3" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="3 Stars" title="3 Stars" onmouseover="current_rating(1863, 3, '3 Stars');" onmouseout="ratings_off(4, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1863_4" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="4 Stars" title="4 Stars" onmouseover="current_rating(1863, 4, '4 Stars');" onmouseout="ratings_off(4, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1863_5" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_off.gif" alt="5 Stars" title="5 Stars" onmouseover="current_rating(1863, 5, '5 Stars');" onmouseout="ratings_off(4, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /> (<strong>3</strong> votes, average: <strong>4,00</strong> out of 5)<br /><span class="post-ratings-text" id="ratings_1863_text"></span></span><span id="post-ratings-1863-loading" class="post-ratings-loading"> <img src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/loading.gif" width="16" height="16" alt="Loading..." title="Loading..." class="post-ratings-image" />Loading...</span>

 [1]: http://localhost:7788/third/wp-content/uploads/2014/10/background_page.png
 [2]: http://nicothin.ru/
 [3]: http://localhost:7788/third/wp-content/uploads/2014/10/bakground_layer_with_pattern.png
 [4]: http://localhost:7788/third/wp-content/uploads/2014/10/background_pattern.png
 [5]: http://localhost:7788/third/wp-content/uploads/2014/10/panel_patterns.png
 [6]: http://localhost:7788/third/wp-content/uploads/2014/10/new_image.png
 [7]: http://localhost:7788/third/wp-content/uploads/2014/10/new_layer_pattern.png
 [8]: http://localhost:7788/third/wp-content/uploads/2014/10/select_pattern_for_layer.png
 [9]: http://localhost:7788/third/wp-content/uploads/2014/10/new_image_background_ready.png