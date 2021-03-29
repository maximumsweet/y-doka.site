---
title: Element.classList
name: element-classlist
author: windrushfarer
co-authors:
designers:
contributors:
tags:
  - sprint-4
summary:
  - классы
  - className
---

## Кратко

`Element.classList` даёт возможность просматривать и манипулировать [классами](/html/doka/class/) элемента.

## Пример

```js
const button = document.querySelector("button")

button.classList.add("active") // добавили класс
button.classList.remove("active") // удалили класс
button.classList.contains("active") // вернет false, т.к. класса у элемента нет
```

<p class="codepen" data-height="500" data-theme-id="light" data-default-tab="js,result" data-user="Windrushfarer" data-slug-hash="BaLREeZ" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="BaLREeZ">
  <span>See the Pen <a href="https://codepen.io/Windrushfarer/pen/BaLREeZ">
  Element.classList</a> by Egor Ogarkov (<a href="https://codepen.io/Windrushfarer">@Windrushfarer</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## Как понять

Управлять классами элемента — одна из распространенных задач, потому браузеры предоставляют встроенные средства для решения такой задачи. `Element.classList` — это специальный объект, который хранит информацию о текущих классах элемента и содержит методы для работы с ними.

```js
const button = document.querySelector("button")

button.classList.add("active")
button.classList[0] // 'active'
```

## Как пишется

У `Element.classList` есть множество методов, но мы рассмотрим только часто используемые.

### `Element.classList.add`

Этот метод используется для добавления класса к элементу. В качестве аргументов нужно передавать строку с именем класса.

```js
const element = document.querySelector("div")

// Добавится класс animate
element.classList.add("animate")
```

Можно так же передать несколько строк-аргументов, тогда добавится несколько классов:

```js
const element = document.querySelector("div")

// Добавятся классы black, fade и animate
element.classList.add("black", "fade", "animate")
```

:::callout 💡

Можно не боятся, что один тот же класс добавится два раза. Если вызвать метод `.add` и передать уже существующий класс, то он не добавится второй раз.

:::

```js
// Находим блок у которого уже есть класс header
const element = document.querySelector("div.header")

// Добавится только animate, т.к. header уже есть на элементе
element.classList.add("header", "animate")
```

### `Element.classList.remove`

Метод используется для удаления класса у элемента. В качестве аргумента нужно передавать строку с именем класса.

```js
// На кнопке есть класс submit, предположим что он единственный
const button = document.querySelector("button.submit")

// Убираем класс
button.classList.remove("submit")
button.classList[0] // undefined т.к. класса больше нет
```

В `.remove()` можно передать несколько аргументов и удалится несколько классов

```js
// Предположим следующий элемент
// <div class="banner hidden animated">...</div>
const elem = document.querySelector("div.banner")

// Убираем классы hidden и animated
button.classList.remove("hidden", "animated")
```

### `Element.classList.replace`

Метод позволяет заменить одно значение класса другим. Метод принимает 2 параметра:

- название класса, который нужно заменить
- название класса, на что нужно заменить

После выполнения `.replace()` возвращает boolean-значение, которые сообщает нам об успешности или неуспешности операции:

- `true` если класс был заменен
- `false` если ничего не изменилось

```js
// На кнопке есть класс hidden
const button = document.querySelector("button.hidden")

// Заменяем класс hidden на visible
const result = button.classList.replace("hidden", "visible")
console.log(result) // Будет true и класс успешно заменился на visible

// Попробуем заменить еще раз
const resultAgain = button.classList.replace("hidden", "visible")
console.log(result) // Теперь будет false, потому что ничего не изменилось
```

### `Element.classList.toggle`

Метод можно использовать чтобы включать или выключать класс. Если при вызове `.toggle()` переданный класс уже есть на элементе, то он будет убран. Если класса не было — то добавлен.

```js
// На кнопке есть класс hidden
const button = document.querySelector("button.hidden")

// так как класс есть, то он будет убран
button.classList.toggle("hidden")
// А при повторном вызове будет снова добавлен
button.classList.toggle("hidden")
```

Метод `.toggle()` принимает только один класс для переключения. Опционально вторым аргументом можно передать boolean-значение: метод будет работать как `.add()`, если передать `true`, и как `.remove()`, если передать `false`.

```js
// На кнопке есть класс submit, предположим что он единственный
const button = document.querySelector("button.submit")

// Передаем вторым аргументом false и будет работать как .remove()
button.classList.toggle("submit", false)
button.classList[0] // undefined, потому что класса больше нет

// Передаем true и теперь класс добавится
button.classList.toggle("submit", true)
```

### Имена клаcсов

:::callout ☝️

Классом не может быть строка содержащая пробелы. При попытке передать в аргументах такую строку, будет выброшена ошибка. Это правило касается любого метода в `classList`.

:::

```js
const element = document.querySelector("div")

// Метод не сработает и будет выброшена ошибка: Uncaught DOMException: String contains an invalid character
element.classList.add("my awesome class")
```

## В работе

🛠 `Element.classList` является псевдомассивом, поэтому разработчик может обращаться к классам по индексам, как в массиве. При этом новые классы добавляются в конец, а при удалении все классы (и соответственно их индексы) смещаются. При этом classList легко превращается в обычный массив, по которому можно итерироваться любым привычным способом.

```js
const element = document.querySelector("div")

// Можно через специальный метод
const classes = Array.fom(element.classList)

// Либо через оператор троеточия
const classes = [...element.classList]

// Теперь нам доступны любые операции обычного массива
classes.map(...)
classes.filter(...)
classes.reduce(...)
```

🛠 Вместо использования `Element.classList` можно попробовать пользоваться `Element.className`. Это поле содержит строку с именами всех классов через пробел.

Предположим у нас есть элемент шапки:

```html
<header class="head theme-light">content</header>
```

В поле `className` будет находится точно такая же строка что и в атрибуте элемента `class` (даже если в ней будут лишние пробелы).

```js
const head = document.querySelector("header")

// То же значение, что и в class-атрибуте элемента
head.className = "head theme-light"
```

С помощью этого поля можно легко менять класс элемента — достаточно происвоить ему новое значение. Если добавляете несколько классов, то их нужно обязательно указывать через пробел.

```js
// Используем элемент из предыдущего примера
const head = document.querySelector("div")

// Теперь у элемента шапки будет три класса
head.className = "head theme-dark bordered"
```

Однако, если с классами приходится работать часто или нужно сделать что-то сложнее, чем просто переопределить класс, то удобнее использовать методы из `classList`.
