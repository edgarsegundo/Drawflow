# How to bundle

nvm install lts/iron
nvm use lts/iron

npm install

Create a file `.babelrc` and with this:

```json
{
    "presets": ["@babel/preset-env"]
}
```

Install watchify and others

```zsh
npm install watchify browserify babelify @babel/core @babel/preset-env
```

Create file index.js and with following content:

```js
// index.js
import Drawflow from './Drawflow'; // adjust the path if needed
window.Drawflow = Drawflow; // Expose Drawflow globally
```

Open the `index.html` file and replace the whole <script></script> content with this:

```html
  <script src="bundle.js"></script>
  <script src="editor.js"></script>
```

Still in `index.html`, comment or remove the line:

```html
<script src="drawflow.min.js"></script>
```

Copy the file `editor.js` to the project root folder

```zsh
watchify src/index.js -o bundle.js -v -t [ babelify --presets [ @babel/preset-env ] ]
```

Use "Go Live" to run `index.html`—and voilà!
