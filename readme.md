# Fabricator Controller Component

While this component is designed with the [BuzzingPixel Fabricator Build Process](https://github.com/tjdraper/buzzing-pixel-fabricator) in mind, it can be used anywhere (in theory).

A Fabricator Controller is a way to describe a set of functions and conveniences for making constructors.

## Installing

With Fabricator and NPM, simply require this library into your project and restart the Fabricator Grunt build process.

`npm install fab.controller --save`

If you are not using Fabricator, you will need to in some manner compile `src/FAB.controller.js` into your build process or put it somewhere where you can link it into your projects.

## `FAB.controller.make()`

Returns: constructor

Takes up to two arguments. If the first argument is a string, it acts as a name and the constructor will be stored for use later with `FAB.controller.construct('myConstructorname')`. The second argument takes an object (or the first argument if you only wish to return a constructor for immediate use and not store it for use with `FAB.controller.construct`).

### Object argument properties

#### `arg.init()`

If the `init` function is present, it will be run when using the `new` keyword, or `FAB.controller.construct`.

#### `arg.events`

`events` is an object of jQuery events to be set on the `$el`. You can space separate and add a selector for delegation within the `$el`.

#### `arg.model`

If you have the Fabricator Model component installed, you can either pass in a constructed model directly, or you can define an object of model properties and a new model will be created.

## The Constructor (returned from `FAB.controller.make()`)

The controller constructor takes an optional object as the first argument. Any arguments after the first are passed to the `init` function if `init` function exists. If you would like to pass arguments to `init` but not set an object for the first argument, use `null` or `false`

### Constructor Arguments

#### First argument: Object|False|Null

##### `arg.el`

`el` can be a jQuery selector or a jQuery object. When set, your constructed objects `el` will be a DOMObject, and `$el` will be set to the jQuery object. If no `el` argument is provided, an empty `div` element will be set.

##### `arg.model`

If you have the Fabricator Model component installed, you can either pass in a model directory, or you can define an object of model properties and a new model will be created.

##### Other properties

Any other properties you set will be set directly on your constructed object.

## `FAB.controller.construct('MyConstructor')`

If you have use `F.controller.make` and passed a string as the first argument to name a constructor, it has been stored for later use. You use `FAB.controller.construct('MyConstructor')` to run that stored constructor.

### `FAB.controller.construct` arguments

#### `'MyConstructor'`

The name of the constructor to construct.

#### `object`

The constructor object argument you would like to pass along (see above).

#### Additional arguments

Any additional arguments are passed to the `init` function if `init` function exists.

## License

Copyright 2017 TJ Draper, BuzzingPixel, LLC

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
