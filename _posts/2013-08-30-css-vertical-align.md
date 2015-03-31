---
title: "CSS - центрирование текста по вертикали в логотипе"
layout: post
categories: css
tags: [css]
share: true
---

> При верстке макета столкнулся с такой задачей. Имеется логотип, внутри которого необходимо разместить текст.

Логотип создается с помощью элемента - заголовка первого уровня `h1`. Внутри этого блочного элемента размещается ссылка. Решений подобной задачи в Интернете вроде бы много, но вот конкретно не нашел под себя. Решил с помощью форума `forum.htmlbook.ru`.

Необходимо сделать также, как и на psd-макете. Чтобы текст располагался по-вертикали по-центру, и был смещен при этом вправо. Часть html-кода, в котором создается логотип со ссылкой, показана ниже:

![Логотип на psd-макете]({{site.url}}/images/uploads/2013/11/psd-maket.png)

![Логотип сайта]({{site.url}}/images/uploads/2013/11/html-schema.png)

С установкой фонового изображения проблем не возникает. Задаю ширину и высоту для блока h1 равной ширине и высоте логотипа. И прописываю для него картинку в качестве фона.

Текст-ссылку внутри блока также стилизую в соотвествии с тем, как она изображена на макете. А вот центрование текста - здесь есть некоторая тонкость. Спасибо SelenIT, что кратко и точно объяснил, как поступать в данном случае.

Итак. С помощью свойства `display: table` превращаю блочный элемент `h1` в табличный. Это делается для того, чтобы можно было разместить текст строго по центру вертикали, так как только таблица имеет свойство `vertical-align`.

Строчный элемент `а`, то есть ссылка, теперь расположена внутри таблицы. Поэтому превращаю ее в ячейку таблицы с помощью правила `display: table-cell`. Теперь можно применить к содержимому этой ячейки свойство `vertical-align: middle`, тем самым размещая ее по-центру по-вертикали.

Осталось сместить текст вправо на заданную величину. Это выполняется с помощью правила `padding-left: 80px`.

Ниже привожу кусок кода, отвечающего за стилизацию логотипа сайта:

{% highlight css %}
.logo{
  background: url(../img/logo.gif) 0 0 no-repeat;
  height: 100px;
  width: 180px;
  display: table; /*!*/

}
.logo a{
  font-family: 'webfontbold';
  font-weight: bold;
  font-size: 20px;
  color: #090909;
  text-transform: uppercase;
  text-decoration: none;
  display: table-cell; /*!*/
  vertical-align: middle; /*!*/
  padding-left: 80px;
}
{% endhighlight %}

Вот задача и решена. Разобрался с центрирование текста по-вертикали с помощью правил `display: table`, `display: table-cell`, `vertical-align: middle`.

На этом все.

---