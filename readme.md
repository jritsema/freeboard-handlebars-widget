freeboard-handlebars-widget
============================

A starter template for building freeboard widgets using the [handlebars plugin](https://github.com/jritsema/freeboard-handlebars).

This gives you a nice development workflow by allowing you to implement your widget using files (view.html, model.js, helpers.js), saving your files, and then refreshing your browser to immediately see your changes (assuming you have script to have freeboard load your dashboard.json) or you can manually re-load your dashboard.

Includes predefined npm scripts for updating freeboard dashboard.json (using [freeboard-handlebars-buildtool](https://github.com/jritsema/freeboard-handlebars-buildtool)) when files are saved.

**setup**

```
$ git clone https://github.com/jritsema/freeboard-handlebars-widget mywidget
$ cd mywidget
$ npm install
```

**usage**

Edit the "build" script command in package.json to point to the dashboard.json file you want updated.  

```
"build": "cat ../freeboard/dashboard.json | freeboard-handlebars-buildtool > temp && cp temp ../freeboard/dashboard.json && rm temp",
```

Note that the target widget defined in dashboard.json needs to have a "title" property that matches the "name" property in package.json.  For example, if you update the name in package.json to "mywidget", then your dashboard.json needs to look like the following.

```
...
"widgets": [
  {
    "title": "mywidget",
    "type": "handlebarsWidget",
    "settings": {
      "height": 3,
      "model": "",
      "view": "",
      "helpers": ""
    }
  }
]
...
```

Now you're ready to edit your source files (view.html, model.js, helpers.js) and then...

`$ npm run build` or `$ npm run watch`

...and this will update your dashboard.json with the resulting model, view, and helpers properties.

