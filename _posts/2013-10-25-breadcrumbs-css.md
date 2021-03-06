---
title: "Навигация breadcrumbs с помощью треугольников на CSS"
layout: post
categories: css
tags: [breadcrumbs, css]
share: true
---

> Интересная статья по созданию навигации в виде "хлебных крошек" (breadcrumbs).

Такая навигация удобна и полезна для сайтов с большим количеством рубрик. Благодаря такой навигации пользователь сайта может не запутаться в содержимом, точно знать, где он находиться и легко перейти в то место, куда ему нужно.

Видов такой навигации может быть множество, все зависит от дизайна. Но принцип построения на CSS стандартный - с помощью списков `ul`.

Статья была опубликована на одном из моих любимых сайтов CSS-Tricks. Ниже привожу вольный перевод ее автора (Chris Coyier):

Вы уже знаете, как создавать треугольники на чистом CSS? Для этого просто генерируется блочный элемент с нулевой шириной и высотой, у которого имеется одна граница с цветом, а две смежные границы имеют прозрачный цвет. Такие треугольники применяются в самых разнообразных местах дизайна - например, для указателей в навигации.

Другое место их применения - невинные украшательства дизайна, не нарушающие его общую разметку. В счастью, это возможно благодаря псевдо-элементам, которые часто используются при их создании. Применяя `:before`, `:after` или оба сразу можно сгенерировать блочные элементы и с их помощью создать треугольники.

А вот последние можно применять для создания навигации в стиле "хлебные крошки". Как выглядит одна из таких навигаций (*чтобы иметь представление, что это такое*), показано на рисунке ниже:

![Один из видов навигации хлебные крошки]({{site.url}}/images/uploads/2013/10/trianglebreadcrumbs.png)

## HTML разметка

Начнем создание такого меню с HTML-разметки, которая максимально проста и представляет собой обычный неупорядоченный список с классом breadcrumb:

{% highlight html %}
<ul class="breadcrumb">
  <li>
    <a href="#">Home</a>
  </li>
  <li>
    <a href="#">Vehicles</a>
  </li>
  <li>
    <a href="#">Vans</a>
  </li>
  <li>
    <a href="#">Camper Vans</a>
  </li>
  <li>
    <a href="#">1989 VW Westfalia Vanagon</a>
  </li>
</ul>
{% endhighlight %}

## CSS код

В первую очередь убедимся, что наш список не выглядит, как обычный неупорядоченный список. Для этого уберем у него маркеры, сделаем его пункты плавающими влево и зададим самые общие стилевые правила для ссылок внутри этого списка. Обратите внимание на свойство `overflow` для всего списка в целом - он применяется здесь по двум причинам.

Первая - наш список должен иметь высоту. Контейнеры, которые содержат только плавающие элементы, схлопываются (`collapse`), что совсем не то, что нам нужно. Второе - когда мы будем создавать треугольники, мы сделаем их достаточно большими:

{% highlight css %}
.breadcrumb {
  list-style-type: none;
  overflow: hidden;
  font: 18px Helvetica, Arial, sans-serif;
}

.breadcrumb li {
  float: left;
}

.breadcrumb li a {
  float: left;
  position: relative;
  color: #fff;
  text-decoration: none;
  padding: 10px 0 10px 65px;
  background-color: brown;
  background-color: hsla(34, 85%, 35%, 1);
}
{% endhighlight %}

Для создания треугольника мы воспользуемся псевдо-элементом `:after`. Для него установим высоту и ширину, равную нулю; и абсолютно спозиционируем его на 100% влево, что означает - он будет располагаться у правого края своего блока родителя.

Затем сместим треугольник вниз на 50% и "вернем" назад на -50px для точного позиционирования по центру (это классический прием - перевод здесь). Есть только один момент, на который нужно обратить внимание.

Граница, которую мы создаем сверху, равна 50px, нижняя граница также равна 50px, а ширина левой границы равна 30px. Это сделано для того, чтобы треугольник получился более "плоским", с не такой острой вершиной. Если мы сделаем левую границу равной остальным сторонам в 50px, угол треугольника будет слишком острый.

Так как верхняя и нижняя границы равны по 50px, то общая высота треугольника получается в 100px. Это гораздо больше, чем высота нашего меню, в котором высота шрифта `18px` и `padding-top: 10px`, `padding-bottom: 10px`. Однако, это хорошо, что треугольник больше высоты меню. Это означает, что у нас остается достаточно свободного пространства, чтобы "поиграться" с размером шрифта:

{% highlight css %}
.breadcrumb li a:after {
  content: '';
  display: block;
  position: absolute;
  top: 50%;
  margin-top: -50px;
  left: 100%;
  z-index: 2;
  width: 0;
  height: 0;
  border-left: 30px solid hsla(34, 85%, 35%, 1);
  border-top: 50px solid transparent;
  border-bottom: 50px solid transparent;
}
{% endhighlight %}

Все хорошо. Но на примере, который нужно воссоздать в коде, есть тонкая полоска шириной в 1px, идущая по краю треугольника. Чтобы "нарисовать" ее в CSS-коде, нам потребуется еще "поколдовать", так как напрямую создать границу для треугольника не получиться. Ведь треугольник как раз сам и является границей!

Поэтому мы поступим по другому - создадим еще один треугольник, который поместим позади нашего первого и зададим для него белый фоновый цвет. По своим свойствам второй треугольник будет практически одинаков с первым, но создаваться будет с помощью псевдо-элемента `:before`.

Обратите внимание на важную вещь - `z-index`. С помощью этого свойства можно "тасовать" элементы `:before` и `:after` (точнее - созданные ими треугольники) в нужном порядке - какой треугольник над каким должен располагаться:

{% highlight css %}
.breadcrumb li a:before {
  content: '';
  display: block;
  position: absolute;
  top: 50%;
  margin: -50px 0 0 1px;
  left: 100%;
  z-index: 1;
  width: 0;
  height: 0;
  border-left: 30px solid #fff;
  border-top: 50px solid transparent;
  border-bottom: 50px solid transparent;
}
{% endhighlight %}

Примечание переводчика:

> Изменения минимальны. Цвет границы задан белым `#fff` и добавлено смещение треугольника влево на 1px `margin-left: 1px`, чтобы разделительная черта была более заметна.

Теперь что касается цветовой заливки навигации. Так как пример имеет плавное изменение цвета элементов навигации, нам потребуются еще два замечательных CSS-свойства: `nth-child` и HSLa.

  * Чем полезно `nth-child` - можно задать цвета для различных элементов навигации без добавления дополнительной разметки в HTML-код;
  * Чем полезно HSLa - основываясь только на одном цвете, можно легко задать различные оттенки для элементов навигации.

Помимо этого, для первой ссылки мы уменьшим отступ слева с помощью `padding-left`, чтобы все элементы меню имели одинаковый размер; для последней ссылки совсем уберем цвет, сделаем некликабельной и вернем вид курсора по умолчанию. Все это мы выполним без какой-либо дополнительной разметки, с помощью псевдо-элементов `:first-child` и `:last-child` (*плюс к двум предыдущим*):

{% highlight css %}
.breadcrumb li:first-child a {padding-left: 10px;}
.breadcrumb li:nth-child(2) a {background-color: hsla(34,85%,45%,1);}
.breadcrumb li:nth-child(2) a:after {border-left-color: hsla(34,85%,45%,1);}
.breadcrumb li:nth-child(3) a {background-color: hsla(34,85%,55%,1);}
.breadcrumb li:nth-child(3) a:after {border-left-color: hsla(34,85%,55%,1);}
.breadcrumb li:nth-child(4) a {background-color: hsla(34,85%,65%,1);}
.breadcrumb li:nth-child(4) a:after {border-left-color: hsla(34,85%,65%,1);}
.breadcrumb li:nth-child(5) a {background-color: hsla(34,85%,75%,1);}
.breadcrumb li:nth-child(5) a:after {border-left-color: hsla(34,85%,75%,1);}
.breadcrumb li:last-child {background-color: transparent !important; color: #000; pointer-events: none; cursor: default;}
{% endhighlight %}

Примечание переводчика:

> Нумерация в `nth-child` начинается с единицы, а не с нуля, как принято в языках программирования.

И наконец, состояния элементов навигации при наведении курсора мыши. Здесь единственная особенность - нам нужно задать цвет треугольника точно таким же, как и ссылка. Не проблема:

{% highlight css %}
.breadcrumb li a:hover {background-color: hsla(34,85%,25%,1);}
.breadcrumb li a:hover:after {border-left-color: hsla(34,85%,25%,1) !important;}
{% endhighlight %}

## Совместимость с браузерами

Назовите меня ленивым, но я не занимался вопросом проверки данного кода на кросс-браузерную совместимость. Я был слишком захвачен самой идеей создания меню "хлебные крошки" на чистом CSS, чтобы думать его практическом использовании. Но если вас волнует мысль о его поддержке более старыми версиями браузеров, то стоит обратить внимание на следующие вещи:

  * используйте для передачи цвета HEX-код вместо HSLa;
  * для каждого из пунктов меню `li` создайте свои классы, вместо использования `nth-child`;
  * для браузеров, не поддерживающих псевдо-классы `:after`/`:before` используйте схему создания навигационного меню, основанную на изображениях;
  * применяйте библиотеку Modernizr для определения поддержки браузерами тех или иных свойств (например, HSLa);
  * используйте дополнительные стилевые правила для IE.

Результат, созданный с помощью приведенного выше кода, показан ниже:

![Меню хлебные крошки с помощью CSS-треугольников]({{site.url}}/images/uploads/2013/10/breadcrumb-result.jpg)

Эффект при наведении курсора мыши на один из пунктов меню:

<figure id="attachment_96" style="width: 600px;" class="wp-caption aligncenter">
  [<img src="http://localhost:7788/third/wp-content/uploads/2013/10/breadcrumb-result-hover-600x129.jpg" alt="Эффект при наведении курсора мыши на меню навигации" width="600" height="129" class="size-medium wp-image-96" />][3]
  <figcaption class="wp-caption-text">Эффект при наведении курсора мыши на меню навигации</figcaption>
</figure>

![Эффект при наведении курсора мыши на меню навигации]({{site.url}}/images/uploads/2013/10/breadcrumb-result-hover.jpg)

На этом все и перевод закончен.

---
