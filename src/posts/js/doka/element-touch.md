---
title: "Element.touch"
name: element-touch
author: Windrushfarer
co-authors:
designers:
contributors:
tags:
summary:
  - touchstart
  - touchend
  - touchcancel
  - touchmove
---

## Кратко

[События](/js/doka/events/) `touch` происходят при касании HTML элемента на тач-экранах. Сюда входит как прикосновение пальцами, так и работа со стилусом. В зависимости от того, какое действие пользователь произвел (прикоснулся, начал двигать пальцем и т.д.) произойдет то или иное событие `touch`:

- `touchstart` - срабатывает при первом касании
- `touchmove` - срабатывает по время движения пальцем по элементу
- `touchend` - срабатывает после окончания прикосновения
- `touchcancel` - сработает когда событие было прервано

## Как пишется

Обработчик начала касания по элементу (аналог `mousedown`):

```js
element.addEventListener("touchstart", (event) => {
  console.log("Вы приложили палец к элементу")
})
```

Подписаться на событие, когда пользователь водит пальцем по элементу (аналог `mousemove`):

```js
element.addEventListener("touchmove", (event) => {
  console.log("По мне ведут пальцем")
})
```

Подписаться на событие, когда пользователь закончил прикосновение (аналог `mouseup`):

```js
element.addEventListener("touchend", (event) => {
  console.log("Прикосновение закончено")
})
```

## Как понять

Когда пользователь работает с компьютером, то чаще всего взаимодействие с элементами на экране происходит с помощью курсора. Для обработки клика нам хватает встроенного сообытия [_click_](/js/doka/element-click/). Событие _click_ так же работает, если пользователь работает с интерфейсом через смартфон или планшет и взаимодействует с помощью касаний по экрану.

Однако, на мобильных устройствах есть не только нажатия, но и жесты, и мультитач. Чтобы дать разработчикам возможность обрабатывать тактие сложные действия пользователей, браузеры стали предоставлять низкоуровнение API для обработки touch-событий. С их помощью можно построить интерфейсы с обработкой мультитача и жестов.

Несмотря на то, что `touch` события очень похоже на `click`, главное их отличие заключается в поддержке нескольких касаний в разных местах экрана (мультитач). Всего у `touch` имеется 4 различных события:

- `touchstart` - произойдет, в момент когда пользователь прикоснулся к элементу
- `touchmove` - произойдет, когда пользователь ведет пальцем по элементу
- `touchend` - произойдет, когда пользователь убрал палец с элемента (закончил прикосновение)
- `touchcancel` - произойдет, если событие было прервано, например, если будет слишком много одноверменных точек прикосновения либо палец ушел за пределы элемента или экрана

Событие касания `TouchEvent`, которое передается в обработчик, содержит несколько полезных полей:

- `touches` - массив, который содержит объекты всех точек касаний на экране (полезно для обработки мультитач)
- `targetTouches` - массив, который содержит объекты всех точек касаний на вызываемом элементе

Рисовалка ниже использует поля события и типы событий касаний. Используйте смартфон, так как касания не работают при использовании мыши.

<p class="codepen" data-height="500" data-theme-id="light" data-default-tab="js,result" data-user="Windrushfarer" data-slug-hash="RwGjopb" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="RwGjopb">
  <span>See the Pen <a href="https://codepen.io/Windrushfarer/pen/RwGjopb">
  Touch Draw</a> by Egor Ogarkov (<a href="https://codepen.io/Windrushfarer">@Windrushfarer</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## В работе

🛠 Стоит учесть, что браузеры в ответ на некоторые действия пользователя отправляют одновременно и событие click и событие touch. Например при прикосновении к элементу (допустим по кнопке) последовательность событий будет следующей:

> `touchstart` -> `touchend` -> `mousedown` -> `mouseup` -> `click`

Стоит помнить эту особенность, если вы на одном и этом же элементе делаете обработку этих событий. Если необходимо, чтобы события мыши не возникали на элементе, то в обработчике события касания нужно вызвать `preventDefault()`.

```js
element.addEventListener('touchstart', (event) => {
  // События мыши теперь не будут вызываться
  event.preventDefault()
  ...
})
```

🛠 С помощью `touch` событий можно делать обработку жестов. Например, свайпов. Для этого необходимо будет сохранять координаты, где пользователь прикоснулся (событие `touchstart`), и сравнивать с изменением координат во время движения пальца (событие `touchmove`). Подробнее можно посмотреть в примере.

<p class="codepen" data-height="500" data-theme-id="light" data-default-tab="js,result" data-user="Windrushfarer" data-slug-hash="KKgZGEq" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="KKgZGEq">
  <span>See the Pen <a href=" https://codepen.io/Windrushfarer/pen/KKgZGEq">
  Touch Draw</a> by Egor Ogarkov (<a href="https://codepen.io/Windrushfarer">@Windrushfarer</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
