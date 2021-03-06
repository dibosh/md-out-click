![mdOutClick Logo](https://raw.githubusercontent.com/dibosh/md-out-click/master/readme-logo.jpg)

[![Build Status](https://travis-ci.org/dibosh/md-out-click.svg?branch=master)](https://travis-ci.org/dibosh/md-out-click)
[![npm version](https://badge.fury.io/js/md-out-click.svg)](https://badge.fury.io/js/md-out-click)
[![codecov](https://codecov.io/gh/dibosh/md-out-click/branch/master/graph/badge.svg)](https://codecov.io/gh/dibosh/md-out-click)
[![all downloads](https://img.shields.io/npm/dt/md-out-click.svg)]()

[mdOutClick](https://dibosh.github.io/md-out-click) is an AngularJS module, having a directive `on-out-click` 
and a service `OutClickService`; which enables you to capture click events outside of an element and fire handlers 
based on that.

Example- `<button ng-click="doSomething()" on-out-click="doSomethingElse()"></button`

### Installation
- `npm install md-out-click`
- **Webpack**:
  1. Import the module in your `index.js` or `entry.js` file, import the module
  right after where you imported `angular`
    - `import mdOutClick from 'mdOutClick'` (ES6)
    - `require('mdOutClick')` (ES5)
    
  2. Where you define your angular app, include `mdOutClick` as dependency.
 
  ```
  angular.module('yourApp', [
     ...
     // other dependencies
     ...
     'mdOutClick'
  ]);
  ```   
    
- **Legacy Way**:

  1. Include the `md.out.click.min.js` file as script tag in between angular source
  and your app specific script files.
  
  ```
    ...
    <script src="node_modules/angular/angular.min.js"></script>
    <script src="node_modules/md-out-click/dist/md.out.click.min.js"></script>
    <script src="app/app.index.js"></script>
    <script src="app/controllers/index.js"></script>
    ...
  </body>
  ```
  
  2. In your `index.js` or `script.js` file where you define your angular app,
  include `mdOutClick` as dependency.
  
  ```
  angular.module('yourApp', [
     ...
     // other dependencies
     ...
     'mdOutClick'
  ]);
  ```

### Usage
Define a handler or action on `on-out-click` attribute of an element. The handler
can be any valid Javascript expression.
   ```
   <aside class="sidenav" ng-class="{'open': isSideNavOpen}" on-out-click="closeSideNav()"></aside>
   ```
Or, this is also do-able-
   ```
   <aside class="sidenav" ng-class="{'open': isSideNavOpen}" on-out-click="isSideNavOpen = false"></aside>
   ```
Using the `OutClickService`, you can apply different handlers for different `element` at the same time-

  ```
  // needs jquery support to get element like this
  var elem1 = $document.find('#e1');
  var elem2 = $document.find('#e2');
  
  OutClickService.register(elem1, function () {
    // do something when click is outside elem1
  });
  
  OutClickService.register(elem2, function () {
    // do something when click is outside elem2
  });
  
  ```

To learn more, check out the examples at - https://dibosh.github.io/md-out-click

### The MIT License

Copyright 2018 Munim Dibosh

Permission is hereby granted, free of charge, to any person obtaining a copy of this 
software and associated documentation files (the "Software"), to deal in the Software 
without restriction, including without limitation the rights to use, copy, modify, 
merge, publish, distribute, sublicense, and/or sell copies of the Software, and to 
permit persons to whom the Software is furnished to do so, subject to the following 
conditions:

The above copyright notice and this permission notice shall be included in all copies 
or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, 
INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A 
PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT 
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF 
CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE 
OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
