---
title: 'Photoshop Marquee Tool &#8211; измерение размеров элементов'
author: gearmobile
layout: post
permalink: /photoshop-marquee-tool-%d0%b8%d0%b7%d0%bc%d0%b5%d1%80%d0%b5%d0%bd%d0%b8%d0%b5-%d1%80%d0%b0%d0%b7%d0%bc%d0%b5%d1%80%d0%be%d0%b2-%d1%8d%d0%bb%d0%b5%d0%bc%d0%b5%d0%bd%d1%82%d0%be%d0%b2/
cleanretina_sidebarlayout:
  - default
ratings_users:
  - 2
ratings_score:
  - 10
ratings_average:
  - 5
categories:
  - Photoshop для кодера
tags:
  - photoshop
---
При верстке макета сайта одним из наиболее важных моментов является точное измерение размеров элементов на psd-шаблоне. Без знания, какие размеры имеют логотип, кнопки навигации, навигационное меню и т. д. невозможно сверстать макет сайта в точности, как он задуман дизайнером в шаблоне. А если нет точности при верстке, но и работа верстальщика (сайт) будет неряшливым.

Об одном из инструментов измерения размеров на psd-шаблоне я уже рассказывал &#8211; &#8220;[Линейка в Photoshop][1]&#8220;. Но программа Photoshop очень богата возможностями. Поэтому этот способ не является единственным. Сегодня будет показан еще один способ измерения размеров &#8211; с помощью инструмента Rectangular Marquee Tool.

Допустим, у нас имеется некий psd-макет, который необходимо порезать в Photoshop. И на этом макете нам необходимо узнать высоту шапки будущего сайта, то есть там, где располагается логотип. Открываем psd-шаблон, масштабируем его, чтобы шапка макета была крупной и нам было удобно с ней работать.

Затем переводим взгляд на панель инструментов Photoshop и на ней выбираем щелком мыши инструмент Rectangular Marquee Tool:

[<img class="size-full wp-image-450 aligncenter" alt="marquee tool" src="http://localhost:7788/third/wp-content/uploads/2013/04/marquee_tool.png" width="54" height="252" />][2]

Теперь аккуратно выделяем логотип на psd-шаблоне, чтобы границы выделения точно совпали с верхней границей самого макета и нижней границей навигационной панели. Таким образом достигается точность измерений. В результате логотип выделяется пунктирной линией. Это подсказка для нас, что он выделен и где именно проходят границы выделения. Проверяем, что все так, как и было задумано:

<figure id="attachment_451" style="width: 600px;" class="wp-caption aligncenter">

[<img class="size-medium wp-image-451" alt="selected element" src="http://localhost:7788/third/wp-content/uploads/2013/04/selected_element-600x331.png" width="600" height="331" />][3]<figcaption class="wp-caption-text">selected element</figcaption></figure>

Большая часть дела уже была сделана. Теперь осталось узнать размеры выделенной области.

Для этого необходимо, чтобы была активирована панель Инфо. Если ее нет, необходимо включить ее через меню &#8220;Window &#8211; Info (F8)&#8221;. На этой панели в правом нижнем разделе показываются геометрические размеры выделенного элемента (W &#8211; ширина, H &#8211; высота):

<figure id="attachment_452" style="width: 239px;" class="wp-caption aligncenter">

[<img class="size-full wp-image-452" alt="element size" src="http://localhost:7788/third/wp-content/uploads/2013/04/element_size.png" width="239" height="258" />][4]<figcaption class="wp-caption-text">element size</figcaption></figure>

Все размеры указаны в пикселах.

 [1]: http://localhost:7788/third/?p=91 "Линейка в Photoshop"
 [2]: http://localhost:7788/third/wp-content/uploads/2013/04/marquee_tool.png
 [3]: http://localhost:7788/third/wp-content/uploads/2013/04/selected_element.png
 [4]: http://localhost:7788/third/wp-content/uploads/2013/04/element_size.png