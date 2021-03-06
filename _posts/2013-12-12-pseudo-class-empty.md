---
title: "Краткая заметка по псевдо-классу :empty"
layout: post
ctegories: css
tags: [empty, css]
share: true
---

> Я люблю ту простоту, которую привносят CSS3-селекторы в таблицы стилей. В этой статье приведено краткое описание одного из моих любимых селекторов: псевдо-класса `:empty`.

## Что такое псевдо-класс :empty

Вот краткое описание, взятое из спецификации W3C:

> Псевдо-класс `:empty` относится к элементу, у которого нет потомков.

Звучит просто и понятно, не правда ли? Потому что это действительно так - псевдо-класс `:empty` применяется к элементам, которые полностью пустые; например, для пустого параграфа:

{% highlight html %}
<p>...</p>
{% endhighlight %}

Или же пустые ячейки таблицы:

{% highlight html %}
<table>
  <tr>
    <td></td>
  </tr>
</table>
{% endhighlight %}

А вот к такому параграфу псевдо-класс `:empty` не применим, так как он не является пустым (внутри этого тега есть пробел, который является равноправным символом по сравнению со всеми остальными):

{% highlight html %}
<p>...</p>
{% endhighlight %}

## Практическое применение :empty

Хорошо, но каким образом может быть полезен этот селектор?

Представим ситуацию, когда вы стилизуете таблицу и некоторые из ячеек этой таблицы не имеют данных внутри себя. Тогда вы можете применить к ним другие правила благодаря псевдо-классу `:empty`.

Давайте возьмем таблицу, которая создавалась мною ранее. Я собираюсь использовать те же самые таблицы стилей, но сделаю их более упрощенными. Также я собираюсь удалить содержимое из некоторых ячеек для того, чтобы сделать пример соответствующим статье.

Разметка будет выглядеть таким образом:

{% highlight html %}
<table>
  <caption>A simple table</caption>
  <tr>
    <th scope="col" rowspan="2">Some headings</th>
    <th scope="col" colspan="4">More headings</th>
  </tr>
  <tr>
    <th scope="col">Great</th>
    <th scope="col">Brilliant</th>
    <th scope="col">Genius</th>
    <th scope="col">Good</th>
  </tr>
  <tr>
    <th scope="row">Interesting totals</th>
    <td>155</td>
    <td>165</td>
    <td>70</td>
    <td>140</td>
  </tr>
  <tr>
    <th scope="row">Curious</th>
    <td>5</td>
    <td>35</td>
    <td>50</td>
    <td>15</td>
  </tr>
  <tr>
    <th scope="row">Awesome</th>
    <td>75</td>
    <td>90</td>
    <td></td>
    <td>5</td>
  </tr>
  <tr>
    <th scope="row">Fabulous</th>
    <td>30</td>
    <td></td>
    <td>20</td>
    <td>80</td>
  </tr>
  <tr>
    <th scope="row">Nice</th>
    <td>45</td>
    <td>40</td>
    <td></td>
    <td>40</td>
  </tr>
</table>
{% endhighlight %}

И вот, что я собираюсь добавить в таблицы стилей, для того чтобы отформатировать пустые ячейки таблицы:

{% highlight html %}
tbody td:empty {
  background: #efefef;
}
{% endhighlight %}

А вот теперь пустые ячейки таблицы отформатированы [по-другому][1]! Мне кажется, что невозможно сделать это более простым способом.

Если вас этот селектор заинтересовал, то скажу, что он поддерживается всеми последними версиями браузеров Firefox, Safari, Chrome и Opera. И возможно, он работает в браузере Internet Explorer 9, наравне с остальными селекторами стандарта CSS3.

[1]: http://webdesignernotebook.com/examples/empty-selector.html "Empty Selector"

---
