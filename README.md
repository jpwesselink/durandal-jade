Jade-Durando proof of concept
========

### What it is ###

A simple [Jade](https://github.com/visionmedia/jade) view engine for [Durandal](https://github.com/BlueSpire/Durandal) framework.
It simply renders jade source into html, which is in turn passed to the regular Durandal view locator. 

### What it's not ###

Since it just providers an extra layer on top of the regular view engine, viewmodel template variables are not available in the jade template scope for rendering, however, you can use good old `data-bind` just like you would in regular html templates.

``` 
ul(data-bind="foreach: listOfStuff")
  li
    span(data-bind="text: $data")
```

### How it works ###

1. Add [jade](https://github.com/visionmedia/jade/blob/0.35.0/jade.js) to Requirejs' path config.
2. Tell Requirejs to load `jadeViewEngine` instead of the default `viewEngine`
3. Write Jade, be happy.

```
requirejs.config({
    paths: {
        'text': '../lib/require/text',
        'durandal':'../lib/durandal/js',
        'plugins' : '../lib/durandal/js/plugins',
        'transitions' : '../lib/durandal/js/transitions',
        'knockout': '../lib/knockout/knockout-2.3.0',
        'bootstrap': '../lib/bootstrap/js/bootstrap',
        'jquery': '../lib/jquery/jquery-1.9.1',
        'jade': ['https://rawgithub.com/visionmedia/jade/0.35.0', '../lib/jade'],
        'durandal/viewEngine': '../lib/durandal/js/jadeViewEngine'
    },
    shim: {
        'bootstrap': {
            deps: ['jquery'],
            exports: 'jQuery'
       }
    }
});
```

### Demo ###

Take a look [here](http://jpwesselink.github.io/durandal-jade), put it on a web server of your own or run one quickly by using [a simple web server](https://github.com/nodeapps/http-server)
