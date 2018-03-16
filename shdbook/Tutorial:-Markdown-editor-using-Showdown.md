## Introduction

In this tutorial we will create a simple browser markdown editor using showdown and some of its extensions. The purpose is to show how easy it is to include and configure showdown in your project.

You can see the working fiddle example [**here**][1]

## Preparation

Showdown core library doesn't have any dependencies so the setup is pretty straightfoward. However, we strongly encourage people to use a package manager such as [**bower**](http://bower.io/) or [](http://npmjs.com) to manage project dependencies.


Create a directory called `showdown-editor` and recreate the following file structure:
```
showdown-editor
├── index.html
├── bower.json
├── js
│   ├── script.js
├── css
│   ├── style.css
```

Then initialize `bower.json` file by running the interactive console command:
```bash
bower init
```
You can press enter to accept defaults or fill the information properly, if you wish.

## Installing showdown

To install showdown, run the following command (inside showdown-editor directory):
```bash
bower install showdown --save
```
This installs showdown inside the `bower_components` directory and save showdown as a dependency in the `bower.json` file.

## index.html

Start by creating a basic html5 html file:

```html
<!DOCTYPE HTML>
<html>
<head>
  <meta charset="UTF-8"/>
  <link rel="stylesheet" href="css/style.css"/>
</head>
<body>

  <textarea id="sourceTA" rows="10" cols="82"></textarea>
  <hr/>
  <button id="runBtn" onClick="run()">Convert</button>
  <hr/>
  <div id="targetDiv"></div>

</body>
</html>
```

We now include showdown.js and our script.js in index.html file, just before the closing `</body>` tag:
```html
<script src="bower_components/showdown/1.0.1/showdown.min.js"></script>
<script src="js/script.js"></script>
```

(note: in this tutorial we are using v 1.0.1. Change this to match the actual installed version.)

## style.css
```css
#sourceTA {
    display: block;
}
#targetDiv {
  border: 1px dashed #333333;
  width: 600px;
  height: 400px;
}
```

## script.js

Now add the following content to `js/script.js`:

```js
function run() {
  var text = document.getElementById('sourceTA').value,
      target = document.getElementById('targetDiv'),
      converter = new showdown.Converter(),
      html = converter.makeHtml(text);
    
    target.innerHTML = html;
}
```

The `script.js` file is pretty straighforward. When the `runBtn` button is clicked, it gets the text of the textarea, passes it through showdown that converts the markdown into html. The output is then put inside the div (replacing the previous content).



[1]: http://jsfiddle.net/tivie/6bnpptkb/
[3]: https://github.com/showdownjs/showdown/releases