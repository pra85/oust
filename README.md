oust
====

> Extract a list of stylesheets, scripts or HTML imports from HTML

### Install

```
npm install oust --save-dev
```

### Usage

First include:

```
var oust = require('oust');
```

Resource links can then be extracted from either files:

#### Extract stylesheets references `<link rel="stylesheet">`

```
oust({ src: 'test/sample/index.html' } , function ( links ){
	console.log(links);
});
```

#### Extract script references `<script src>`

```
oust({ 
	src: 'test/sample/index.html', 
	selector: 'script', 
	attribute: 'src'
	}, function (links){
		console.log(links);
	});
```

#### Extract HTML imports `<link rel="import">`

```
oust({ 
	src: 'test/imports.html', 
	selector: 'link[rel="import"]', 
	attribute: 'href' 
	}, function (links){
		console.log(links);
	});
```

#### Or from HTML string input:

```
oust({ 
	source: '<html><link rel="stylesheet" href="styles/main.css"></html>' 
	}, function (links){
	console.log(links);
	});
```

### API

#### Options

Attribute       | Default   | Description
---             | ---       | ---
`src`           | ``        | a valid path to the file you wish to parse
`source`        | ``        | a valid string to parse for references
`selector`      | `link[rel="stylesheet"]`        | a selector to query for
`attribute`        | `href`        | an attribute to read from the selector query

The second parameter to `oust()` is a callback function which will include the array of resources discovered.

### License

Released under an Apache 2 license. Copyright Google 2014.