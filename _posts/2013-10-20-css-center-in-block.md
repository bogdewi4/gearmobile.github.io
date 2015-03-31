---
title: "CSS - разместить объект точно по центру блока"
layout: post
categories: css
tags: [css]
share: true
---

> Перевод небольшой статьи с замечательного сайта для веб-дизайнеров CSS-Tricks.

Статья посвящена одному интересному моменту - как правильно точно отцентрировать один объект с фиксированными размерами внутри другого. В принципе ничего сложного (и большого секрета) в этом нет, но статья мне понравилась, поэтому решил перевести и разместить у себя. Особенно хороши картинки - глядя на них, можно и текст не писать - все наглядно понятно. Далее - вольный перевод статьи Криса Койера:

На днях мне потребовалось создать страницу-заглушку для сайта. Мне необходимо было разместить изображение логотипа точно по центру экрана, а именно - отцентрированную по вертикали и горизонтали. Немного подумав, я задал для изображения класс centered и прописал для него правила:

{% highlight css %}
.centered {
    position: fixed;
    top: 50%;
    left: 50%;
  }
{% endhighlight %}

Примечание переводчика:

> Свойство `fixed` здесь задается по двум причинам. Первая - необходимо, чтобы изображение имело фиксированное положение на странице и не изменяло его при прокрутке в окне браузера. Второе - изображение должно располагаться точно по центру окна. Одновременно соответствовать обоим критериям может только одно свойство - `fixed`. Оно очень похоже на более известное `absolute`, но с одним отличием - объект с этим свойством не меняет своего положения при прокрутке страницы.

Но я уверен, что вы скажете - это еще не все, что необходимо сделать. Тот код, который я прописал, помещает верхний левый угол изображения посередине страницы, но не центр изображения по центру страницы:

![Изображение, размещенное не по центру блока]({{site.url}}/images/uploads/2013/11/css-not-centered-block.gif)

Для того чтобы расположить картинку точно по центру, необходимо сместить ее влево на величину, равную половине ширины изображения и сместить вверх на величину, равную половине высоты изображения.

Оба смещения нужно сделать с помощью свойства `margin-left` и `margin-top` с отрицательными значениями. Код в итоге будет следующим:

{% highlight css %}
.centered {
position: fixed;
top: 50%;
left: 50%;
margin: -50px 0 0 -100px;
}
{% endhighlight %}

В результате изображение разместиться точно по центру экрана:

![Изображение, размещенное точно по центру блока]({{site.url}}/images/uploads/2013/11/css-centered-block.gif)

На этом все.

---