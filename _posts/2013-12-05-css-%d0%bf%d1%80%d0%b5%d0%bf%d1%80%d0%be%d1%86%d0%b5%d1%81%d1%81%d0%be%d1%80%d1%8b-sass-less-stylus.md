---
title: CSS-препроцессоры и преимущество их использования
author: gearmobile
layout: post
permalink: /css-%d0%bf%d1%80%d0%b5%d0%bf%d1%80%d0%be%d1%86%d0%b5%d1%81%d1%81%d0%be%d1%80%d1%8b-sass-less-stylus/
cleanretina_sidebarlayout:
  - default
ratings_users:
  - 24
ratings_score:
  - 118
ratings_average:
  - 4.92
categories:
  - Статьи по CSS
tags:
  - less
  - sass
  - stylus
---
*Статья на NetTuts+, написанная Johnathan Croom в 2012 году. Основная цель статьи &#8211; показать преимущество использования любого из трех описанных в ней препроцессоров Sass, LESS и Stylus. Обзор прекрасно подойдет для новичков, которые только открывают для себя эту грань веб-дизайна.*

В этой статье мы рассмотрим преимущества и выгоды использования трех различных препроцессоров &#8211; Sass (http://sass-lang.com/), LESS (http://lesscss.org/) и Stylus (http://learnboost.github.com/stylus/).

### Введение

Препроцессоры CSS были созданы с одной единственной целью &#8211; добавить стилевым таблицам CSS мощь и одновременную гибкость без нарушения кросс-браузерности. Все препроцессоры компилируют созданный с помощью их синтаксиса код в стандартный CSS-код, который понимает и использует любой браузер, каким бы древним он (*браузер*) не был. Существуют множество преимуществ, которые привносят препроцессоры в таблицы стилей CSS и в этой статье мы рассмотрим только некоторые из них, как хорошо известные, так и мало распространенные. Давайте приступим к обзору.

### Синтаксис

Наиболее важной частью при написании кода в любом препроцессоре CSS является его синтаксис. В счастью для нас, синтаксис всех трех препроцессоров, которые мы будем рассматривать, имеют CSS-подобный вид.

#### Sass & LESS

Оба препроцессора Sass и LESS имеют стандартный CSS-синтаксис. Это делает задачу конвертирования уже существующего CSS-кода в синтаксис любого из этих препроцессоров простой и быстрой. Sass использует для своих файлов расширение `.scss`, LESS &#8211; расширение `.less`.

Вид обычного файла в синтаксисе Sass или LESS представлен ниже:

<pre>/* style.scss или style.less */
h1{
    color: #0982c1;
}
</pre>

Хорошо видно, что это обычный синтаксис CSS, который прекрасно конвертируется в Sass (SCSS) или LESS.

Важно обратить внимание, что Sass (SCSS) также имеет старую версию синтаксиса Sass, в которой *опущены точки с запятой и фигурные скобки*. Несмотря на то, что такой синтаксис все еще можно применять на практике, он является **устаревшим** и мы не будем использовать его в наших примерах.

Синтаксис Sass (*старая версия*) выглядит следующим образом:

<pre>/* style.sass */
h1
    color: 0982c1
</pre>

#### Stylus

Для своих файлов этот препроцессор использует расширение `.styl`. Синтаксис препроцессора Stylus более многословный (*прим. переводчика: автор что-то напутал здесь*) в нем применяется за основу стандартный синтаксис CSS, но допускается применение различного сочетания скобок, двоеточий и точек с запятой.

Примеры различных видов синтаксиса Stylus:

<pre>/* CSS-подобный синтаксис */
h1 {
  color: #0982C1;
}
 
/* опущены фигурные скобки */
h1
  color: #0982C1;
 
/* опущены фигурные скобки, двоеточия и точки с запятой */
h1
  color #0982C1
</pre>

Все варианты синтаксиса, показанные выше, являются валидными и в результате компиляции получается правильный CSS-код. Например, такой код скомпилируется в стандартный CSS без ошибок:

<pre>h1 {
  color #0982c1
}
h2
  font-size: 1.2em
</pre>

### Переменные

В препроцессорах переменные объявляются и используются внутри файлов стилей CSS. Переменные могут принимать любое значение, допустимое в CSS (цвет, число или текст) и может ссылаться из любого места CSS-документа.

#### Sass

В препроцессоре Sass переменная объявляется с помощью символа `$`, при этом имя переменной и ее значение отделяются друг от друга двоеточием так, как это делается в CSS:

<pre>$mainColor: #0982c1;
$siteWidth: 1024px;
$borderStyle: dotted;
 
body {
  color: $mainColor;
  border: 1px $borderStyle $mainColor;
  max-width: $siteWidth;
}
</pre>

#### LESS

Переменные в LESS точно такие же, как и в Sass, за исключением того, что перед именем переменной ставится символ `@`:

<pre>@mainColor: #0982c1;
@siteWidth: 1024px;
@borderStyle: dotted;
 
body {
  color: @mainColor;
  border: 1px @borderStyle @mainColor;
  max-width: @siteWidth;
}
</pre>

#### Stylus

Переменные в Stylus не нуждаются ни в каком знаке для своего объявления, но, тем не менее, могут использовать символ `$`. Как правило, завершающий символ строки точка с запятой также не нужен, за исключением случая, когда имя переменной и ее значение совпадают. Еще один достойный упоминания момент заключается в том, что Stylus (0.22.4) компилирует код, даже если в нем имя переменной объявлено с помощью символа `@`, но при вызове этой переменной в коде подстановки значения переменной не происходит. Другими словами, не выполняется такая операция:

<pre>mainColor = #0982c1
siteWidth = 1024px
$borderStyle = dotted
 
body
  color mainColor
  border 1px $borderStyle mainColor
  max-width siteWidth
</pre>

#### Скомпилированный CSS

Каждый из представленных в виде примера файлов компилируется в точно такой же CSS-код. Вы можете включить воображение, чтобы представить, насколько полезными могут быть переменные. Благодаря им отпадает необходимость задавать значение цвета и потом двадцать раз повторять его в CSS-коде. Или же поставлена задача изменить ширину сайта и для этого необходимо "перерыть" код в поисках этой величины.

> *Прим. переводчика: здесь автор немного утрирует ситуацию, так как в любом нормальном редакторе кода имеется функция поиска.*

Ниже представлен CSS-код после выполнения компиляции:

<pre>body {
    color: #0982c1;
    border: 1px dotted #0982c1;
    max-width: 1024px;
}
</pre>

### Вложенность (nesting)

Если в коде CSS поставлена задача обратиться одновременно к нескольким элементам, имеющим одного и того же родителя, то писать снова и снова этого родителя &#8211; занятие утомительное.

Например, так:

<pre>section { 
    margin: 10px;
}
section nav { 
    height: 25px;
}
section nav a { 
    color: #0982C1;
}
section nav a:hover {
    text-decoration: underline;
}
</pre>

Вместо этого, используя возможности препроцессора, мы можем поместить все дочерние селекторы внутри скобок элемента-родителя. Кроме того, символ `&#038;` является ссылкой (*сокращением*) на селектор элемента-родителя.

#### Sass, LESS & Stylus

Все три препроцессора имеют абсолютно одинаковый синтаксис для вложенных селекторов:

<pre>section {
  margin: 10px;
 
  nav {
    height: 25px;
 
    a {
      color: #0982C1;
   
      &#038;:hover {
        text-decoration: underline;
      }
    }
  }
}
</pre>

#### Скомпилированный CSS

Ниже показан скомпилированный в CSS результат кода, представленного выше. Сравните с тем кодом, который мы писали в самом начале &#8211; абсолютно одинаково. Но какое удобство при использовании преимуществ препроцессора!

<pre>section {
  margin: 10px;
}
section nav {
  height: 25px;
}
section nav a {
  color: #0982C1;
}
section nav a:hover {
  text-decoration: underline;
}
</pre>

### Подмешивания (mixins)

Миксины (mixins) являются функциями, которые позволяют многократно использовать сгруппированные свойства внутри CSS-кода. Вместо того, чтобы просматривать весь код в поисках нужных строчек для их изменения, теперь можно вносить изменения только один раз, внутри миксина. Применение подмешиваний особенно оправдывает себя при создании специфичных стилей для элементов или простановке браузерных префиксов. Когда миксин вызывается внутри CSS-селектора, происходит распознавание аргументов этого миксина, затем его стили применяются к селектору, который его вызвал.

> *Прим. переводчика: в приведенных ниже примерах стоит обратить внимание на разницу в синтаксисе объявления и вызова миксина внутри CSS-селектора для всех трех препроцессоров.*

#### Sass

<pre>/* Sass mixin по имени error с аргументом $borderWidth, значение которого по умолчанию равно 2px */
@mixin error($borderWidth: 2px) {
  border: $borderWidth solid #F00;
  color: #F00;
}
 
.generic-error {
  padding: 20px;
  margin: 4px;
  @include error(); /* Подключается миксин по имени error */
}
.login-error {
  left: 12px;
  position: absolute;
  top: 20px;
  @include error(5px); /* Подключается миксин по имени error со значением аргумента $borderWidth, равным 5px; то есть происходит переопределение значения аргумента */
}
</pre>

#### LESS

<pre>/* LESS mixin по имени error с аргументом $borderWidth, значение которого по умолчанию равно 2px */
.error(@borderWidth: 2px) {
  border: @borderWidth solid #F00;
  color: #F00;
}
 
.generic-error {
  padding: 20px;
  margin: 4px;
  .error(); /* Подключается миксин по имени error */
}
.login-error {
  left: 12px;
  position: absolute;
  top: 20px;
  .error(5px); /* Подключается миксин по имени error со значением аргумента $borderWidth, равным 5px; то есть происходит переопределение значения аргумента */
}
</pre>

#### Style

<pre>/* Stylus mixin по имени error с аргументом $borderWidth, значение которого по умолчанию равно 2px */
error(borderWidth= 2px) {
  border: borderWidth solid #F00;
  color: #F00;
}
 
.generic-error {
  padding: 20px;
  margin: 4px;
  error(); /* Подключается миксин по имени error */
}
.login-error {
  left: 12px;
  position: absolute;
  top: 20px;
  error(5px); /* Подключается миксин по имени error со значением аргумента $borderWidth, равным 5px; то есть происходит переопределение значения аргумента */
}
</pre>

#### Скомпилированный CSS

Результатом компиляции из всех трех препроцессоров будет одинаковый CSS-код:

<pre>.generic-error {
  padding: 20px;
  margin: 4px;
  border: 2px solid #f00;
  color: #f00;
}
.login-error {
  left: 12px;
  position: absolute;
  top: 20px;
  border: 5px solid #f00;
  color: #f00;
}
</pre>

### Наследование (inheritance)

При написании CSS стилей "классическим" способом, для того чтобы применить одни и те же свойства к нескольким элементам в HTML-документе, нам следовало бы создать такой код:

<pre>p,
ul,
ol {
  /* какие-то стили здесь */
}
</pre>

Все работает прекрасно. Но если потребуется написать стили отдельно для любого из этих селекторов, нужно будет создавать отдельные правила для каждого из них. И сразу же код таблиц стилей становиться неряшливым и трудно поддерживаемым. В противоположность этому применяются наследование. Наследование &#8211; это возможность для одних CSS-селекторов наследовать свойства у другого селектора.

> *Прим. переводчика: обратите внимание на одинаковый синтаксис подключения (объявления) наследования внутри CSS-селектора с помощью директивы @extend.*

#### Sass & Stylus

<pre>.block {
  margin: 10px 5px;
  padding: 2px;
}
 
p {
  @extend .block; /* Наследовать свойства у селектора класса .block */
  border: 1px solid #EEE;
}
ul, ol {
  @extend .block; /* Наследовать свойства у селектора класса .block */
  color: #333;
  text-transform: uppercase;
}
</pre>

#### Скомпилированный CSS

<pre>.block, p, ul, ol {
  margin: 10px 5px;
  padding: 2px;
}
p {
  border: 1px solid #EEE;
}
ul, ol {
  color: #333;
  text-transform: uppercase;
}
</pre>

#### LESS

Препроцессор LESS не поддерживает наследование в полной мере так, как это организовано в Sass или Stylus. Вместо добавления множественных селекторов в один набор свойств, наследование трактуется как миксин без аргументов. Импорт стилей выполняется для каждого селектора. Обратной стороной такого подхода является постоянное повторение строк со свойствами в компилированном CSS-стиле.

Вот как может выглядеть LESS-код с наследованием:

<pre>.block {
  margin: 10px 5px;
  padding: 2px;
}
 
p {
  .block; /* Наследование свойств у селектора класса .block */
  border: 1px solid #EEE;
}
ul, ol {
  .block; /* Наследование свойств у селектора класса .block */
  color: #333;
  text-transform: uppercase;
}
</pre>

#### Скомпилированный CSS

<pre>.block {
  margin: 10px 5px;
  padding: 2px;
}
p {
  margin: 10px 5px;
  padding: 2px;
  border: 1px solid #EEE;
}
ul,
ol {
  margin: 10px 5px;
  padding: 2px;
  color: #333;
  text-transform: uppercase;
}
</pre>

Как хорошо видно из кода, стили класса `.block` добавлены для селекторов, которым требуется задать наследование у этого класса.

> *Прим. переводчика: код действительно получается избыточным, просто для каждого селектора тупо добавляются строки класса `.block`.*

### Импортирование

В CSS-сообществе к импортированию стилей с помощью директивы `@import` существует стойкое негативное отношение, так как такой подход порождает множественные HTTP-запросы к серверу, что замедляет работу браузера и нагружает сам сервер. Однако, в препроцессорах технология импортирования работает иначе. В любом из трех препроцессоров импортирование одного файла внутрь другого фактически приводит к вставке кода одного файла в другой при компиляции, в результате которой получается один CSS-файл.

> *Прим. переводчика: другими словами, в препроцессорах импортирование необходимо для компиляции одного файла из нескольких. В стандартном CSS импортирование приводит к подстановке одного кода внутрь другого.*

Обратите внимание, что при компилировании файла со стандартным подключением с помощью директивы `@import "file.css"` внутри него компиляции последнего не происходит. А вот миксины или переменные импортируются и используются в стилевом файле, как положено. Технология импортирования очень удобная, так как она позволяет создавать множество отдельных файлов для правильной организации проекта.

<pre>/* file.{type} */
body {
  background: #EEE;
}
@import "reset.css";
@import "file.{type}";
 
p {
  background: #0982C1;
}
</pre>

#### Скомпилированный CSS

<pre>@import "reset.css";
body {
  background: #EEE;
}
p {
  background: #0982C1;
}
</pre>

### Функции работы с цветом

"Цветовые" функции созданы для трансформации цвета при компиляции. Такие функции чрезвычайно полезны при создании градиентов, затемнения цвета при `hover` и многое другое.

#### Sass

<pre>lighten($color, 10%); /* возвращает цвет на 10% светлее чем $color */
darken($color, 10%);  /* возвращает цвет на 10% темнее чем $color */
 
saturate($color, 10%);   /* возвращает цвет на 10% более насыщенный чем $color */
desaturate($color, 10%); /* возвращает цвет на 10% менее насыщенный чем $color */
 
grayscale($color);  /* возвращает шкалу полутонов цвета $color */
complement($color); /* returns complement color of $color */
invert($color);     /* возвращает инвертированный цвет от $color */
 
mix($color1, $color2, 50%); /* возвращает результат смешивания цвета $color1 с цветом $color2 */
</pre>

Представленный выше код является всего лишь кратким списком функций работы с цветом в Sass. Полный список всех доступных функций расположен по адресу Sass Documentation (http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html).

"Цветовые" функции могут использоваться везде, где требуется работа с цветов в коде. Простой пример &#8211; объявлена переменная с цветом, к которой дальше в коде применяется функция затемнения цвета `darken`:

<pre>$color: #0982C1;
 
h1 {
  background: $color;
  border: 3px solid darken($color, 50%);
}
</pre>

#### LESS

<pre>lighten(@color, 10%); /* возвращает цвет на 10% светлее чем $color */
darken(@color, 10%);  /* возвращает цвет на 10% темнее чем $color */
 
saturate(@color, 10%);   /* возвращает цвет на 10% более насыщенный чем $color */
desaturate(@color, 10%); /* возвращает цвет на 10% менее насыщенный чем $color */
 
spin(@color, 10);  /* возвращает цвет, смещенный на 10 градусов вправо относительно цвета @color */
spin(@color, -10); /* возвращает цвет, смещенный на 10 градусов влево относительно цвета @color */
 
mix(@color1, @color2); /* возвращает результат смешивания цвета $color1 с цветом $color2 */
</pre>

Список функций препроцессора LESS находится на официальном сайте проекта LESS Documentation (http://lesscss.org/#-color-functions).

Ниже показан пример того, как можно применять "цветовые" функции в LESS:

<pre>@color: #0982C1;
 
h1 {
  background: @color;
  border: 3px solid darken(@color, 50%);
}
</pre>

#### Stylus

<pre>lighten(@color, 10%); /* возвращает цвет на 10% светлее чем $color */
darken(@color, 10%);  /* возвращает цвет на 10% темнее чем $color */
 
saturate(@color, 10%);   /* возвращает цвет на 10% более насыщенный чем $color */
desaturate(@color, 10%); /* возвращает цвет на 10% менее насыщенный чем $color */
</pre>

Полный список всех функций работы с цветом препроцессора Stylus представлен на сайте проекта Stylus Documentation (http://learnboost.github.com/stylus/docs/bifs.html).

И пример использования "цветовой" функции в Stylus:

<pre>color = #0982C1
 
h1
  background color
  border 3px solid darken(color, 50%)
</pre>

### Арифметические операции

Благодаря препроцессорам выполнение арифметических операций внутри CSS-кода теперь осуществляется просто и легко. Такая возможность часто бывает полезной. 

> *Прим. переводчика: стоит упомянуть о функции из CSS3 по имени `calc()`, которая также позволяет выполнять внутри CSS-кода простые арифметические операции.*

#### Sass, LESS & Stylus

<pre>body {
  margin: (14px/2);
  top: 50px + 100px;
  right: 100px - 50px;
  left: 10 * 10;
}
</pre>

### Практические примеры

Вот мы и рассмотрели основные моменты того, что и как умеют делать все три препроцессора. Однако мы еще ни разу не коснулись момента практического применения этих возможностей. Ниже показан список реальных веб-приложений, в которых используются препроцессоры, заметно улучшая при этом весь код.

#### Браузерные префиксы

Одним из наиболее ярких примеров преимущества использования препроцессоров является написание с их помощью свойств с браузерными префиксами. Один раз создав миксин с поддержкой браузерных префиксов, мы избавляем себя от рутинной работы.

Например, создадим для всех трех препроцессоров миксин скругления углов блока:

##### Sass

<pre>@mixin border-radius($values) {
  -webkit-border-radius: $values;
     -moz-border-radius: $values;
          border-radius: $values;
}
 
div {
  @include border-radius(10px);
}
</pre>

##### LESS

<pre>.border-radius(@values) {
  -webkit-border-radius: @values;
     -moz-border-radius: @values;
          border-radius: @values;
}
 
div {
  .border-radius(10px);
}
</pre>

##### Stylus

<pre>border-radius(values) {
  -webkit-border-radius: values;
     -moz-border-radius: values;
          border-radius: values;
}
 
div {
  border-radius(10px);
}
</pre>

##### Скомпилированный CSS

<pre>div {
  -webkit-border-radius: 10px;
     -moz-border-radius: 10px;
          border-radius: 10px;
}
</pre>

#### Трехмерный текст

Создание эффекта трехмерности для текста с помощью CSS-свойства `text-shadow` является прекрасной идеей. Единственная проблема заключается в работе с цветом, которая достаточно трудная и обременительная. Используя миксины и функции для работы с цветом, мы можем создать объемный текст и изменять его цвет на лету:

##### Sass

<pre>@mixin text3d($color) {
  color: $color;
  text-shadow: 1px 1px 0px darken($color, 5%),
               2px 2px 0px darken($color, 10%),
               3px 3px 0px darken($color, 15%),
               4px 4px 0px darken($color, 20%),
               4px 4px 2px #000;
}
 
h1 {
  font-size: 32pt;
  @include text3d(#0982c1);
}
</pre>

##### LESS

<pre>.text3d(@color) {
  color: @color;
  text-shadow: 1px 1px 0px darken(@color, 5%),
               2px 2px 0px darken(@color, 10%),
               3px 3px 0px darken(@color, 15%),
               4px 4px 0px darken(@color, 20%),
               4px 4px 2px #000;
}
 
span {
  font-size: 32pt;
  .text3d(#0982c1);
}
</pre>

##### Stylus

<pre>text3d(color)
  color: color
  text-shadow: 1px 1px 0px darken(color, 5%), 2px 2px 0px darken(color, 10%), 3px 3px 0px darken(color, 15%), 4px 4px 0px darken(color, 20%), 4px 4px 2px #000
span
  font-size: 32pt
  text3d(#0982c1)
</pre>

В примере для Stylus я выбрал вариант написания свойства `text-shadow` в одну строку, так как здесь я опустил фигурные скобки.

##### Скомпилированный CSS

<pre>span {
  font-size: 32pt;
  color: #0982c1;
  text-shadow: 1px 1px 0px #097bb7,
               2px 2px 0px #0875ae,
               3px 3px 0px #086fa4,
               4px 4px 0px #07689a,
               4px 4px 2px #000;
}
</pre>

#### Колонки

Использование переменных и числовых значений для этих переменных пришла мне в голову, когда я только начал знакомиться с возможностями CSS-препроцессоров. Объявление ширины для макета внутри переменной делает задачу изменения этой ширины (*при необходимости*) простой и быстрой:

##### Sass

<pre>$siteWidth: 1024px;
$gutterWidth: 20px;
$sidebarWidth: 300px;
 
body {
  margin: 0 auto;
  width: $siteWidth;
}
.content {
  float: left;
  width: $siteWidth - ($sidebarWidth+$gutterWidth);
}
.sidebar {
  float: left;
  margin-left: $gutterWidth;
  width: $sidebarWidth;
}
</pre>

##### LESS

<pre>@siteWidth: 1024px;
@gutterWidth: 20px;
@sidebarWidth: 300px;
 
body {
  margin: 0 auto;
  width: @siteWidth;
}
.content {
  float: left;
  width: @siteWidth - (@sidebarWidth+@gutterWidth);
}
.sidebar {
  float: left;
  margin-left: @gutterWidth;
  width: @sidebarWidth;
}
</pre>

##### Stylus

<pre>siteWidth = 1024px;
gutterWidth = 20px;
sidebarWidth = 300px;
 
body {
  margin: 0 auto;
  width: siteWidth;
}
.content {
  float: left;
  width: siteWidth - (sidebarWidth+gutterWidth);
}
.sidebar {
  float: left;
  margin-left: gutterWidth;
  width: sidebarWidth;
}
</pre>

##### Скомпилированный CSS

<pre>body {
  margin: 0 auto;
  width: 1024px;
}
.content {
  float: left;
  width: 704px;
}
.sidebar {
  float: left;
  margin-left: 20px;
  width: 300px;
}
</pre>

#### Некоторые уловки препроцессоров

Существует несколько хитростей при работе с CSS-препроцессорами. В этой статье я расскажу только о некоторой части из них. Но если эта тема вас заинтересовала, я рекомендую вам внимательно прочитать официальную документацию или же, что еще лучше, просто начните пользоваться препроцессором каждый день в процессе кодинга.

##### Сообщение об ошибках

Если вы уже пишите код на CSS достаточно давно, то наверняка сталкивались с ситуацией, когда внутри кода закралась ошибка, которую вы никак не можете найти. Если вы попадали в точно такую же ситуацию, то могу вас обрадовать &#8211; существует способ решить такую задачу.

CSS-препроцессоры могут сообщать об ошибках в коде и заставить их поступать таким образом достаточно просто. В этом случае препроцессор сам сообщает вам, в каком месте CSS-кода находиться ошибка (*и все счастливы*). Если вас заинтересовала подобная возможность во всех трех препроцессорах, то в этой статье (http://tjholowaychuk.com/post/5002088731/stylus-vs-sass-vs-less-error-reporting) подробно описано, как выполнить данную настройку.

##### Комментирование

В CSS-препроцессоре при компиляции из кода удаляются любые комментарии в виде двойного слеш&#8217;а (`// это комментарий`). Но, в тоже время, блочные комментарии (`/* это комментарий */`) остаются в коде без изменений.

На заметку: при компиляции в минимизированную версию CSS-файла *удаляются любые комментарии*.

### Заключение

Каждый из трех рассмотренный в этой статье CSS-препроцессоров (Sass, LESS и Stylus) обладает своим собственным, уникальным способом решения одной и той же задачи. Это дает в руки разработчика возможность выбора, каким способом выполнить поставленную задачу. Объединяет все препроцессоры способность расширить горизонты кодера с одновременным сохранением кросс-браузерности и чистоты кода.

> Препроцессоры не являются обязательным инструментом веб-разработчика. Однако, они предоставляют множество интересных возможностей при кодинге, сохраняя при этом массу времени и сил.

Я советую вам попробовать все известные препроцессоры, чтобы на личном опыте вы выбрали для себя наиболее предпочтительный. Если же до этого момента вы писали код только на чистом CSS, я настоятельно рекомендую вам научиться работать хотя бы в одном из препроцессоров.

Оцените статью:  
<span id="post-ratings-755" class="post-ratings" data-nonce="ffaeaf44eb"><img id="rating_755_1" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="1 Star" title="1 Star" onmouseover="current_rating(755, 1, '1 Star');" onmouseout="ratings_off(4.9, 5, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_755_2" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="2 Stars" title="2 Stars" onmouseover="current_rating(755, 2, '2 Stars');" onmouseout="ratings_off(4.9, 5, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_755_3" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="3 Stars" title="3 Stars" onmouseover="current_rating(755, 3, '3 Stars');" onmouseout="ratings_off(4.9, 5, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_755_4" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="4 Stars" title="4 Stars" onmouseover="current_rating(755, 4, '4 Stars');" onmouseout="ratings_off(4.9, 5, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_755_5" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_half.gif" alt="5 Stars" title="5 Stars" onmouseover="current_rating(755, 5, '5 Stars');" onmouseout="ratings_off(4.9, 5, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /> (<strong>24</strong> votes, average: <strong>4,92</strong> out of 5)<br /><span class="post-ratings-text" id="ratings_755_text"></span></span><span id="post-ratings-755-loading" class="post-ratings-loading"> <img src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/loading.gif" width="16" height="16" alt="Loading..." title="Loading..." class="post-ratings-image" />Loading...</span>