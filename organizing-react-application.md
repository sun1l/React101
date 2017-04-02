# How to organize React application?

Whevnever starting a new React project, one question always arise - How do I strcuture my React application?

This is my (opinionated) high level thought process on how we should approach application and component structure. Though I am calling it 'React', it can be used for any library/framework which is component driven.

## Application Anatomy

```
|---- README.md
|---- package.json
|---- <dot-files> e.g. .gitignore, .npmrc, .babelrc
|
+---- src
|       components
|           Heading
|           Carousal
|           ...
|       config
|
+---- build
|       grunt
|       <build-scripts>
|
+---- public
|       index.html
|
+---- dist
|       bundle.js
|       bundle.css
```

This structure works fine for smaller project, but if you are building a complex application, it is good idea to start structuring your component folder based on the templates/pages/screen - whatever you want to call it.

```
src
|
+---- components
|       HomePage
|         Hero
|           index.js  
|
|       ProductDetail
|         AddToCart
|           index.js
|
|       shared
|         Header
|           index.js
```


## Component Anatomy

React is a view library which is built with component driven development in mind. With the ability to create highly nested structure without worring about performance, it allows developer to easily adopt patterns like Atomic.

The best way to think about component is to treat it like an isolated unit, where each component encapsulate the behaviour as well as presentation aspects, including dependencies, test cases and documentation. For e.g. a NPM module, as a developer I should be able to publish it as NPM module and a component should simply work.

```
<component-name>
|---- index.js
|---- README.md
|---- package.json
|
+---- assets
|       sprite.svg
|
+---- data
|       data.json
|
+---- style
|       icon.scss
|       index.css
|
+---- test
|       <component-name>.spec.js
```

Few things to note:
* `<component-name>` should use PascalCase
* Component root `.js` file should be `index.js` instead of `<component-name.js>`, it allow for easy imports without specifying the filenames. For e.g.

```
// you can do
import Heading from './components/Heading';

// otherwise if you use component name, you have to

import Heading from './components/Heading/Heading.js';
```