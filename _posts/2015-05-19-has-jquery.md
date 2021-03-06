---
title: "Методы has и hasClass библиотеки jQuery"
layout: post
categories: jquery
tags: [jquery, has, hasClass]
share: true
---

Два очень похожих метода библиотеки jQuery, служащих для фильтрации выборки - метод `.has()` и метод `.hasClass()`.

И действительно, оба этих метода похожи между собой. Чтобы было понятно, лучше сразу перейду к примерам.

## Метод .has()

Метод `.has()` фильтрует элементы, имеющие в своем составе указанные в `.has()` **селекторы**.

Простой пример:

{% highlight javascript %}
$('li').has('a').addClass('active');
{% endhighlight %}

**То есть**: всем элементам `li`, имеющим в качестве потомков (*в своем составе*) элемент `a`, присвоить класс `.active`.

На лицо, как бы это сказать, обратная фильтрация - *справа налево*. Обычно все методы библиотеки jQuery работают *слева направо*.

Этот метод чем-то похож на метод `.parent()`. В качестве примера рассмотрим такой вариант:

{% highlight javascript %}
$('a').parent('li').addClass('active');
{% endhighlight %}

... что читается таким образом: всем элементам `li`, являющимся родителями элементов `a`, присвоить класс `.active`.

Напомню, что метод `.has()` работает именно с селекторами и имеет такой синтаксис:

{% highlight javascript %}
.has('selector')
{% endhighlight %}

## Метод .hasClass()

Метод `.hasClass()` очень похож по принципу действия на предыдущий метод `has()` - но это только кажущееся впечатление.

Во-первых, как понятно из имени метода `.hasClass()`, что он работает с **классами**, а не **селекторами**.

То есть, синтаксис метода `.hasClass()` таков:

{% highlight javascript %}
.hasClass('class')
{% endhighlight %}

Во-вторых, метод `.hasClass()` возвращает логическое `true` или `false`, в отличие от метода `.has()`, который возвращает **массив объектов**, доступных для дальнейшей обработки.

Простой пример:

{% highlight javascript %}
if ($('li').hasClass('active')) {
  $('li').find('a').addClass('activeLink');
} else {
  $('li').find('a').addClass('inactiveLink');
}
{% endhighlight %}

... что читается таким образом: если элементы `li` имеют класс `.active`, то всем элементам `a`, являющимся потомками элементов `li`, присвоить класс `.activeLink`; иначе всем элементам `a` присвоить класс `.inactiveLink`.

Стоит обратить внимание, что в случае метода `.hasClass()` имеет место быть обычный способ фильтрации элементов - слева направо; выборка сужается по мере появления новых условий.

Вот такая картина получается, с двумя этими методами - `.has()` и `.hasClass`.

На этом все.

***
