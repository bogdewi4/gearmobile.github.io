---
title: "Функция .find библиотеки jQuery"
layout: post
categories: jquery
tags: [jquery, find]
share: true
---

Осуществляет поиск элементов внутри **уже выбранных элементов**.

Метод имеет варианты использования и соответствующий синтаксис:

`.find(selector)` - ищет элементы, соответствующие заданному селектору, внутри **выбранных элементов**.

`.find(element)` - осуществляет поиск элемента `element` внутри **выбранных элементов**. Параметр `element` задается в виде DOM-элемента.

`.find(jQuery object)` - осуществляет поиск элементов внутри **выбранных элементов**, оставляя те, которые содержатся в заданном объекте jQuery.


**Примеры использования**.

- вернет все элементы `span`, находящиеся внутри div-элементов:

{%  highlight javascript %}
$('div').find('span')
{%  endhighlight %}

- вернет все элементы с классом `.bigBlock`, находящиеся внутри div-элементов:

{%  highlight javascript %}
$('div').find('.bigBlock')
{%  endhighlight %}

**Вышеуказанные примеры хороши лишь в качестве демонстрации возможностей метода `.find()`.**

Например, искать span-элементы, лежащие внутри div'ов правильнее будет так:

{%  highlight javascript %}
$('div span')
{%  endhighlight %}

Метод `.find()` же удобно использовать, когда некоторые **элементы уже найдены** и необходимо осуществить поиск других элементов внутри уже найденных элементов:

{%  highlight javascript %}
// найдем все ul-элементы на странице
var $ulElements = $('ul');
// найдем li-элементы с классом .userBox внутри $ulElements
$ulElements.find('li.userBox');

// сокращенный вариант записи
var $ulElements = $('ul').find('li.userBox');
{%  endhighlight %}

Так же `.find()` удобен для использования в **цепочках методов**:

{%  highlight javascript %}
$('ul') // найдем все ul-элементы на странице
  .addClass('listElements') // добавим ul'ам класс .listElements
  .find('li.userBox') // найдем li-элементы с классом .userBox внутри ul'ов
  .remove(); // и удалим их

// сокращенный вариант записи
$('ul').addClass('listElements').find('li.userBox').remove();
{%  endhighlight %}

Работа метода `.find()` **схожа** с методом `.children()`, который осуществляет поиск подходящих **дочерних элементов**.

Отличие заключается в том, что `.find()` проводит поиск не только среди дочерних элементов, но и внутри них тоже (другими словами - поиск проходит на **всех уровнях** иерархии DOM, в то время как `.children()` ищет только **на одном уровне**).

## Пример метода .find()

Внутри каждого ul-элемента найдем первый li-элемент и последний p-элемент:

{%  highlight javascript %}
// найдем и сохраним все ul-элементы
var $matched = $('ul');

// выделим их
$matched.addClass('matched');

// найдем внутри уже выбранных элементов все требуемые и выделим их, добавив класс .result
$matched.find('li:first, p:last').addClass('result');

// сокращенный вариант записи
var $matched = $('ul').addClass('matched').find('li:first, p:last').addClass('result');
{%  endhighlight %}

## Фильтрация элементов помощью .find()

Кроме поиска, .find() может осуществлять своеобразную фильтрацию.

{%  highlight javascript %}
var $span = $('span'); // создать переменную $span и поместить в нее результат выборки по элементам span
$('p').find($span).css('color','blue'); // найти все элементы p, среди этих найденных элементов найти все элементы span и расскрасить их
{%  endhighlight %}

***

Материал статьи полностью основан на [http://jquery.page2page.ru][1] и не претендует на оригинальность.

[1]: http://jquery.page2page.ru/ "jQuery page2page2Page"
