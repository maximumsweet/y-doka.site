---
title: "<select>"
name: select
author: ezhkov_d
co-authors:
designers:
contributors:
summary:
  - тэг
  - тег
  - выпадашка
  - селект
  - <select>
  - выбор
---

## Кратко

Элемент `<select>` используется, когда нужно показать выпадающий список.

## Пример

```html
<form>
  <label for="city-select">Ваш город</label>
  <select name="city" id="city-select">
    <option value="">-- Выберите город --</option>
    <option value="petersburg">Санкт-Петербург</option>
    <option value="moscow">Москва</option>
    <option value="kazan">Казань</option>
    <option value="samara">Самара</option>
    <option value="perm">Пермь</option>
    <option value="novosibirsk">Новосибирск</option>
  </select>
</form>
```

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="html,result" data-user="ezhkov" data-slug-hash="dypzXYW" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="&amp;lt;select&amp;gt;">
  <span>See the Pen <a href="https://codepen.io/ezhkov/pen/dypzXYW">
  &lt;select&gt;</a> by Denis Ezhkov (<a href="https://codepen.io/ezhkov">@ezhkov</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Подробно

В примере выше показано типовое использование элемента `<select>`. Это своего рода обёртка над списком опций, которые задаются тегом [`<option>`](/html/doka/option/). Чтобы иметь возможность отправить выбранное значение на сервер, необходимо выполнить несколько условий:

- задать тегу `<select>` атрибут `name`;
- задать каждому тегу [`<option>`](/html/doka/option/) атрибут `value`. Если этот атрибут не задан, то его значение будет равно текстовому содержимому тега [`<option>`](/html/doka/option/).

Если нужно, чтобы изначально был выбран какой-то элемент из списка, нужно задать соответствующему тегу [`<option>`](/html/doka/option/) атрибут `selected`.

Внутри тега `<select>` могут использоваться только теги [`<option>`](/html/doka/option/) и [`<optgroup>`](/html/doka/optgroup/).

## Атрибуты

Тег `<select>` используется совместно с несколькими специфическими, а так же с большинством атрибутов для элементов форм.

### `autocomplete`

Разрешает автозаполнение. Автозаполнение — это когда браузер предлагает сохранить, например, выбранный город, чтобы данные подставлялись при следующем входе.

### `autofocus`

Атрибут булевого типа (без значения, либо атрибут есть в теге, либо его нет совсем). Если он указан, то при загрузке страницы фокус будет автоматически помещён на наш выпадающий список.

### `disabled`

Атрибут булевого типа. Если задан, то выпадающий список отключается для взаимодействия с пользователем. Если атрибут не задан, то он может быть унаследован у одного из предков (например у контейнера [`<fieldset>`](/html/doka/fieldset/) или [`<form>`](/html/doka/form/). Если ни у одного предка вверх по дереву этот атрибут не задан, то выпадающий список доступен для взаимодействия.

### `form`

Атрибут указывает на элемент [`<form>`](/html/doka/form/), с которым связан выпадающий список. Значением атрибута должен быть `id` формы в пределах текущего документа. Если атрибут не задан, то `<select>` обязательно должен находиться внутри тега [`<form>`](/html/doka/form/). Но если задать атрибут, то нахождение внутри формы не обязательно и `<select>` может находиться в любом месте страницы.

### `multiple`

Атрибут булевого типа. Включает возможность выбора сразу нескольких пунктов списка. Если атрибут задан, то внешний вид списка поменяется с однострочного на многострочный с возможностью скроллинга.

### `name`

Имя выпадающего списка. При отправке формы значение атрибута `name` будет ключом в отправляемом объекте.

### `required`

Атрибут булевого типа. Указывает, должен ли обязательно быть выбран какой-то пункт выпадающего списка, значение атрибута `value` которого — это не пустая строка. Атрибут учитывается при валидации формы при отправке. Если поле не заполнить, то при попытке отправки формы браузер покажет ошибку.

### `size`

Числовой атрибут. Если включен атрибут `multiple`, то это число указывает на количество видимых пунктов списка.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="html,result" data-user="ezhkov" data-slug-hash="oNzGMEB" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="&amp;lt;select disabled&amp;gt;">
  <span>See the Pen <a href="https://codepen.io/ezhkov/pen/oNzGMEB">
  &lt;select disabled&gt;</a> by Denis Ezhkov (<a href="https://codepen.io/ezhkov">@ezhkov</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Подсказки

💡 Выбрать несколько элементов списка, когда включен атрибут `multiple`, можно, используя клавиши <kbd>Ctrl</kbd>, <kbd>Cmd</kbd> и <kbd>Shift</kbd>. Клавиши <kbd>Ctrl</kbd> (Windows, Linux) и <kbd>Cmd</kbd> (Mac OS) работают одинаково. Мы зажимаем эту клавишу на клавиатуре, а затем кликаем мышкой в нужные пункты списка. Этим способом можно выбрать несколько пунктов, находящихся на разном расстоянии друг от друга. Если выбрать пункт списка, зажать клавишу <kbd>Shift</kbd> и выбрать любой другой, то будут выбраны последовательно все пункты списка между этими двумя.

## В работе

🛠 Выпадающий список — это один из элементов формы, почти не поддающихся стилизации. Мы можем немного изменить внешний вид самого элемента `<select>`, но выпадающий список опций вообще не стилизуется. Многие дизайнеры любят рисовать нестандартные выпадающие списки в угоду красоте, но реализация таких списков очень трудоёмка и невозможна на чистом HTML и CSS. Рекомендуется для выпадающих списков оставлять родной вид, потому что такие списки обладают рядом преимуществ перед нестандартными. Например, выпадающий список опций может выходить за границы окна браузера, давая пользователю возможность выбрать нужный элемент.

🛠 Несмотря на вышесказанное, немного стилизовать выпадающий список всё же можно. Но только отображение самого `<select>`, но не списка опций. Вот как можно изменить вид стрелочки:

```html
<form>
  <label for="city-select">Нестандартная стрелочка</label>
  <div class="select-wrapper">
    <select name="city" id="city-select">
      <option selected disabled>-- Выберите город --</option>
      <option value="petersburg">Санкт-Петербург</option>
      <option value="moscow">Москва</option>
      <option value="kazan">Казань</option>
      <option value="samara">Самара</option>
      <option value="perm">Пермь</option>
      <option value="novosibirsk">Новосибирск</option>
    </select>
  </div>
</form>
```

В данном случае мы оборачиваем наш `<select>` дополнительным блоком, чтобы задействовать псевдоэлемент [`::after`](/css/doka/after/) этого блока. К сожалению, `<select>` относится к такому типу элементов, у которых нет своих псевдоэлементов [`::before`](/css/doka/before/) и [`::after`](/css/doka/after/).

```css
.select-wrapper {
  position: relative;
}

.select-wrapper::after {
  content: "⬇️";
  position: absolute;
  right: 0;
  margin-top: -2px;
  pointer-events: none;
}

select {
  appearance: none;
  width: 200px;
  padding: 4px;
  border-color: #aaa;
  border-radius: 3px;
}
```

Используем свойство `appearance`, чтобы отключить браузерную стрелку справа. В качестве стрелки ставим псевдоэлемент [`::after`](/css/doka/after/) от родительского блока. Не забываем про позиционирование, а также отключаем у псевдоэлемента взаимодействие с мышкой, иначе при клике на него выпадающий список раскрываться не будет.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="html,result" data-user="ezhkov" data-slug-hash="YzGEKjP" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="&amp;lt;select&amp;gt; custom">
  <span>See the Pen <a href="https://codepen.io/ezhkov/pen/YzGEKjP">
  &lt;select&gt; custom</a> by Denis Ezhkov (<a href="https://codepen.io/ezhkov">@ezhkov</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
