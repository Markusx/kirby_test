A lot of people use css ui kits like bootstrap, semantic-ui and require default class names for html elements.

```html
<h1 class="ui large header">1st Heading</h1>
<h2 class="ui medium header">2nd Heading</h2>
<ul class="ui list">
  <li class="ui item">first item</li>
  <li class="ui item">second item</li>
</ul>
```

Showdown does not support this out of the box. But you can create an extension to accomplish this:

```js
const showdown = require('showdown');

const classMap = {
  h1: 'ui large header',
  h2: 'ui medium header',
  ul: 'ui list',
  li: 'ui item'
}

const bindings = Object.keys(classMap)
  .map(key => ({
    type: 'output',
    regex: new RegExp(`<${key}>`, 'g'),
    replace: `<${key} class="${classMap[key]}">`
  }));

const conv = new showdown.Converter({
  extensions: [...bindings],
  noHeaderId: true // important to add this, else regex match doesn't work
});

const text = `
# 1st Heading
## 2nd Heading

- first item
- second item
`;
```

This would output something like this:

```html
​​​​​<h1 class="ui large header">1st Heading</h1>​​​​​
​​​​​<h2 class="ui medium header">2nd Heading</h2>​​​​​
​​​​​<ul class="ui list">​​​​​
​​​​​<li class="ui item">first item</li>​​​​​
​​​​​<li class="ui item">second item</li>​​​​​
​​​​​</ul>​​​​​
```




---
Credits for this extension go to [@zusamann](https://github.com/zusamann) (original issue can be [consulted here](https://github.com/showdownjs/showdown/issues/376)). Kudos for his contribution!
