---
title: "getElementById()"
name: getelementbyid
author: N_Lopin
co-authors:
designers:
contributors:
summary:
---

## Кратко

Метод объекта `document`, который позволяет найти элемент на веб-странице по его идентификатору(`id`). Возвращает [`Element`](/js/doka/element/) или `null`, если ничего не нашлось.

## Пример

```html
<html>
  <head></head>
  <body>
    <h1 id="title">Привет, незнакомец!</h1>
    <script>
      let title = document.getElementById("title")
      console.log(title.textContent) // напечатает "Привет, незнакомец!"
    </script>
  </body>
</html>
```

Живой пример:

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="js,result" data-user="Lopinopulos" data-slug-hash="XwKRaZ" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="XwKRaZ">
  <span>See the Pen <a href="https://codepen.io/Lopinopulos/pen/XwKRaZ">
  XwKRaZ</a> by Nikolai Lopin (<a href="https://codepen.io/Lopinopulos">@Lopinopulos</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## Как это понять

Метод работает с DOM, который связан с HTML разметкой. Если в HTML есть тег с атрибутом `id`, то его можно получить из JavaScript с помощью метода `getElementById`.

Спецификация HTML требует, чтобы в рамках одной страницы значения атрибутов `id` были уникальными. За счёт этого и работает метод `getElementById` — элемент с искомым идентификатором или один, или его нет. Такой поиск работает очень быстро.

## В работе

{% include "authors/n_lopin/in-work.njk" %}

🛠 С идентификаторами удобно работать, когда их немного. Они хорошо подходят для уникальных элементов на странице: единственного заголовка, элементов формы или самой формы. Не используй идентификаторы для повторяющихся элементов — элементов списков, повторяющихся полей.

🛠 Скрипты, которые работают с HTML видят только ту разметку, которую уже распарсил браузер. Браузер парсит HTML сверху вниз. Если скрипт находится вверху страницы, то он не найдет элементы ниже в странице — браузер их еще не увидел и ничего о них не знает. Поэтому скрипты либо подключают в конце страницы, либо [подписываются на событие](/js/doka/event-load-and-domcontentloaded/) `DOMContent​Loaded`, которое сигнализирует о том, что браузер распарсил весь HTML.

🛠 HTML спецификация требует уникальности идентификатора на странице, но сайт не сломается, если идентификаторы задублируются. До такого лучше не доводить, потому что поведение `getElementById` в этом случае не определено — метод может вернуть любой из элементов.

🛠 В отличие от других похожих методов: `getElementsByClassName` и `getElementsByTagName` , метод `getElementById` есть только у объекта `document`

{% include "authors/n_lopin/author.njk" %}
