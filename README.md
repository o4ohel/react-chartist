react-chartist
==============

[![NPM version][npm-image]][npm-url]
[![Downloads][downloads-image]][downloads-url]


React component for [Chartist.js](https://gionkunz.github.io/chartist-js/)

### Installation

```
$ npm install react-chartist --save
```
Chartist is a peer dependency to react chartist. You need to install it if you do not have it installed already.

```
$ npm install chartist --save
```

### Usage

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import ChartistGraph from 'react-chartist';

class Pie extends React.Component {
  render() {

    var data = {
      labels: ['W1', 'W2', 'W3', 'W4', 'W5', 'W6', 'W7', 'W8', 'W9', 'W10'],
      series: [
        [1, 2, 4, 8, 6, -2, -1, -4, -6, -2]
      ]
    };

    var options = {
      high: 10,
      low: -10,
      axisX: {
        labelInterpolationFnc: function(value, index) {
          return index % 2 === 0 ? value : null;
        }
      }
    };
    
    // Example of registering an handler to the 'draw' event
    var listener = {
      draw: (data) => {
        if (data.type === "point") {
          data.element.replace(new Chartist.Svg('image', {
            height: 32,
            width: 32,
            x: data.x - (32 / 2),
            y: data.y - (32 / 2),
            "xlink:href": 'http://icons.iconarchive.com/icons/ergosign/free-spring/32/strawberry-icon.png'
          }));
        }
      }
    };

    var type = 'Bar'

    return (
      <div>
        <ChartistGraph data={data} options={options} type={type} listener={listener} />
      </div>
    )
  }
}

ReactDOM.render(<Pie />, document.body)

```

### Properties

Please check out [Chartist.js API documentation](http://gionkunz.github.io/chartist-js/api-documentation.html) for more details of the options.

* data - chart data (required)
* type - chart type (required)
* style - inline css styles (optional)
* options - chart options (optional)
* responsive-options - chart responsive options (optional)
* listener - An object used to register event handlers (optional)

To add support for aspect ratio

```HTML
<ChartistGraph className={'ct-octave'} data={data} options={options} type={type} />
```

### Note

This module does not include the css files for Chartist. If you want to add it, include their CDN in your html file

```HTML
<link rel="stylesheet" href="//cdn.jsdelivr.net/chartist.js/latest/chartist.min.css">
<script src="//cdn.jsdelivr.net/chartist.js/latest/chartist.min.js"></script>
```

Or use `bower` or `npm` to install Chartist and include it in your build process.

```
$ npm install chartist
```

Or

```
$ bower install chartist
```

### Development

```
$ npm install
```

To build run `npm run build`

### Changelog

If you want to support react version under v0.13, use `npm install react-chartist@0.9.0`

### License

MIT

[npm-image]: https://img.shields.io/npm/v/react-chartist.svg?style=flat-square
[npm-url]: https://npmjs.org/package/react-chartist
[downloads-image]: http://img.shields.io/npm/dm/react-chartist.svg?style=flat-square
[downloads-url]: https://npmjs.org/package/react-chartist
