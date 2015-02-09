---
title: 'Photoshop &#8211; вырезать изображение из рамки (stroke)'
author: gearmobile
layout: post
permalink: /photoshop-%d0%b2%d1%8b%d1%80%d0%b5%d0%b7%d0%b0%d1%82%d1%8c-%d0%b8%d0%b7%d0%be%d0%b1%d1%80%d0%b0%d0%b6%d0%b5%d0%bd%d0%b8%d0%b5-%d0%b8%d0%b7-%d1%80%d0%b0%d0%bc%d0%ba%d0%b8-stroke/
cleanretina_sidebarlayout:
  - default
ratings_users:
  - 4
ratings_score:
  - 20
ratings_average:
  - 5
categories:
  - Photoshop для кодера
tags:
  - photoshop
  - stroke
---
На практике верстки часто встречаются ситуации, когда нужно вырезать изображение с рамкой. Ну и что, скажете вы &#8211; что там может быть сложного? В принципе, ничего. Но ситуация осложняется тем, что рамка в таких изображениях очень часто выполнена в виде обводки с эффектом наложения. Что это значит? Это означает, что поверх существующего изображения дизайнер наносит линию определенной толщины, которая располагается по краю этого изображения.

Что же получается? Выходит, нужно вырезать изображение, расположенное внутри рамки. Ведь если просто отключить в Photoshop эффект обводки, картинка получиться больше за счет того, что появятся скрытые под рамкой лишние пиксели. Такое изображение нельзя вставлять в код, так как оно не соответствует psd-макету. Средствами CSS невозможно создать границу border, чтобы она накладывалась на контент. По спецификации CSS граница может располагаться только рядом с контентом, но не поверх. Кстати, есть еще одна статья, посвященная проблеме обводки &#8211; &#8220;[Преобразовываем обводку из Photoshop в CSS][1]&#8220;. Но в ней описывается случай, когда изображение можно оставить как есть, только добавив к нему внешнюю границу в коде CSS.

Как же можно поступить в данном случае? Для себя нашел такой выход. Отключаю эффект обводки для картинки, затем обрезаю ее по краям на толщину обводки, и уже сохраняю изображение для последующей вставки в код. Мне такой способ кажется точным и аккуратным.

В Photoshop есть инструмент &#8220;Рамка&#8221; (Crop), предназначенный как раз для вырезания элементов из psd-макета или обрезки изображений. В подавляющем большинстве всяческих руководств описывается только один способ использования этого инструмента. Который можно назвать &#8220;ручным&#8221;, так как область выделения обозначается вручную, с помощью мыши. Но обрезку изображения можно выполнить более точным образом, с помощью инструмента &#8220;Размер холста&#8221;. В этом случае конкретно устанавливается размер рамки и ее расположение на картинке. Все, что находится за пределами рамки, будет обрезано.

Ну, хватит говорить, а лучше посмотрим на живой пример. Ниже показан масштабированный фрагмент psd-макета &#8211; картинка симпатичного льва, с рамкой в виде обводки:<figure id="attachment_298" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2013/10/img01-600x342.jpg" alt="Изображение с обводкой в Photoshop" width="600" height="342" class="size-medium wp-image-298" />][2]<figcaption class="wp-caption-text">Изображение с обводкой в Photoshop</figcaption></figure> 

Чтобы не гадать, так ли это, посмотрим на палитру слоев. Видно, что слой со львом имеет дополнительный стиль &#8220;Эффекты &#8211; Выполнить обводку&#8221;. Давайте узнаем, с какими параметрами художник создал данную обводку. Двойным щелчком мыши кликаем на самом слое в палитре, после чего появится окно настроек стилей. Там их много, но включен только один, напротив которого стоит галочка:<figure id="attachment_299" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2013/10/img02-600x347.jpg" alt="Стиль слоя Обводка в Photoshop" width="600" height="347" class="size-medium wp-image-299" />][3]<figcaption class="wp-caption-text">Стиль слоя Обводка в Photoshop</figcaption></figure> 

Какие же характеристики дизайнер задал для обводки? Совсем несложные &#8211; размер в 3 пикселя, положение &#8211; внутри (о чем и говорилось ранее &#8211; рамка смещена внутрь изображения, то есть, расположена поверх него), цвет обводки &#8211; какой-то оттенок желтого. Хорошо. Теперь мы знаем, что нам необходимо обрезать изображение льва по краям на толщину в 3 пикселя.

Отключаю в палитре слоев эффект обводки и выделяю &#8220;чистое&#8221; изображение льва прямоугольным выделением:<figure id="attachment_300" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2013/10/img03-600x360.jpg" alt="Отключенный эффект обводки в Photoshop" width="600" height="360" class="size-medium wp-image-300" />][4]<figcaption class="wp-caption-text">Отключенный эффект обводки в Photoshop</figcaption></figure> 

Копирую выделение в новый документ, чтобы случайно не повредить оригинал psd-макета. Нажимаю сочетание клавиш Ctrl+A, выделив тем самым всю картинку. Мне это нужно для получения размеров нашего льва. Видим, что ширина и высота изображения равны 118 на 95 пикселей. Значит, обрезку по краям необходимо выполнить на величину в 6 пикселей. Толщина обводки ведь равна 3 пикселям, по горизонтали и вертикали она расположена с обеих сторон картинки. Поэтому &#8211; 118px &#8211; 3px\*2 = 112px, 95px &#8211; 3px\*2 = 89px. Получили размеры ширины и высоты рамки, которую будем использовать в инструменте &#8220;Размер холста&#8221;:<figure id="attachment_301" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2013/10/img04-600x374.jpg" alt="Размеры скопированного изображения в Photoshop" width="600" height="374" class="size-medium wp-image-301" />][5]<figcaption class="wp-caption-text">Размеры скопированного изображения в Photoshop</figcaption></figure> 

Перехожу в меню &#8220;Изображение &#8211; Размер холста&#8221;. Откроется небольшое окно, в котором я введу полученные значения ширины и высоты для рамки. Также проверю, чтобы рамка располагалась по центру изображения:<figure id="attachment_302" style="width: 519px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2013/10/img05.jpg" alt="Размеры холста в Photoshop" width="519" height="357" class="size-full wp-image-302" />][6]<figcaption class="wp-caption-text">Размеры холста в Photoshop</figcaption></figure> 

Жму ОК, чтобы применить изменения. Photoshop выдаст предупреждающее сообщение о том, что новый размер холста меньше оригинала, поэтому часть изображения будет усечена (обрезана). Ну, так мы этого и добиваемся, не правда ли? Соглашаюсь и получаю картинку нашего льва, которая уменьшена на заданную величину. Чтобы проверить это, снова нажимаю сочетание клавиш Ctrl+A и смотрю на палитру &#8220;Инфо&#8221;. Точно &#8211; картинка имеет те самые размеры, которые необходимы:<figure id="attachment_303" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2013/10/img07-600x388.png" alt="Обрезанное изображение в Photoshop" width="600" height="388" class="size-medium wp-image-303" />][7]<figcaption class="wp-caption-text">Обрезанное изображение в Photoshop</figcaption></figure> 

Все, задача выполнена. Теперь картинку льва можно вставлять в код и прописать для него CSS-правила, наподобие таких:

<pre>img {border: 3px solid #fde40b};</pre>

Существует еще одна разновидность вырезания с помощью инструмента &#8220;Рамка&#8221;. Он больше похож на &#8220;ручной&#8221; способ. Для этого используются направляющие (guidelines), которые задают границы будущей обрезки. Но мне такой способ кажется более трудоемким, времязатратным и менее точным. Это же нужно построить аж 8 направляющих, и при этом не промахнуться, точно попасть на границы обводки. Иногда бывает, что обводка нарисована каким-то странным образом, как в данном случае:<figure id="attachment_304" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2013/10/img08-1-600x369.png" alt="Странные разводы обводки в Photoshop" width="600" height="369" class="size-medium wp-image-304" />][8]<figcaption class="wp-caption-text">Странные разводы обводки в Photoshop</figcaption></figure> 

Если замерить толщину обводки там, где есть эти непонятные мне разводы, то получиться толщина не 3 пикселя, а 4 пикселя. Несоответствие получается, однако. Ну, а дальше все как обычно &#8211; &#8220;Crop + Выделить участок изображения + Enter&#8221;.

Оцените статью:  
<span id="post-ratings-296" class="post-ratings" data-nonce="eab838eaf9"><img id="rating_296_1" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="1 Star" title="1 Star" onmouseover="current_rating(296, 1, '1 Star');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_296_2" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="2 Stars" title="2 Stars" onmouseover="current_rating(296, 2, '2 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_296_3" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="3 Stars" title="3 Stars" onmouseover="current_rating(296, 3, '3 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_296_4" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="4 Stars" title="4 Stars" onmouseover="current_rating(296, 4, '4 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_296_5" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="5 Stars" title="5 Stars" onmouseover="current_rating(296, 5, '5 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /> (<strong>4</strong> votes, average: <strong>5,00</strong> out of 5)<br /><span class="post-ratings-text" id="ratings_296_text"></span></span><span id="post-ratings-296-loading" class="post-ratings-loading"> <img src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/loading.gif" width="16" height="16" alt="Loading..." title="Loading..." class="post-ratings-image" />Loading...</span>

 [1]: http://localhost:7788/third/?p=100 "Преобразовываем обводку из Photoshop в CSS"
 [2]: http://localhost:7788/third/wp-content/uploads/2013/10/img01.jpg
 [3]: http://localhost:7788/third/wp-content/uploads/2013/10/img02.jpg
 [4]: http://localhost:7788/third/wp-content/uploads/2013/10/img03.jpg
 [5]: http://localhost:7788/third/wp-content/uploads/2013/10/img04.jpg
 [6]: http://localhost:7788/third/wp-content/uploads/2013/10/img05.jpg
 [7]: http://localhost:7788/third/wp-content/uploads/2013/10/img07.png
 [8]: http://localhost:7788/third/wp-content/uploads/2013/10/img08-1.png