---
title: Создаем эффект маскирования фона на CSS
author: gearmobile
excerpt: Сегодня мы рассмотрим пошаговый процесс создания впечатляющей технологии, которую можно использовать для создания эффекта, очень похожего на параллакс, не используя при этом ни строчки Javascript; она может быть достигнута с помощью очень простого способа и на чистом CSS.
layout: post
permalink: /masked-background-effect-with-css/
cleanretina_sidebarlayout:
  - default
ratings_users:
  - 4
ratings_score:
  - 20
ratings_average:
  - 5
categories:
  - Статьи по CSS
tags:
  - css
---
Сегодня мы рассмотрим пошаговый процесс создания впечатляющей технологии, которую можно использовать для создания эффекта, очень похожего на параллакс, не используя при этом ни строчки Javascript; она может быть достигнута с помощью очень простого способа и на чистом CSS.

Прежде чем продолжить чтение, посмотрите на [демо-результат][1], чтобы сразу оценить, что мы будет изучать в данной статье (чтобы увидеть эффект, вам необходимо воспользоваться настольным компьютером или ноутбуком).

Данный прием может быть применен для создания страниц с описанием продукта или даже для своего рода презентаций типа Powerpoint/Keynote. В этом приеме кроется большой потенциал для создания иллюстрированных online-страниц.

Ниже описан способ, как можно добиться такого результата.

### Это все CSS

Основой данного приема является CSS-свойство `background-attachment: fixed`, которое доступно для использования веб-разработчиками, начиная с версии CSS2.1. Любое фоновое изображение, к которому применено данное свойство, начинает занимать фиксированное положение относительно окна браузера. Мы воспользуемся данным свойством для того, чтобы зафиксировать иллюстрации страницы в определенном месте, в то время как весь остальной контент будет перемещаться при прокрутке.

Стоит обратить внимание на пару моментов относительно данного CSS-свойства &#8211; оно применяется для фоновых изображений и задает им фиксированное положение относительно окна браузера; на изображение с данным свойством не оказывают влияние CSS-свойство margin, как если бы это было с обычными фоновыми изображениями.

Также необходимо помнить, что данное CSS-свойство прекрасно работает в десктопных версиях браузеров; однако в мобильной версии браузера Chrome оно работает некорректно, а в остальных мобильных браузерах возможно отображение страницы рывками. Поэтому, несмотря на то, что посетители с мобильных устройств будут прекрасно видеть все изображения на странице, сам эффект скроллинга лучше всего смогут оценить пользователи настольных систем.

### Основные шаги

Основные шаги, которые нужно выполнить, чтобы получить тот результат, который был на демо-странице, следующие:

  1. Создать элемент-контейнер и наполнить его содержимым
  2. Задать для контейнера (в нашем случае это блок `div`) с одной стороны padding, равный 50%-м от ширины контейнера, таким образом сдвинув весь контент в противоположную сторону
  3. Добавить на страницу фоновое изображение шириной, равной 50%-м от ширины контейнера и поместить его на противоположной стороне от контента
  4. Задать для фонового изображения CSS-свойство `background-attachment: fixed;` и любоваться результатом!

Давайте шаг за шагом детально разберемся с тем, как все это делается. Для статьи подготовлены исходные материалы, которые вы можете получить по [данной ссылке][2], так что в вашем распоряжении уже будут готовые изображения нужного размера.

### 1. Основная настройка

Для начала давайте создадим папку проекта и добавим в нее индексный файл **index.html**, а также папку **css** с вложенным в нее файлом стилей **style.css**. Скопируйте и поместите четыре изображения из скачанного архива в папку с именем **images**.

Добавьте следующую HTML-разметку в файл **index.html**:

<pre>
  
    
    
      

<div class="content right illustration_01">
  <h2>
    Scroll Down and Watch What Happens
  </h2>
          
  
  <p>
    Alice was beginning to get very tired of sitting by her sister on the bank, and of having nothing to do: once or twice she had peeped into the book her sister was reading, but it had no pictures or conversations in it, `and what is the use of a book,' thought Alice `without pictures or conversation?'
  </p>
          
  
  <p>
    So she was considering in her own mind (as well as she could, for the hot day made her feel very sleepy and stupid), whether the pleasure of making a daisy- chain would be worth the trouble of getting up and picking the daisies, when suddenly a White Rabbit with pink eyes ran close by her.
  </p>
          
  
  <p>
    There was nothing so very remarkable in that; nor did Alice think it so very much out of the way to hear the Rabbit say to itself, `Oh dear! Oh dear! I shall be late!' (when she thought it over afterwards, it occurred to her that she ought to have wondered at this, but at the time it all seemed quite natural); but when the Rabbit actually took a watch out of its waistcoat- pocket, and looked at it, and then hurried on, Alice started to her feet, for it flashed across her mind that she had never before seen a rabbit with either a waistcoat-pocket, or a watch to take out of it, and burning with curiosity, she ran across the field after it, and fortunately was just in time to see it pop down a large rabbit-hole under the hedge.
  </p>
          
  
  <p>
    In another moment down went Alice after it, never once considering how in the world she was to get out again.
  </p>
          
  
  <p>
    The rabbit-hole went straight on like a tunnel for some way, and then dipped suddenly down, so suddenly that Alice had not a moment to think about stopping herself before she found herself falling down a very deep well.
  </p>
          
  
  <p>
    Either the well was very deep, or she fell very slowly, for she had plenty of time as she went down to look about her and to wonder what was going to happen next. First, she tried to look down and make out what she was coming to, but it was too dark to see anything; then she looked at the sides of the well, and noticed that they were filled with cupboards and book-shelves; here and there she saw maps and pictures hung upon pegs. She took down a jar from one of the shelves as she passed; it was labelled `ORANGE MARMALADE', but to her great disappointment it was empty: she did not like to drop the jar for fear of killing somebody, so managed to put it into one of the cupboards as she fell past it.
  </p>
          
  
  <p>
    `Well!' thought Alice to herself, `after such a fall as this, I shall think nothing of tumbling down stairs! How brave they'll all think me at home! Why, I wouldn't say anything about it, even if I fell off the top of the house!' (Which was very likely true.) 
  </p>
        
</div>
    
  
  </pre>

Данным действием мы создали основной HTML-каркас страницы, подключили к нему файл CSS-стилей и шрифт Roboto с сервиса Google Fonts. Внутри HTML-каркаса мы создали первый блок-контейнер div с содержимым, к которому будем применять CSS-свойства.

Блок-контейнер div имеет три класса:

  1. `.content` &#8211; служит для задания CSS-свойств, общих для всех блоков-контейнеров;
  2. `.right` &#8211; задает контейнеру правило для смещения его содержимого вправо (немного позже мы будет создавать контейнеры со смещенным влево контентом);
  3. `.illustration_01` &#8211; создает правило для использования конкретного фонового изображения и для задания фонового цвета блока-контейнера.

### Стилизация

Теперь у нас все готово для создания CSS-стилей нашей страницы. Начнем с добавления в файл **style.css** основных правил сброса стилей и форматирования шрифта:

<pre>* {
    box-sizing: border-box;
  }
  html {
    font-size: 1em;
    font-family: 'Alike';
    background-color: #262626;
    color: #d9d9d9;
  }
  body {
    margin: 0;
  }
  img {
    max-width: 100%;
    height: auto;
  }
  h1,h2,h3,h4,h5,h6 {
    font-family: 'Roboto';
    line-height: 1.313em;
  }
  h1 {
    font-size: 3em;
    margin: 0.563em 0;
  }
  h2 {
    font-size: 2.25em;
    margin: 0.625em 0;
  }
  h3 {
    font-size: 1.5em;
    margin: 1.313em 0;
  }
  h4 {
    font-size: 1.313em;
    margin: 1.313em 0;
  }
  h5 {
    font-size: 1.125em;
    margin: 1.313em 0;
  }
  h6 {
    font-size: 1em;
    margin: 0.75em 0;
  }
  </pre>

Затем переходим к классу `.content`. Добавим внизу таблицы стилей следующее содержимое:

<pre>.content {
    font-size: 1.875rem;
    color: #262626;
    background-size: 49% auto;
    background-attachment: fixed;
    background-repeat: no-repeat;
  }
  </pre>

В этом классе заключена почти вся магия нашего примера. Для текста задаем размер шрифта и цвет. Для фона блока-контейнера задаем свойство `background-size: 49% auto;`.

Это означает, что фоновое изображение блока будет всегда растягиваться или сжиматься в своем размере, стремясь заполнить 49% от ширины страницы; высота изображения при этом будет изменяться пропорционально. В нашем примере мы используем значение 49% вместо 50%, потому что браузер Firefox иначе будет отображать артефакт в виде странной линии по середине окна браузера.

Затем мы задаем правило `background-attachment: fixed;`, которое, как вы уже знаете из предыдущего описания, заставляет фоновое изображение занимать фиксированное положение относительно окна браузера.

И наконец, мы задаем правило `background-repeat: no-repeat;` чтобы наше изображение повторялось только один раз на странице.

Теперь добавим в стили еще один класс `.right`:

<pre>.right {
    padding: 1.618em 6.472em 3.236em 50%;
    background-position: 0 50%;
  }
  </pre>

Этот последний класс помещает текст контейнера в одной половине экрана, а фоновое изображение &#8211; в другой половине.

Правило `background-position: 0 50%;` задает для фонового изображения нулевую позицию относительно левого края окна браузера и выравнивает его точно по центру по вертикали окна.

Наконец, для класса `.illustration_01` добавляем следующее содержимое:

<pre>.illustration_01 {
    background-color: #00c17b;
    background-image: url("../images/minipadwhite.png");
  }
  </pre>

Таким образом задается конкретное изображение и фоновый цвет контейнера.

Проверим нашу страницу &#8211; мы должны увидеть следующий результат:<figure id="attachment_1452" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/07/image_01.png" alt="Страница с одним блоком-контейнером" width="600" height="310" class="size-full wp-image-1452" />][3]<figcaption class="wp-caption-text">Страница с одним блоком-контейнером</figcaption></figure> 

Когда вы будете прокручивать страницу вниз, то увидите, что содержимое этой страницы будет перемещаться, в то время как изображение будет оставаться на своем месте.

### Добавляем второй контейнер

Давайте добавим еще один контейнер, в котором содержимое будет смещено влево.

Добавьте HTML-контейнер ниже последнего блока div:

<pre><div class="content left illustration_02">
  <h2>
    Fixed Background Scrolling Effect
  </h2>
      
  
  <p>
    Down, down, down. Would the fall never come to an end! `I wonder how many miles I've fallen by this time?' she said aloud. `I must be getting somewhere near the centre of the earth. Let me see: that would be four thousand miles down , I think--' (for, you see, Alice had learnt several things of this sort in her lessons in the schoolroom, and though this was not a very good opportunity for showing off her knowledge, as there was no one to listen to her, still it was good practice to say it over) `--yes, that's about the right distance--but then I wonder what Latitude or Longitude I've got to?' (Alice had no idea what Latitude was, or Longitude either, but thought they were nice grand words to say .)
  </p>
      
  
  <p>
    Presently she began again. `I wonder if I shall fall right through the earth! How funny it'll seem to come out among the people that walk with their heads downward! The Antipathies, I think--' (she was rather glad there was no one listening, this time, as it didn't sound at all the right word) `--but I shall have to ask them what the name of the country is, you know. Please, Ma' am, is this New Zealand or Australia?' (and she tried to curtsey as she spoke-- fancy curtseying as you're falling through the air! Do you think you could manage it?) `And what an ignorant little girl she'll think me for asking! No, it'll never do to ask: perhaps I shall see it written up somewhere.'
  </p>
      
  
  <p>
    Down, down, down. There was nothing else to do, so Alice soon began talking again. `Dinah'll miss me very much to-night, I should think!' (Dinah was the cat .) `I hope they'll remember her saucer of milk at tea-time. Dinah my dear! I wish you were down here with me! There are no mice in the air, I'm afraid, but you might catch a bat, and that's very like a mouse, you know. But do cats eat bats, I wonder?' And here Alice began to get rather sleepy, and went on saying to herself, in a dreamy sort of way, `Do cats eat bats? Do cats eat bats?' and sometimes, `Do bats eat cats?' for, you see, as she couldn't answer either question, it didn't much matter which way she put it. She felt that she was dozing off, and had just begun to dream that she was walking hand in hand with Dinah, and saying to her very earnestly, `Now, Dinah, tell me the truth: did you ever eat a bat?' when suddenly, thump! thump! down she came upon a heap of sticks and dry leaves, and the fall was over.
  </p>
      
  
  <p>
    Alice was not a bit hurt, and she jumped up on to her feet in a moment: she looked up, but it was all dark overhead; before her was another long passage, and the White Rabbit was still in sight, hurrying down it. There was not a moment to be lost: away went Alice like the wind, and was just in time to hear it say, as it turned a corner, `Oh my ears and whiskers, how late it's getting!' She was close behind it when she turned the corner, but the Rabbit was no longer to be seen: she found herself in a long, low hall, which was lit up by a row of lamps hanging from the roof.
  </p>
      
  
  <p>
    There were doors all round the hall, but they were all locked; and when Alice had been all the way down one side and up the other, trying every door, she walked sadly down the middle, wondering how she was ever to get out again. 
  </p>
    
</div>
  </pre>

Обратите внимание, что на этот раз мы используем класс `.left` вместо класса `.right`; также изменяем порядковый номер класса `.illustration_01` на `.illustration_02`.

Добавляем два новых класса в таблицу стилей:

<pre>.left {
    padding: 1.618em 50% 3.236em 6.472em;
    background-position: 100% 50%;
  }
  .illustration_02 {
    background-color: #e8697b;
    background-image: url("../images/minipadblack.png");
  }
  </pre>

На этот раз мы добавляем padding, равный 50%, с правой стороны блока-контейнера так, чтобы контент внутри блока смещался влево; фоновое изображение позиционируем по горизонтали на 100% &#8211; другими словами, вправо до упора. Также добавляем другой цвет для фоновой заливки блока и меняем файл изображения для фоновой картинки.

Снова проверим результат нашей работы и прокрутим страницу вниз в окне браузера. Когда мы достигнем нижнего края первого блока-контейнера то увидим, как начнет появляться верхний край второго блока, постепенно скрывая при этом первое фоновое изображение и открывая второе:<figure id="attachment_1453" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/07/image_02.png" alt="Страница с двумя блоками-контейнерами" width="600" height="309" class="size-full wp-image-1453" />][4]<figcaption class="wp-caption-text">Страница с двумя блоками-контейнерами</figcaption></figure> 

### Добавляем блок-разделитель

Наш пример будет гораздо эффектнее смотреться, если мы добавим блок-разделитель между двумя блоками-контейнерами. Давайте так и поступим.

Между двумя блоками div вставляем следующий HTML-код:

<pre>&lt;section class="separator">
    

<h3>
  Another Section Starts Here
</h3>
  &lt;/section>
  </pre>

И для него в таблице стилей создаем отдельный класс с несколькими правилами:

<pre>.separator {
    font-size: 1.875rem;
    padding: 1.618em 0;
    text-align: center;
  }
  </pre>

Теперь, если обновить нашу страницу-пример, то мы заметим, как между двумя контейнерами появился замечательный блок-разделитель:<figure id="attachment_1454" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/07/image_03.png" alt="Блок-разделитель" width="600" height="396" class="size-full wp-image-1454" />][5]<figcaption class="wp-caption-text">Блок-разделитель</figcaption></figure> 

### Третий и четвертый контейнеры

Пример почти готов и мы можем добавить в него оставшиеся блоки-разделители и блоки-контейнеры. Для этого вставим нижеследующий HTML-код в индексную страницу **index.html**:

<pre>&lt;section class="separator">
    

<h3>
  Another Section Starts Here
</h3>
  &lt;/section>
  

<div class="content right illustration_03">
  <h2>
    Great For Product Presentations
  </h2>
      
  
  <p>
    Suddenly she came upon a little three-legged table, all made of solid glass; there was nothing on it except a tiny golden key, and Alice's first thought was that it might belong to one of the doors of the hall; but, alas! either the locks were too large, or the key was too small, but at any rate it would not open any of them. However, on the second time round, she came upon a low curtain she had not noticed before, and behind it was a little door about fifteen inches high: she tried the little golden key in the lock, and to her great delight it fitted!
  </p>
      
  
  <p>
    Alice opened the door and found that it led into a small passage, not much larger than a rat-hole: she knelt down and looked along the passage into the loveliest garden you ever saw. How she longed to get out of that dark hall, and wander about among those beds of bright flowers and those cool fountains, but she could not even get her head though the doorway; `and even if my head would go through,' thought poor Alice, `it would be of very little use without my shoulders. Oh, how I wish I could shut up like a telescope! I think I could, if I only know how to begin.' For, you see, so many out-of-the-way things had happened lately, that Alice had begun to think that very few things indeed were really impossible.
  </p>
      
  
  <p>
    There seemed to be no use in waiting by the little door, so she went back to the table, half hoping she might find another key on it, or at any rate a book of rules for shutting people up like telescopes: this time she found a little bottle on it, (`which certainly was not here before,' said Alice,) and round the neck of the bottle was a paper label, with the words `DRINK ME' beautifully printed on it in large letters.
  </p>
      
  
  <p>
    It was all very well to say `Drink me,' but the wise little Alice was not going to do that in a hurry. `No, I'll look first,' she said, `and see whether it's marked "poison" or not'; for she had read several nice little histories about children who had got burnt, and eaten up by wild beasts and other unpleasant things, all because they would not remember the simple rules their friends had taught them: such as, that a red-hot poker will burn you if you hold it too long; and that if you cut your finger very deeply with a knife, it usually bleeds; and she had never forgotten that, if you drink much from a bottle marked `poison,' it is almost certain to disagree with you, sooner or later.
  </p>
      
  
  <p>
    However, this bottle was NOT marked `poison,' so Alice ventured to taste it, and finding it very nice, (it had, in fact, a sort of mixed flavour of cherry- tart, custard, pine-apple, roast turkey, toffee, and hot buttered toast,) she very soon finished it off. 
  </p>
    
</div>
  &lt;section class="separator">
    

<h3>
  Another Section Starts Here
</h3>
  &lt;/section>
  

<div class="content left illustration_04">
  <h2>
    Simple Technique Using Pure CSS
  </h2>
      
  
  <p>
    `What a curious feeling!' said Alice; `I must be shutting up like a telescope .'
  </p>
      
  
  <p>
    And so it was indeed: she was now only ten inches high, and her face brightened up at the thought that she was now the right size for going though the little door into that lovely garden. First, however, she waited for a few minutes to see if she was going to shrink any further: she felt a little nervous about this; `for it might end, you know,' said Alice to herself, `in my going out altogether, like a candle. I wonder what I should be like then?' And she tried to fancy what the flame of a candle is like after the candle is blown out, for she could not remember ever having seen such a thing.
  </p>
      
  
  <p>
    After a while, finding that nothing more happened, she decided on going into the garden at once; but, alas for poor Alice! when she got to the door, she found he had forgotten the little golden key, and when she went back to the table for it, she found she could not possibly reach it: she could see it quite plainly through the glass, and she tried her best to climb up one of the legs of the table, but it was too slippery; and when she had tired herself out with trying, the poor little thing sat down and cried.
  </p>`Come, there's no use in crying like that!' said Alice to herself, rather sharply; `I advise you to leave off this minute!' She generally gave herself very good advice, (though she very seldom followed it), and sometimes she scolded herself so severely as to bring tears into her eyes; and once she remembered trying to box her own ears for having cheated herself in a game of croquet she was playing against herself, for this curious child was very fond of pretending to be two people. `But it's no use now,' thought poor Alice, `to pretend to be two people! Why, there's hardly enough of me left to make ONE respectable person!'
      
  
  <p>
    Soon her eye fell on a little glass box that was lying under the table: she opened it, and found in it a very small cake, on which the words `EAT ME' were beautifully marked in currants. `Well, I'll eat it,' said Alice, `and if it makes me grow larger, I can reach the key; and if it makes me grow smaller, I can creep under the door; so either way I'll get into the garden, and I don't care which happens!'
  </p>
      
  
  <p>
    She ate a little bit, and said anxiously to herself, `Which way? Which way?', holding her hand on the top of her head to feel which way it was growing, and she was quite surprised to find that she remained the same size: to be sure, this generally happens when one eats cake, but Alice had got so much into the way of expecting nothing but out-of-the-way things to happen, that it seemed quite dull and stupid for life to go on in the common way.
  </p>
      
  
  <p>
    So she set to work, and very soon finished off the cake. 
  </p>
    
</div>
  &lt;section class="separator">
    

<h1>
  THE END
</h1>
  &lt;/section>
  </pre>

И добавим в таблицу стилей классы для двух оставшихся фоновых изображений:

<pre>.illustration_03 {
    background-color: #14b29a;
    background-image: url("../images/miniwhite.png");
  }
  .illustration_04 {
    background-color: #80b9f1;
    background-image: url("../images/miniblack.png");
  }
  </pre>

Теперь потребуется вся ширина монитора для того, чтобы отобразились третий и четвертый блоки-контейнеры:<figure id="attachment_1455" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/07/image_04.png" alt="Третий и четвертый блоки-контейнеры" width="600" height="308" class="size-full wp-image-1455" />][6]<figcaption class="wp-caption-text">Третий и четвертый блоки-контейнеры</figcaption></figure> 

Прокручиваем страницу до конца и видим последний блок-разделитель:<figure id="attachment_1456" style="width: 600px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/07/image_05.png" alt="Последний блок-разделитель" width="600" height="309" class="size-full wp-image-1456" />][7]<figcaption class="wp-caption-text">Последний блок-разделитель</figcaption></figure> 

### Делаем страницу адаптивной

Последний штрих, который нам необходимо выполнить &#8211; это учесть вариант отображения нашей страницы на экранах устройств с разными размерами. Когда область просмотра страницы становится слишком маленькой для того, чтобы вмешать фоновые изображения, нам необходимо сделать так, чтобы картинки страницы из фоновых становились встраиваемыми (через тег \`img\`).

Для этого в начале каждого из блоков-контейнеров вставим еще один блок `figure` с классом `.smallscreen`, внутри которого поместим тег `img` для вставки тех же самых изображений, которые мы использовали для фона нашей страницы.

Для первого блока-контейнера добавим в его начало:

<pre><div class="smallscreen">
  &lt;image src="images/minipadwhite.png">&lt;/image>
    
</div>
  </pre>

Второй блок-контейнер будет содержать:

<pre>&lt;figure class="smallscreen">
    &lt;image src="images/minipadblack.png">
  &lt;/figure>
  </pre>

Начало третьего блока-контейнера:

<pre>&lt;figure class="smallscreen">
    &lt;image src="images/miniwhite.png">
  &lt;/figure>
  </pre>

Четвертый контейнер:

<pre>&lt;figure class="smallscreen">
    &lt;image src="images/miniblack.png">
  &lt;/figure>
  </pre>

Класс `.smallscreen` мы будем использовать для того, чтобы по умолчанию скрывать изображения `<image src="images/miniblack.png">`, но показывать их, когда размер экрана становиться маленьким.

Для этого добавим в таблицу стилей следующее правило:

<pre>.smallscreen {
    display: none;
  }
  </pre>

И затем добавим медиа-запросы, которые будут отвечать за то, отображать ли на странице изображение как фоновую картинку или же как встроенную (*обычную*) картинку. Они также будут отвечать за то, чтобы пропорционально уменьшать размер текста страницы и расстояния в разметке таким образом, чтобы ширина страницы точно отвечала различной ширине области просмотра экрана устройств.

Для этого добавим медиа-запросы в таблицу стилей:

<pre>@media (max-width: 106.25rem) {
    .wrapper,
    .separator {
      font-size: 1.6875rem;
    }
  }
  @media (max-width: 93.75rem) {
    .content,
    .separator {
      font-size: 1.5rem;
    }
    .right {
      padding: 1.618em 4.854em 1.618em 50%;
    }
    .left {
      padding: 1.618em 50% 1.618em 4.854em;
    }
  }
  @media (max-width: 81.25rem) {
    .content,
    .separator {
      font-size: 1.3125rem;
    }
    .right {
      padding: 1.618em 3.236em 1.618em 45%;
      background-size: 44% auto;
      background-position: 0 55%;
    }
    .left {
      padding: 1.618em 45% 1.618em 3.236em;
      background-size: 44% auto;
      background-position: 100% 55%;
    }
  }
  @media (max-width: 68.75rem) {
    .content,
    .separator {
      font-size: 1.125rem;
    }
    .right {
      padding: 1.618em 3.236em 1.618em 40%;
      background-size: 39% auto;
      background-position: 0 60%;
    }
    .left {
      padding: 1.618em 40% 1.618em 3.236em;
      background-size: 39% auto;
      background-position: 100% 60%;
    }
  }
  @media (max-width: 50rem) {
    .smallscreen {
      display: block;
    }
    .right {
      padding: 1.618em 3.236em;
      background-image: none;
    }
    .left {
      padding: 1.618em 3.236em;
      background-image: none;
    }
  }
  @media (max-width: 31.25rem) {
    .right {
      padding: 1.618em 1.618em;
    }
    .left {
      padding: 1.618em 1.618em;
    }
  }
  @media (max-width: 12rem) {
    html {
      min-width: 12rem;
    }
  }
  </pre>

В приведенном выше коде первые четыре медиа-запроса просто уменьшают размер теста страницы и padding внутри блоков-контейнеров таким образом, чтобы ширина страницы соответсвовала ширине экрана.

В пятом медиа-запросе с правилом `max-width: 50rem` мы включаем код, который делает класс `.smallscreen` видимым, удаляет 50%-ый padding у содержимого блока-контейнера и скрывает фоновое изображение на странице. Когда медиа-запрос &#8220;обнаруживает&#8221;, что большое фоновое изоражение больше не вписывается в размер окна, он заменяет фоновое изображение на обычное, которое помещается в начале контента блока-контейнера.

Теперь после обновления уменьшаем страницу и в результате получаем плавно изменяемую ширину, которая подстаивается под различные размеры областей просмотра, до тех пор, пока размер не станет самым маленьким:<figure id="attachment_1457" style="width: 471px;" class="wp-caption aligncenter">

[<img src="http://localhost:7788/third/wp-content/uploads/2014/07/image_06-471x600.png" alt="Самый маленький размер экрана" width="471" height="600" class="size-medium wp-image-1457" />][8]<figcaption class="wp-caption-text">Самый маленький размер экрана</figcaption></figure> 

### Заключение

Даже после многих лет работы с CSS я не устаю удивляться все увеличивающемуся количеству потрясающих вещей, которые можно сделать с помощью CSS. И чем проще прием, тем более впечатляющий получается результат.

Попробуйте сами создать описанный выше прием &#8211; это быстро и легко и должно вам понравиться!

Оригинал статьи размещен здесь &#8211; &#8220;<a href="http://webdesign.tutsplus.com/tutorials/a-visual-demonstration-of-background-attachment-fixed--cms-21112" title="Create a Masked Background Effect With CSS" target="_blank">Create a Masked Background Effect With CSS</a>&#8220;

Оцените статью:  
<span id="post-ratings-1450" class="post-ratings" data-nonce="d757691b91"><img id="rating_1450_1" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="1 Star" title="1 Star" onmouseover="current_rating(1450, 1, '1 Star');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1450_2" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="2 Stars" title="2 Stars" onmouseover="current_rating(1450, 2, '2 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1450_3" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="3 Stars" title="3 Stars" onmouseover="current_rating(1450, 3, '3 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1450_4" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="4 Stars" title="4 Stars" onmouseover="current_rating(1450, 4, '4 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /><img id="rating_1450_5" src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/stars_crystal/rating_on.gif" alt="5 Stars" title="5 Stars" onmouseover="current_rating(1450, 5, '5 Stars');" onmouseout="ratings_off(5, 0, 0);" onclick="rate_post();" onkeypress="rate_post();" style="cursor: pointer; border: 0px;" /> (<strong>4</strong> votes, average: <strong>5,00</strong> out of 5)<br /><span class="post-ratings-text" id="ratings_1450_text"></span></span><span id="post-ratings-1450-loading" class="post-ratings-loading"> <img src="http://localhost:7788/third/wp-content/plugins/wp-postratings/images/loading.gif" width="16" height="16" alt="Loading..." title="Loading..." class="post-ratings-image" />Loading...</span>

 [1]: http://goo.gl/AXcG4t "демо-результат"
 [2]: http://goo.gl/J0XMVV
 [3]: http://localhost:7788/third/wp-content/uploads/2014/07/image_01.png
 [4]: http://localhost:7788/third/wp-content/uploads/2014/07/image_02.png
 [5]: http://localhost:7788/third/wp-content/uploads/2014/07/image_03.png
 [6]: http://localhost:7788/third/wp-content/uploads/2014/07/image_04.png
 [7]: http://localhost:7788/third/wp-content/uploads/2014/07/image_05.png
 [8]: http://localhost:7788/third/wp-content/uploads/2014/07/image_06.png