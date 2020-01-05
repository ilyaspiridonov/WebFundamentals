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
<polymer-media-query query="max-width:640px" queryMatches="{{isPhone}}">
</pre>
</pre>


If it's inline, you'll need to wrap it in a `<code>` block instead of backticks.
<pre class="prettyprint">
* Declarative two-way data-binding: <code><input id="input" value="{{foo}}"></code>
</pre>
## Images
When adding a caption, wrap images in `<figure>` blocks, and ideally, use
responsive images with the `scrset` attribute when possible. Be sure you
include `alt` attributes for your images as well.
<figure>
  <img src="https://placehold.it/350x150" alt="sample image">
  <figcaption>This caption should be used to describe the image.</figcaption>
</figure>
For example:
    <figure>
      <img src="https://placehold.it/350x150" alt="sample image">
      <figcaption>This caption should be used to describe the image.</figcaption>
    </figure>
Note: Optimized images are served automatically only for `index.yaml` pages, 
simply provide a 2x version, and the server will do the rest.
You can apply `class="screenshot"` to an image to give it a border that
offsets it from nearby text. This is typically used for screenshots that have
white backgrounds and otherwise get lost on the page. Don't use it for images
that don't need it.
### Floating images on the right
<div class="attempt-right">
  <figure>
    <img src="https://placehold.it/350x150" alt="Alert dialog">
    <figcaption><b>Figure 1</b>: Alert dialog</figcaption>
  </figure>
</div>
The image at right also has `class="attempt-right"`, which floats the image
right on larger screens, but forces the image into vertical layout on smaller
screens, tablets and smaller, where floating right would cause problems. Also
available is `class="attempt-left"`. To use `attempt-left` and `attempt-right`
together, make sure the `attempt-left` element comes first.
<div class="clearfix"></div>
    <div class="attempt-right">
      <figure>
        <img src="https://placehold.it/350x150" alt="Alert dialog">
        <figcaption><b>Figure 1</b>: Alert dialog</figcaption>
      </figure>
    </div>
Caution: When using `attempt-left` and `attempt-right`, it may be necessary to include a `<div class="clearfix"></div>` block.
### Do and do not images
Add the class `success` or `warning` to the figure caption
to indicate a good or bad example.
<div class="attempt-left">
  <figure>
    <img src="https://placehold.it/350x150" alt="Alert dialog">
    <figcaption class="success">
      <b>DO</b>: This is the right thing to do
     </figcaption>
  </figure>
</div>
<div class="attempt-right">
  <figure>
    <img src="https://placehold.it/350x150" alt="Alert dialog">
    <figcaption class="warning">
      <b>DON'T</b>: This is the wrong thing to do
     </figcaption>
  </figure>
</div>
<div class="clearfix"></div>
    <div class="attempt-left">
      <figure>
        <img src="https://placehold.it/350x150" alt="Alert dialog">
        <figcaption class="success">
          <b>DO</b>: This is the right thing to do
         </figcaption>
      </figure>
    </div>
    <div class="attempt-right">
      <figure>
        <img src="https://placehold.it/350x150" alt="Alert dialog">
        <figcaption class="warning">
          <b>DON'T</b>: This is the wrong thing to do
         </figcaption>
      </figure>
    </div>
## Callouts
Note: This type of callout is an ordinary note or tip.
Caution: This type of callout suggests proceeding with caution.
Warning: This type of callout is stronger than a Caution; it means "Don't do this."
Success: This type of callout describes a successful action or an error-free status. Used only in interactive or dynamic content; don't use in ordinary static pages.
Key Point: This type of callout defines an important concept.
Key Term: This type of callout defines important terminology.
Objective: This type of callout defines the goal of a procedure.
Dogfood: This type of callout is for notes that apply temporarily during internal dogfood testing. Remove all Dogfood callouts before making a document publicly visible.
## Comparisons
<p><span class="compare-worse">Not recommended</span> — indent with tabs</p>
<pre class="prettyprint">(bad sample code)</pre>
<p><span class="compare-better">Recommended</span> — indent with spaces</p>
<pre class="prettyprint">(good sample code)</pre>
<p><span class="compare-no">Not allowed</span> — indent with spaces</p>
<pre class="prettyprint">(very bad sample code)</pre>
## Lists
### Unordered
* Lorem ipsum dolor sit amet, consectetur adipiscing elit.
* Lorem ipsum dolor sit amet, consectetur adipiscing elit.
* Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    * Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    * Lorem ipsum dolor sit amet, consectetur adipiscing elit.
* Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    * Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        * Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        * Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    * Lorem ipsum dolor sit amet, consectetur adipiscing elit.
* Lorem ipsum dolor sit amet, consectetur adipiscing elit.
### Ordered
1. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
2. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
3. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
4. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
5. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    1. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    2. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        1. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        2. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    3. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
6. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
## Tables
Tables are supported with standard markup. Here's a typical table with a
heading row, several regular rows, and a row marked up as `<tr class="alt">`,
which produces a darker background that can be used as an alternate header.
<table>
  <tr>
<th>One</th>
<th>Two</th>
<th>Three</th>
</tr>
  <tr>
<td>1.0</td>
<td>2.0</td>
<td>3.0</td>
</tr>
  <tr>
<td>1.1</td>
<td>2.1</td>
<td>3.1</td>
</tr>
  <tr class="alt"><td colspan="3">Here come some numbers that end in .2!</td></tr>
  <tr>
<td>1.2</td>
<td>2.2</td>
<td>3.2</td>
</tr>
</table>
    <table>
      <tr>
<th>One</th>
<th>Two</th>
<th>Three</th>
</tr>
      <tr>
<td>1.0</td>
<td>2.0</td>
<td>3.0</td>
</tr>
      <tr>
<td>1.1</td>
<td>2.1</td>
<td>3.1</td>
</tr>
      <tr class="alt"><td colspan="3">Here come some numbers that end in .2!</td></tr>
      <tr>
<td>1.2</td>
<td>2.2</td>
<td>3.2</td>
</tr>
    </table>
### Responsive tables
To make a table responsive, add the `responsive` class to the table.
<table class="responsive">
  <tbody>
    <tr>
      <th colspan="2">Parameters</th>
    </tr>
    <tr>
      <td><code>value</code></td>
<td>
<code>String</code><br>the choice's value, which respondents see as a label when viewing the form</td>
    </tr>
    <tr>
      <td><code>navigationType</code></td>
<td>
<code><a href="#">PageNavigationType</a></code><br>the choice's navigation type</td>
    </tr>
  </tbody>
</table>
* There must be ***only two columns*** in the table: the first column for the things being defined (the key), and the second column for all information about that key, in multiple lines if necessary. This two-column restriction means that responsive tables cannot be used for truly two-dimensional tabular data, checkmark-based feature comparison, but they are well suited for reference information (or anything other data that could reasonably be expressed by a definition list instead of a table).
* If there are multiple lines of information about the key — say, a type and a description — wrap each line in `<p>` to force line breaks (instead of `<br>`).
* There must be only one cell in the header row. Use `</p>
<th colspan="2">` to force it to span both columns. To remind you of this behavior, we automatically hides any `</th>
<th>` after the first (which intentionally looks very broken).
<div class="clearfix"></div>
    <table class="responsive">
      <tbody>
        <tr>
          <th colspan="2">Parameters</th>
        </tr>
        <tr>
          <td>
            <code>value</code>
          </td>
          <td>
            <code>String</code><br>
            the choice's value, which respondents see as a label when viewing the form
          </td>
        </tr>
        <tr>
          <td>
            <code>navigationType</code>
          </td>
          <td>
            <code>
              <a href="#">PageNavigationType</a>
            </code>
            <br>the choice's navigation type
          </td>
        </tr>
      </tbody>
    </table>
### Invisible tables
You can arrange text in columns, or otherwise make a table invisible, using
`<table class="columns">...</table>`. This is typically used for arranging
long narrow lists.
<table class="columns">
  <tr>
    <td>
      <code>auto</code><br>
      <code>break</code><br>
      <code>case</code><br>
      <code>char</code>
    </td>
    <td>
      <code>const</code><br>
      <code>continue</code><br>
      <code>default</code><br>
      <code>do</code>
    </td>
    <td>
      <code>double</code><br>
      <code>else</code><br>
      <code>enum</code><br>
      <code>extern</code>
    </td>
  </tr>
</table>
    <table class="columns">
      <tr>
        <td>
          <code>auto</code><br>
          <code>break</code><br>
          <code>case</code><br>
          <code>char</code>
        </td>
        <td>
          <code>const</code><br>
          <code>continue</code><br>
          <code>default</code><br>
          <code>do</code>
        </td>
        <td>
          <code>double</code><br>
          <code>else</code><br>
          <code>enum</code><br>
          <code>extern</code>
        </td>
      </tr>
    </table>
## External links
To mark a link as external, use
`<a href="https://www.google.com/" class="external">External Link</a>` when
authoring in HTML, or append `{: .external}` to links when authoring in
Markdown.
<a href="https://www.google.com/" class="external">External Link</a>
## Custom attributes and named anchors 
Markdown supports custom markup attributes for block level HTML elements and
headers.
The format for this allows for a custom class, a custom ID, and/or custom
attribute/value pairs in the same statement:
    This is a paragraph.
    {: .customClass #custom_id attribute='value' }
This generates this HTML:
    <p class="customClass" id="custom_id" attribute="value">This is a paragraph.</p>
### Custom attributes on headers
As headers can only be defined in one line, the attributes list should be
defined at the end of the header definition:
    ## Header with custom ID {: #custom_id }
Generates:
    <h2 id="custom_id">Header with custom ID</h2>
## Block quote
    > Lorem ipsum dolor sit amet, consectetur adipiscing elit.
> Lorem ipsum dolor sit amet, consectetur adipiscing elit.
## Tooltips
Any element that has a `title` attribute will show a tooltip (with the value
of the attribute) on mouseover. For example: "...someday screen
<abbr title="pixels per inch">PPI</abbr> may increase further..."
(note that the dotted underline comes from the abbr element, not the tooltip).
    ...someday screen <abbr title="pixels per inch">PPI</abbr> may increase further...
Warning: Be sure to use tooltips only for supplemental information—not essential text or primary user-experience features—since the presence of tooltips is not obvious and users on mobile devices will not see them at all.
## Miscellaneous classes
Use `class="inline"`, `class="inline-block"`, and `class="block"` to force
inline, inline-block, or block layout, in the rare cases when it is necessary.
Use `class="clearfix"` to clear a floated element, for example after using
`attempt-left` or `attempt-right`.
## Comments
A one-line comment and a multi-line comment have different syntax. Both are
removed from the web pages that are produced when staging or publishing.
### One line comments
A one-line comment. Hash characters (#) used like this are reserved only for
one-line comments.
<pre class="prettyprint">
{# Time travel is fun #}
</pre>
### Multi-line comments
A multi-line comment, with start and end tags surrounding the comment.
<pre class="prettyprint">
{% comment %}
Time travel is fun.
I do it literally all the time.
{% endcomment %}
</pre>
</th>
</tr></figure></code>

