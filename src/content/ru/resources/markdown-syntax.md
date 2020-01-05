путь_проекта: /web/_project.yaml
book_path: /web/resources/_book.yaml
описание: это описание страницы, помещенное в заголовок.

{# wf_updated_on: 2017-09-20 #}
{# wf_published_on: 2016-09-13 #}

# Синтаксис уценки {: .page-title}

{% include "web / _shared / contributors / petelepage.html"%}

Web **Fundamental** предоставляет широкий выбор стилизованных элементов и CSS
классы для использования в документации. Хотя вы можете дополнить эти стили
пользовательский CSS, вы должны использовать пользовательский CSS только в случае крайней необходимости если ты
обнаружите, что вам нужно создать новый стиль, который будет применяться более чем к
одну страницу, пожалуйста, напишите вопрос на GitHub, чтобы другие страницы могли использовать его
также. Это обеспечивает согласованность всего сайта.

Примечание. Этот документ дополняет разработчика [Google.
руководство по стилю документации](/style/) . Если есть различия, то
Официальное руководство по стилю имеет приоритет, если не указано иное.

## Заголовки

Самым верхним заголовком страницы является заголовок страницы. Тело страницы не должно
содержит еще один заголовок уровня 1, чтобы избежать путаницы в невизуальных браузерах.

**Когда я должен использовать заглавные буквы?**

Используйте [предложение](/style/capitalization#capitalization-in-titles-and-headings) ,
для **всех** заголовков и заголовков разделов.

Да, мы не согласны с этим, но мы пытаемся это исправить, пожалуйста, сделайте
лучше всего придерживаться этих рекомендаций.

## Заголовок 2 {: # заголовок-что-что}

Внимание: если вы планируете ссылку на конкретные заголовки
[`a href="#heading-what-what"`](#heading-what-what) в вашем документе,
**настоятельно** рекомендуется определить их самостоятельно с помощью
`{: #anchor-name }` синтаксис. Это гарантирует, что когда документы локализованы,
якорь все еще будет работать, но также гарантирует, что любая разница между
Процессоры уценки не являются проблемой.

### Заголовок 3

DevSite автоматически добавит элементы `<h2>` и `<h3>`
к содержанию. Чтобы не допустить добавления (как эти два здесь,
которые не отображаются в оглавлении), примените `class="hide-from-toc"` .
Вы также можете поместить `<h2>` или `<h3>` в заголовок таблицы ( `<th>` ), чтобы принудительно
таблица в оглавление. Внутри заголовка таблицы, `<h2>` и `<h3>`
стилизованы под обычный текст, поэтому читатели не смогут сказать.

#### Заголовок 4

##### Заголовок 5

###### Заголовок 6

```
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

## Образец кода

Если ваш вклад содержит код, убедитесь, что он соответствует
[Руководство по стилю кодирования Google для JavaScript](https://google.github.io/styleguide/javascriptguide.xml) .
В противном случае нам придется попросить вас внести изменения, и это ни для кого не доставит удовольствия.

### Встроенный код

Чтобы указать диапазон кода, заключите его в кавычки (`). В отличие от
предварительно отформатированный кодовый блок, диапазон кода указывает код в нормальном абзаце.
Например:
Используйте функцию `printf()` .
Приведет к:
Используйте функцию `printf()` .

### Кодовые блоки

Чтобы создать блок кода в Markdown, просто сделайте отступ в каждой строке блока:
не менее 4 пробелов или 1 таб. Например, учитывая этот вход:
Вот пример AppleScript:
расскажите приложение "Фу"
гудок
конец сказать
приведет к:
Вот пример AppleScript:
расскажите приложение "Фу"
гудок
конец сказать
Внутри блока кода амперсанды ( `&` ) и угловые скобки ( `<` и `>` )
автоматически конвертируется в HTML-сущности. Это позволяет очень легко включить
пример исходного кода HTML с использованием Markdown - просто вставьте его и сделайте отступ, и
Markdown справится с трудностями кодирования амперсандов и угловых скобок.
Предупреждение: перенос кодовых блоков в `&<>` не поддерживается
DevSite. DevSite не будет автоматически стилизовать эти блоки и нашу интеграцию
тесты не пройдут.

### Выделив

Используйте `<strong>` чтобы привлечь внимание к содержанию внутри блока `<pre>` . Делать это
осветит окружающий контент, чтобы подчеркнуть раздел, выделенный
`<strong>` блок. Например:

<pre class="prettyprint">
// ...
// ...
// ...
для (i = 0; i <10; i ++) {
printf ("Подсчет% d \ n", i);
<strong>if (i% 3 == 0) {
SomeFunc (я);
}</strong>
}
// ...
// ...
// ...
</pre>

```
<pre class="prettyprint">
// ...
// ...
// ...
for (i = 0; i < 10; i++) {
    printf("Counting %d\n", i);
    <strong>if (i % 3 == 0) {
        someFunc(i);
    }</strong>
}
// ...
// ...
// ...
</pre>
```

### Нажмите, чтобы скопировать

Click to copy автоматически включается для всех блоков кода.

### Special Case: Templates -  {{}}

Если вам нужно включить шаблоны в примеры кода, обязательно избегайте их.
Например:

<pre class="prettyprint">
<pre class="prettyprint">
<polymer-media-query query="max-width:640px" queryMatches="{{isPhone}}"></pre>
</pre>


Если он встроенный, вам нужно будет обернуть его в блок ` <code>` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





</code> {pre1} {code2}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code2} {/pre1} {code3}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code3} {figure4} {code5}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code5} {figure6} {code7}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code7} {figcaption8} {code9}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code9} {/figcaption8} {code10}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code10} {/figure6} {code11}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code11} {figure12} {code13}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code13} {figcaption14} {code15}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code15} {/figcaption14} {code16}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code16} {/figure12} {code17}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code17} {div18} {code19}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code19} {figure20} {code21}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code21} {figcaption22} {code23}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code23} {/figcaption22} {code24}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code24} {/figure20} {code25}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code25} {/div18} {code26}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code26} {/div27}{div27} {code28}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code28} {div29} {code30}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code30} {figure31} {code32}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code32} {figcaption33} {code34}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code34} {/figcaption33} {code35}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code35} {/figure31} {code36}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code36} {/div29} {code37}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code37} {div38} {/div38} {code39}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code39} {div40} {code41}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code41} {figure42} {code43}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code43} {figcaption44} {code45}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code45} {/figcaption44} {code46}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code46} {/figure42} {code47}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code47} {/div40} {code48}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code48} {div49} {code50}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code50} {figure51} {code52}` block instead of backticks.

* Declarative two-way data-binding: <input id="input" value="{{foo}}">

## Images
When adding a caption, wrap images in ` ` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.


This caption should be used to describe the image.

For example:


This caption should be used to describe the image.

Note: Optimized images are served automatically only for `index.yaml` pages,
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right



Figure 1 : Alert dialog


The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.




Figure 1 : Alert dialog


Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a ` ` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.




DO : This is the right thing to do





{/code52}т / 350x150" >
{figcaption53}
{b54}Не{/b54} надо: это неправильно
{/figcaption53}
{/figure51}
{/div49}
{/div55}{div55}
{div56}
{figure57}
{img58}
{figcaption59}
{b60}DO{/b60} : Это правильно
{/figcaption59}
{/figure57}
{/div56}
{div61}
{figure62}
{img63}
{figcaption64}
{b65}Не{/b65} надо: это неправильно
{/figcaption64}
{/figure62}
{/div61}
## выноски
Примечание. Этот тип выноски является обычной запиской или подсказкой.
Внимание: этот тип выноски предлагает действовать с осторожностью.
Предупреждение: этот тип выноски сильнее, чем предостережение; это значит «Не делай этого».
Успех: этот тип выноски описывает успешное действие или статус без ошибок. Используется только в интерактивном или динамическом контенте; не используйте в обычных статических страницах.
Ключевой момент: этот тип выноски определяет важную концепцию.
Ключевой термин: этот тип выноски определяет важную терминологию.
Цель: этот тип выноски определяет цель процедуры.
Корм для собак: Этот тип выноски предназначен для заметок, которые временно применяются во время внутреннего тестирования корма для собак. Удалите все выноски Dogfood, прежде чем сделать документ публично видимым.
## Сравнения
{p66} {span67}Не рекомендуется{/span67} - отступ для вкладок {/p66}
{pre68} (неверный пример кода) {/pre68}
{p69} {span70}Рекомендуется{/span70} - отступ с пробелами {/p69}
{pre71} (хороший пример кода) {/pre71}
{p72} {span73}Не допускается{/span73} - отступ с пробелами {/p72}
{pre74} (очень плохой пример кода) {/pre74}
## Списки
### Неупорядоченный
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
* Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
### Заказал
1. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
2. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
3. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
4. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
5.Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
1. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
2. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
1. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
2. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
3. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
6. Lorem Ipsum Dolor Sit Amet, Concetetur Adipiscing Elit.
## Таблицы
Таблицы поддерживаются со стандартной разметкой. Вот типичный стол с
строка заголовка, несколько обычных строк и строка, помеченная как ` {tr75} `,
который производит более темный фон, который можно использовать в качестве альтернативного заголовка.
{table76}
{tr77}
{th78} Один {/th78}
{th79} Два {/th79}
{th80} Три {/th80}
{/tr77}
{tr81}
{td82} 1,0 {/td82}
{td83} 2,0 {/td83}
{td84} 3.0 {/td84}
{/tr81}
{tr85}
{td86} 1,1 {/td86}
{td87} 2,1 {/td87}
{td88} 3,1 {/td88}
{/tr85}
{tr89}{td90} Вот некоторые цифры, заканчивающиеся на .2! {/td90}{/tr89}
{tr91}
{td92} 1.2 {/td92}
{td93} 2,2 {/td93}
{td94} 3,2 {/td94}
{/tr91}
{/table76}
{table95}
{tr96}
{th97} Один {/th97}
{th98} Два {/th98}
{th99} Три {/th99}
{/tr96}
{tr100}
{td101} 1,0 {/td101}
{td102} 2,0 {/td102}
{td103} 3.0 {/td103}
{/tr100}
{tr104}
{td105} 1,1 {/td105}
{td106} 2,1 {/td106}
{td107} 3,1 {/td107}
{/tr104}
{tr108}{td109} Вот некоторые цифры, заканчивающиеся на .2! {/td109}{/tr108}
{tr110}
{td111} 1.2 {/td111}
{td112} 2,2 {/td112}
{td113} 3,2 {/td113}
{/tr110}
{/table95}
### Адаптивные таблицы
Чтобы сделать таблицу адаптивной, добавьте в нее класс «отзывчивый».
{table114}
{tbody115}
{tr116}
{th117} параметры {/th117}
{/tr116}
{tr118}
{td119} {code120}value{/code120} {/td119}
{td121}
{code122}String{/code122} {br123} значение выбора, которое респонденты видят как ярлык при просмотре формы {/td121}
{/tr118}
{tr124}
{td125} {code126}navigationType{/code126} {/td125}
{td127}
{code128}<a href="#">PageNavigationType</a>{/code128} {br129} выбор типа навигации {/td127}
{/tr124}
{/tbody115}
{/table114}
* В таблице должно быть *** только два столбца ***: первый столбец для определяемых вещей (ключ) и второй столбец для всей информации об этом ключе, если необходимо, в нескольких строках. Это ограничение в два столбца означает, что адаптивные таблицы не могут использоваться для действительно двумерных табличных данных, сравнения объектов на основе галочек, но они хорошо подходят для справочной информации (или любых других данных, которые могут быть разумно выражены списком определений вместо стол).span translate = "no"> * Если есть несколько строк информации о ключе - скажем, тип и описание - оберните каждую строку в ` {p130} `заставить разрывы строк (вместо` {br131} `).
* В строке заголовка должна быть только одна ячейка. Используйте ` {/p130}
{th132} `заставить его охватить оба столбца. Чтобы напомнить вам об этом, мы автоматически скрываем любые {/th132}
{th133} `после первого (который преднамеренно выглядит очень разбитым).
{/div134}{div134}
{table135}
{tbody136}
{tr137}
{th138} параметры {/th138}
{/tr137}
{tr139}
{td140}
{code141}value{/code141}
{/td140}
{td142}
{code143}String{/code143} {br144}
значение выбора, которое респонденты видят как ярлык при просмотре формы
{/td142}
{/tr139}
{tr145}
{td146}
{code147}navigationType{/code147}
{/td146}
{td148}
{code149}
PageNavigationType
{/code149}
{br150} выбор типа навигации
{/td148}
{/tr145}
{/tbody136}
{/table135}
### Невидимые таблицы
Вы можете расположить текст в столбцах или сделать таблицу невидимой, используя
` {table151} ... {/table151} `. Это обычно используется для организации
длинные узкие списки.span translate = "no"> {table152}
{tr153}
{td154}
{code155}auto{/code155} {br156}
{code157}break{/code157} {br158}
{code159}case{/code159} {br160}
{code161}char{/code161}
{/td154}
{td162}
{code163}const{/code163} {br164}
{code165}continue{/code165} {br166}
{code167}default{/code167} {br168}
{code169}do{/code169}
{/td162}
{td170}
{code171}double{/code171} {br172}
{code173}else{/code173} {br174}
{code175}enum{/code175} {br176}
{code177}extern{/code177}
{/td170}
{/tr153}
{/table152}
{table178}
{tr179}
{td180}
{code181}auto{/code181} {br182}
{code183}break{/code183} {br184}
{code185}case{/code185} {br186}
{code187}char{/code187}
{/td180}
{td188}
{code189}const{/code189} {br190}
{code191}continue{/code191} {br192}
{code193}default{/code193} {br194}
{code195}do{/code195}
{/td188}
{td196}
{code197}double{/code197} {br198}
{code199}else{/code199} {br200}
{code201}enum{/code201} {br202}
{code203}extern{/code203}
{/td196}
{/tr179}
{/table178}
## Внешние ссылки
Чтобы пометить ссылку как внешнюю, используйте
{a204}Внешняя ссылка{/a204}
авторство в HTML, или добавьте `{: .external}` к ссылкам при авторизации в
Markdown.
{a205}внешняя ссылка{/a205}
## Пользовательские атрибуты и именованные якоря
Markdown поддерживает пользовательские атрибуты разметки для элементов HTML уровня блока и
заголовки.
Формат для этого учитывает пользовательский класс, пользовательский идентификатор и / или пользовательский
пары атрибут / значение в одном выражении:
Это параграф.
{: .customClass #custom_id attribute = 'value'}
Это создает этот HTML:
{p206} Это параграф. {/p206}
### Пользовательские атрибуты в заголовках
Поскольку заголовки могут быть определены только в одной строке, список атрибутов должен быть
определяется в конце определения заголовка:
## Заголовок с пользовательским идентификатором {: #custom_id}
Формирует:
{h2207} Заголовок с пользовательским идентификатором {/h2207}
## Блок цитата
> Lorem Ipsum Dolor Sit Amet, Заклинатель Adipiscing Elit.
> Lorem Ipsum Dolor Sit Amet, Заклинатель Adipiscing Elit.
## Подсказки
Любой элемент, имеющий атрибут `title`, покажет всплывающую подсказку (со значением
атрибута) при наведении курсора. Например: "... когда-нибудь экран
{abbr208}ИЦП{/abbr208} может увеличиться дальше ... »
(обратите внимание, что пунктирное подчеркивание происходит от элемента abbr, а не от подсказки).
...odiay экран {abbr209}PPI{/abbr209} может увеличиться в дальнейшем ...
Предупреждение. Обязательно используйте всплывающие подсказки только для дополнительной информации, а не для основного текста или основных функций взаимодействия с пользователем, поскольку наличие всплывающих подсказок не очевидно, а пользователи мобильных устройств их вообще не видят.
## Разные занятия
Используйте `class =" inline "`, `class =" inline-block "` и `class =" block "` для принудительной установки
inline, inline-block или block layout в тех редких случаях, когда это необходимо.
Используйте `class =" clearfix "`, чтобы очистить плавающий элемент, например, после использования
`попытка влево` или` попытка вправо`.
## Комментарии
Однострочный комментарий и многострочный комментарий имеют разный синтаксис. Оба
удалены из веб-страниц, которые создаются при постановке или публикации.
### Однострочные комментарии
Комментарий в одну строку. Хэш-символы (#), используемые так, зарезервированы только для
однострочные комментарии.
{pre210}
{# Путешествие во времени это весело #}
{/pre210}
### Многострочные комментарии
Многострочный комментарий с начальным и конечным тегами, окружающими комментарий.
{pre211}
{% comment%}
Путешествие во времени это весело.
Я делаю это буквально все время.span translate = "no"> {% endcomment%}
{/pre211}
{/th133}
{/tr75}{/figure4}
