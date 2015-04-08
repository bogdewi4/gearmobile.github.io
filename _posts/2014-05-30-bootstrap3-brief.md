---
title: "Краткий обзор Bootstrap 3"
layout: post
categories: css
tags: [bootstrap, css]
share: true
---

> Еще один фреймворк из бесчисленного на сегодняшний день полка фреймворков - Bootstrap 3. Точнее было бы сказать, что не еще один - а флагман CSS-фреймворков! Версия 2 вышла давно и на сегодня является устаревшей. Сегодня самая современная версия - это версия 3. Поэтому ее мы и будем рассматривать. Вопрос данной статьи будет посвящен основе данной фреймворка - CSS-сетке и особенностям ее создания в версии 3.

## Установка и настройка Bootstrap 3

Ничего сложного и необычного в установке фреймворка Bootstrap 3 нет. Для этого скачиваем дистрибутив с официального сайта Bootstrap 3, распаковываем архив в готовый проект-директорию.

Затем с официального сайта берем готовый шаблон HTML-документа - [Basic template][1] и создаем свой собственный индексный файл HTML:

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- The above 3 meta tags *must* come first in the head; any other head content must come *after* these tags -->
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
      <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="js/bootstrap.min.js"></script>
  </body>
</html>
{% endhighlight %}

В этом файле проверяем правильность путей для CSS и JS-файлов:

{% highlight html %}
<link href="css/bootstrap.css" rel="stylesheet">
<link href="css/bootstrap-theme.css" rel="stylesheet">
...
{% endhighlight %}

Все готово для дальнейшей работы.

## Система сеток Bootstrap 3

Важнейшей составляюшей любого CSS-фреймворка является система CSS-сетки (grid). Как и в предыдущей версии Bootstrap 2, в версии 3 используется 12-ти колоночная система.

Однако, в Bootstrap 3 применяются четыре типа классов для создания адаптивной (responsive) сетки. На официальном сайте Bootstrap 3 имеется таблица с побробным и наглядным описанием этих классов - [Grid Options][2].

![Таблица классов для CSS-сетки Bootstrap 3]({{site.url}}/images/uploads/2014/05/bootstrap3_grid-options.png)

В этой таблице представлены четыре ширины экрана устройства, на котором будет отображена страница. Колонка "Extra small devices" с шириной менее 768px обозначает **мобильные устройства**. Колонка "Small devices" с шириной равной или больше 768px представляет **планшетные компьютеры** (планшеты). Две остальные колонки представляют **обычный настольный монитор** через колонку "Medium devices" с шириной равной или больше 992px и **широкоформатный монитор** через колонку "Large devices" с шириной равной или больше 1200px.

Вышеназванные величины 768px, 992px и 1200px являются контрольными точками (breakpoints), служащими для обработки медиа-запросов в адаптивном дизайне страницы.

В данной таблице строка "Class prefix" является чуть ли не самой важной, так как в ней содержатся имена (префиксы) классов фреймворка Bootstrap 3 для каждого из четырех типов устройств. Для мобильного устройства имя (префикс) класса будет `.col-xs-`, для планшетного компьютера префикс будет `.col-sm-`, для обычного монитора - `.col-md-` и для широкоформатного монитора - `.col-lg-`. Для видно из названия префиксов, они являются сокращениями от названия самих устройств, поэтому их легко запомнить.

Вот и все, что необходимо знать о системе CSS-сеток в фреймворке Bootstrap 3. Дальше можно легко домыслить ход построения адаптивной сетки для конкретного сайта.

## Пример создания CSS-сетки в Bootstrap 3

Допустим, необходимо создать следующий макет:

  * для широкоформатного монитора в макете должно быть 2 столбца - один шириной 10 колонок и второй шириной 2 колонки;
  * для обычного монитора 2 столбца - один шириной 8 колонок и второй шириной 4 колонки;
  * для планшета 2 столбца - один шириной 6 колонок и второй шириной также 6 колонок;
  * для мобильного устройства макет должен остаться, как и для планшета - два столбца одинаковой ширины.

То есть, при изменении ширины монитора устройства ширина столбцов в макете должна меняться, как показано выше. Для этого создадим простую разметку и добавим в нее классы Bootstrap 3:

{% highlight html %}
<div class="container">
  <div class="row">
    <div class="col-lg-10 col-md-8 col-sm-6"></div>
    <div class="col-lg-2 col-md-4 col-sm-6"></div>
  </div>
</div>
{% endhighlight %}

Если открыть созданную страницу в окне браузера и попробовать менять ширину его окна, то в диспечере свойств страницы увидим метаморфозы, связанные с работой медиа-запросов `media-queries`. При ширине окна больше 1200px будем наблюдать левый столбец шириной в 10 колонок и правый столбец шириной в 2 колонки.

Уменьшив ширину окна до 992px, получим левый столбец шириной в 8 колонок и правый стлбец шириной в 4 колонки. Еще уменьшив окно до 768px, получим два одинаковых столбца шириной в 6 колонок. Если окно окончательно уменьшится (менее 768px), ширина столбцов останется прежней, но они расположаться вертикально, друг под другом (*поведение по умолчанию*).

## Видимость элементов сетки в Bootstrap 3

Немного усложним задачу и сделаем ее интереснее ради теоретического примера работы фреймворка Bootstrap 3. Допустим, нам необходим такой макет:

  * широкоформатный монитор - 12 колонок;
  * обычный монитор - 3 колонки;
  * планшетный монитор - 3 колонки;
  * мобильный монитор - 2 колонки.

Тогда HTML-разметка и классы фреймворка Bootstrap 3 следующими:

{% highlight html %}
<div class="container">
  <div class="row">
    <div class="col-lg-2 col-md-4  col-sm-4  col-xs-6"></div>
    <div class="col-lg-2 hidden-md hidden-sm hidden-xs"></div>
    <div class="col-lg-2 col-md-4  col-sm-4  col-xs-6"></div>
    <div class="col-lg-2 hidden-md hidden-sm hidden-xs"></div>
    <div class="col-lg-2 col-md-4  col-sm-4  hidden-xs"></div>
    <div class="col-lg-2 hidden-md hidden-sm hidden-xs"></div>
  </div>
</div>
{% endhighlight %}

В данном случае при измении ширины окна браузера будет меняться количество колонок внутри макета. При ширине большей 1200px число колонок будет равняться шести. При уменьшении окна до ширины в 992px число колонок изменится до 4-х и будет оставаться таковым при ширине окна 768px. Если окно еще уменьшится ниже 768px, то количество колонок измениться до двух.

Подобные метаморфозы возможны благодаря классу `hidden-x`, который вы могли заметить в разметке. Задача этого класса скрыть указанный элемент при достижении окном браузера определенной контрольной точки. Для каждого из предполагаемых состояний окна браузера необходимо указать класс - `hidden-lg`, `hidden-md`, `hidden-sm`, `hidden-xs`:

![Сравнительная таблица классов hidden и visible в Bootstrap 3]({{site.url}}/images/uploads/2014/05/bootstrap3_available-classes.png)

Противоположностью класса `hidden-x` является класс `visible-x`. Несмотря на то, что действие этих классов должно быть прямо противоположным друг другу, на практике это различие уловить не так просто и тут может помочь сравнительная таблица с официального файта Bootstrap 3 - [Responsive utilities][3]. В этой таблице (см. таблицу выше) хорошо видно различие между этими классами.

В то время как класс `hidden-x` производит скрытие элемента в определенной контрольной точке (breakpoint), во всех остальных состояниях элемент видимый. Класс `visible-x` делает элемент видимым только в определенном состоянии - во всех остальных состояниях элемент **невидимый**.

## Вложенность (nesting) сетки в Bootstrap 3

CSS-сетка в фреймворке Bootstrap 3 позволяет выполнять вложение одних ячеек в другие. Такое явление называется nesting. К примеру, необходим создать такую HTML-разметку:

{% highlight html %}
<div class="container">
  <div class="row primo">
    <div class="col-lg-4"></div>
    <div class="col-lg-4"></div>
    <div class="col-lg-4"></div>
  </div>
  <div class="row secondo">
    <div class="col-lg-8">
      <div class="row">
        <div class="col-lg-6"></div>
        <div class="col-lg-6"></div>
      </div>
    </div>
    <div class="col-lg-4"></div>
  </div>
  <div class="row tetro">
    <div class="col-lg-6">
      <div class="row">
        <div class="col-lg-6"></div>
        <div class="col-lg-6"></div>
      </div>
    </div>
    <div class="col-lg-6">
      <div class="row">
        <div class="col-lg-6"></div>
        <div class="col-lg-6"></div>
      </div>
    </div>
  </div>
  <div class="row quattro">
    <div class="col-lg-2"></div>
    <div class="col-lg-2"></div>
    <div class="col-lg-2"></div>
    <div class="col-lg-2"></div>
    <div class="col-lg-2"></div>
    <div class="col-lg-2"></div>
  </div>
</div>
{% endhighlight %}

Для наглядности примера оставим для элементов только один класс `.col-lg-`. Блок с классом `primo` имеет три обычные колонки `col-lg-4`. Блок с классом `secondo` имеет две колонки - `col-lg-8` и `col-lg-4`. Внутри колонки `col-lg-8` размещено еще два блока равной ширины - две колонки с классом `col-lg-6`. Это пример вложенности (nesting) одних ячеек CSS-сетки Bootstrap 3 в другие ячейки.

Аналогичная ситуация с блоком класса `tetro`, но в нем в оба "первичных" блока вложены еще два блока. Всего получается четыре блока. С блоком класса `quattro` все просто - там "обычные" (не вложенные) шесть блоков класса `col-lg-2`.

При этом нужно обратить внимание (если еще не догадались), что при вложении одних блоков в другие ширина блока-родителя принимается по умолчанию равной 12-колонкам.

## Смещение (offsetting) колонок в Bootstrap 3

В Bootstrap 3 можно смещать колонки вправо с помощью класса `.col-*-offset-*`, который добавляет `margin-left` для указанной колонки. Смещение производится на ширину колонки, кратную указанному количеству.

Приведу пример, чтобы было наглядно понятно:

{% highlight html %}
<div class="container">
  <div class="row">
    <div class="col-lg-8"></div>
    <div class="col-lg-2 col-lg-offset-2 right"></div>
  </div>
</div>
{% endhighlight %}

В этом примере колонка с классом `right` имеет ширину в два столбца и смещается вправо опять таки на два столбца - `col-lg-offset-2`. При этом стоит также заметить, что данное смещение будет выполняться только при ширине экрана больше 1200px (breakpoint), на что указывает имя класса - `col-lg-`. Если необходимо, чтобы такое смещение сохранялось при меньших размерах окна браузера, необходимо явно указать это в коде:

{% highlight html %}
<div class="container">
  <div class="row">
    <div class="col-lg-8"></div>
    <div class="col-lg-2 col-lg-offset-2 col-md-offset-2 col-sm-offset-2 col-xs-offset-2 right"></div>
  </div>
</div>
{% endhighlight %}

## Адаптивная (responsive) сетка в Bootstrap 3

Переключать ширину сетки с фиксированной на резиновую в Bootstrap 3 можно точно также, как и во 2-й версии. Для этого нужно заменить для блока-контейнера имя класса с `container` на `container-fluid`:

{% highlight html %}
<div class="container-fluid">
  <div class="row">
    ...
  </div>
</div>
{% endhighlight %}

## Заключение

На этом обзор CSS-сетки в фреймворке Bootstrap 3 можно считать законченным. Субъективно для меня был интересен именно этот вопрос. Что касается рассмотрения остальных классов, предназначенных для оформления различных элементов на странице, то мне они кажутся не такими интересныи и важными.

Может быть, в дальнейшем я и вернусь к расмотрению деталей фреймворка Bootstrap 3.

---

[1]: http://getbootstrap.com/getting-started/#template "Basic template"
[2]: http://getbootstrap.com/css/#grid "Grid Options"
[3]: http://getbootstrap.com/css/#responsive-utilities "Responsive utilities"