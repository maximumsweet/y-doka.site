---
title: "Наследование в CSS"
name: inheritance
author: Roman_Ganin
co-authors:
designers:
contributors:
summary:
  - наследование
---

## Кратко

**Наследование в CSS** — это способность элементов-_потомков_ перенимать правила форматирования (свойства CSS), которые присвоены их _предкам_.

## Пример

```html
<p style="color: red">
  Весь <span>текст</span> в <em>этом</em> абзаце будет <b>красным</b>.
</p>
```

## Как это понять

Для некоторых HTML-тегов предопределены особые CSS-свойства по умолчанию (их ещё называют `user agent`-стили — т. е. стили от браузера), которые характерны только для _конкретно этих элементов_, например, `margin: 8px` для `<body>`, `color: #00c` для ссылок или `font-weight: bolder` для `<b>`. Их можно переопределить, но некоторые свойства (цвета текста, размера шрифта, внешнего вида курсора и другие) будут применяться для любых вложенных элементов, пока для них не будет указано иного значения. Такая наследуемость не случайна и обусловлена одним очень интересным CSS-значением у этих свойств — `inherit`, что буквально и значит «наследуемое».

Если у какого-то свойства указать значение `inherit` — оно будет взято у верхнего «родителя». Для некоторых CSS-свойств это значение указано по умолчанию.

## Наследуемые свойства

- Свойства шрифта: `font` и его «производных»: `font-style`, `font-variant`, `font-weight`, `font-stretch`, `font-size` и `font-family`; `color` и `line-height`;
- свойства межбуквенных и «межсловных» расстояний: `letter-spacing`, `word-spacing` и `white-space`;
- параметры текста: `text-align`, `text-indent`, `text-shadow`, `text-transform`;
- оформление пунктов списков: `list-style`, `list-style-type`, `list-style-position`;
- внешний вид курсора: `cursor` и отображение содержимого элемента `visablity`.

Например, в отличие от `color`, ненаследуемое свойство `border` не будет применено к вложенным элементам:

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="result" data-user="Realetive" data-slug-hash="pobKOjo" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="inherit color">
  <span>See the Pen <a href="https://codepen.io/Realetive/pen/pobKOjo">
  inherit color</a> by Roman Ganin (<a href="https://codepen.io/Realetive">@Realetive</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Но если мы укажем у `<p>` свойство `border` как `inherit` (т. е. наследуемое):

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="result" data-user="Realetive" data-slug-hash="eYzKLJZ" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="inherit border">
  <span>See the Pen <a href="https://codepen.io/Realetive/pen/eYzKLJZ">
  inherit border</a> by Roman Ganin (<a href="https://codepen.io/Realetive">@Realetive</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Подсказки

💡 Другой пример наследования — использование вместо указания цвета значения `currentColor` , который равен цвету текста текущего элемента, т. е. значению свойства `color`. Если `color` текущего элемента равен `inerit` (т. е. наследует значение «родителя»), то и `currentColor` также будет соответствовать текущему значению `color` «родителя». Причём это ключевое слово можно указывать в качестве значения для любого свойства, где значением является цвет, не только для `color`. См. раздел «В работе».

Значения [**rem / em**](/css/doka/rem-em) — также частный случай наследования кратного размера текста («родителя», если указан `em` и корневого тега в случае с `rem`).

Полный список наследуемых по умолчанию CSS-свойств помечен в [спецификации](https://www.w3.org/TR/CSS22/propidx.html) в колонке «Inherited?» значением `yes`.

Значение любого CSS-свойства можно «позаимствовать» («унаследовать») у родителя. Если «родителя» нет, `inherit` будет соответствовать значению по умолчанию для этого элемента.

## В работе

{% include "authors/ABatickaya/in-work.njk" %}

🛠 Удобно делать всякие трюки, используя `currentColor`. Мы не меняем явно цвет бордера по наведению курсора, но он меняется вслед за `color`.

```html
<button class="magick-btn">Волшебная кнопка</button>
```

```css
.magick-btn {
  padding: 15px;
  color: pink;
  border: 1px solid;
  border-color: currentColor;
  background-color: transparent;
  cursor: pointer;
  transition: all 0.2s;
}

.magick-btn:hover {
  color: darkblue;
}
```

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="result" data-user="solarrust" data-slug-hash="MWeBpma" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="MWeBpma">
  <span>See the Pen <a href="https://codepen.io/solarrust/pen/MWeBpma">
  MWeBpma</a> by Alena (<a href="https://codepen.io/solarrust">@solarrust</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

{% include "authors/Roman_Ganin/author.njk" %}
