---
title: ":required"
name: required
author: ezhkov_d
co-authors:
designers:
contributors:
summary:
  - валидация
  - форма
  - form
  - обязательное
---

## Кратко

Псевдокласс `:required`, дополняющий основной селектор, поможет выбрать элементы [`<input>`](/html/doka/input), [`<textarea>`](/html/doka/textarea) или [`<select>`](/html/doka/select), у которых задан атрибут `required`.

## Пример


```html
<form>
  <div class="form-row">
    <label for="first_name">Имя*</label>
    <input type="text" id="first_name" required>
  </div>
  <div class="form-row">
    <label for="last_name">Фамилия</label>
    <input type="text" id="last_name">
  </div>
</form>
```


```css
input:required {
  outline: 2px solid blue;
}
```

Обязательное для заполнения поле ввода будет иметь синюю обводку.

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="css,result" data-user="ezhkov" data-slug-hash="BaLbMKG" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title=":required">
  <span>See the Pen <a href="https://codepen.io/ezhkov/pen/BaLbMKG">
  :required</a> by Denis Ezhkov (<a href="https://codepen.io/ezhkov">@ezhkov</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Как это понять

Если нужно как-то выделить обязательные для заполнения элементы форм можно использовать в селекторе псевдокласс `:required`.

:::callout ☝️

Обратите внимание, что использование этого псевдокласса эквивалентно [селектору по атрибуту](/css/doka/attribute-selector) `[required]`.

Использование псевдокласса `:required` допускается исключительно с селекторами полей формы. Использовать совместно с другими селекторами его бесполезно.

:::

## В работе

💡 Как правило, в реальных формах обязательные к заполнению поля выделяют не так явно, как в примерах выше. Обычно после текстового описания обязательного поля ставят звёздочку. В примере ниже, кроме того, показано, как можно стилизовать подсказку к полю.

```html
<form>
  <div class="form-row">
    <label for="first_name">Имя*</label>
    <input type="text" id="first_name" required>
    <span class="hint">Обязательно к заполнению</span>
  </div>
  <div class="form-row">
    <label for="last_name">Фамилия</label>
    <input type="text" id="last_name">
    <span class="hint">Необязательно</span>
  </div>
</form>
```

```css
.hint {
  color: #555555;
}

input:required + .hint {
  color: lightcoral;
}
```

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="css,result" data-user="ezhkov" data-slug-hash="mdrNzgw" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title=":required">
  <span>See the Pen <a href="https://codepen.io/ezhkov/pen/mdrNzgw">
  :required</a> by Denis Ezhkov (<a href="https://codepen.io/ezhkov">@ezhkov</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

{% include "authors/ezhkov_d/author.njk" %}
