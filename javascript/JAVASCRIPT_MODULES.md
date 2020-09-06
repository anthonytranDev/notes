# JavaScript Modules

**Created:** 2020-08-30T18:25:41Z
**Last Updated:**

## Deeper Diver into

- Modules
- Bundles
- Transpilation
- Code Splitting

## History of JavaScript usage

**Early 2000s - no module bundling**

- Common practice to write one main script for an entire website
- Dependencies were in separate files that had to load before the main script, e.g. jQuery (released in early 2006) for handling cross-browser differences
- There were quite a few problems with this approach, such as polluting the global scope, but it worked for the low complexity of web applications at the time.

**Mid 2000s - introducing modules**

- Developers needed a better way to build and maintain online software at scale
- Problems
  - As more and more features were required, the hassle of tracking and loading dependencies in the right order became too much of a burden
  - increasing complexity often resulted in features being frustratingly intermingled and scattered in code
- The solution—split your codebase into modules

**Early 2009 - CommonJS**

- Create a specification for loading modules in a specific format, in order into a file that could then be used by a browser. This requires a server which is capable of compiling JavaScript.
- Mulitple implementations of CommonJS, most notably Node.js

**Mid 2009 - Present**

- Node.js pioneered the CommonJS ethos, which became a central component of “universal” JavaScript.
- Node.js not only processes JavaScript, it runs it—empowering modules to be written in JavaScript with no extra setup.

**2011 - Server side JavaScript**

- By 2011 JavaScript had broken out of the browser and could be used as a server-side scripting language
- Entire applications were—and are—written in JavaScript, and share modules between client and server.

**JavaScript Modules Present**

- Today, Native Modules are a browser standard ES6 (ECMAScript 2015+). Including Node v13+
- Spanning the gap between ES5 and ES6 required to the use of a tool called "Transpilation". Basically enabling the use of ES6 code to be used in browsers that only supports ES5, rather than wait for the browser support to catch up, this is called "JavaScript Bundling"
- Most popular tool to use is "Webpack + Babel"

**Note:** ES5 and ES6 are the 5th and 6th edition of the ECMAScript standard - see https://en.wikipedia.org/wiki/ECMAScript, under Versions heading

## Modules - what are they?

[Encapsulated units of JavaScript linked by an export/import syntax](https://exploringjs.com/es6/ch_modules.html)

### Native Browser Modules Support

Use of native JavaScript modules is dependent on the import and export statements, with IE not supporting this ES6 feature. Please see https://caniuse.com/#feat=es6-module-dynamic-import for more details. With exports being very similar

## Module Bundling

Providing mechanisms for splitting JavaScript programs up into separate modules that can be imported when needed.

Modern JavaScript for web applications can now be thought of as a bundle of modules interacting with each other to create features. Dependencies are modules, too, which means they no longer need to be loaded individually before the main file can load.

### Minifying JavaScript and debugging with sourcemaps

**Minification** - to removes formatting, such as white-space or long variable names, which can reduce the file size down significantly - does not have to be human-readable

**Sourcemaps** - contain references to the lines in the original files, which means it’s possible to track bugs to the exact source. Bundler tools offer an option to create a sourcemap file at the time of minifying, which is co-located with your bundle.

## How does bundling relate to code splitting?

Since website loading time is a prime concern for users, it’s important to keep JavaScript bundles as small as possible.

Bundling will result in increasing the filesize, apart from the minified sourcecode, due to;

- Sourcemap(s) (required)
- Inclusion of dependencies
- Bundle is the main script file, which the browser loads through a script tag

One method for reducing bundle size is [code splitting](#code-splitting-to-create-multiple-scripts)

### Code splitting to create multiple scripts

The most common reason to have multiple scripts for a single application is to take advantage of browser caching

Bundles to cache;

- vendor bundle with dependencies that are unlikely to change, such as utility libraries for math or date calculations
- source code bundles that don't often change, i.e. the core of the app
- each page of a website
- bundles for each application that shares a codebase

That way even when the application changes a returning user won’t need to load the unchanged vendor bundle.

Modular JavaScript became standard and popular because it doesn’t require loading dependencies before the main script. The key difference is that these dependencies only include what the application is directly using.

Even better, all of the dependencies are managed by the bundler. This is how modular JavaScript shows its full power—reusable code that can be used consistently throughout the code base. Features can be developed once and work consistently between server and client.

### Tree shaking to help reduce bloat

> When a module is included the whole package gets added to the bundle, even if only a part of it is used

It can be difficult for bundlers to know if code has side effects, which means that the code has dependencies on variables within scope but not within the explicit export. Without being able to distinguish what is being used and what is dead code, bundlers include the entirety of modules.

This causes unnecessary additions to file size, this will mean the unused export is included in the bundle.

This is where **Tree Shaking** comes into play.

**Tree Shaking** - bundlers can eliminate unused exports and other dead code in a module. By telling Webpack what parts of the code have no side effects it can shake the dead code out of the “tree”, or bundle. Using ESM is the most effective way to enable tree-shaking

### Dynamic require and lazy-loaded modules

One of the main attractions of modern ECMAScript Modules is the ability to load modules as-needed. A rarely used part of an application can weigh down a bundle size unnecessarily for most users.

Instead, it’s possible to dynamically load a module later instead of including it in the bundle file.

On-demand, “lazy-load” of a module is part of the specification for ES6. The syntax follows different rules, since it relies on Promises: the module is conditionally loaded when the import function is called.

This means that the rarely used feature mentioned earlier is only referenced by the bundle and only loaded by the browser when a user accesses the feature, hence the on-demand nature of dynamic imports.

### Summary

The below is all handlered by bundlers

- **Codesplitting** - reduces the bundlesize, by initially caching bundles that do not change often or rarely. This enables upon small bundles that change often to be requested; takes advantage of browser caching
- **Tree Shaking** - elimates unused exports and other dead code modules. For instance webpack can told what parts of the code have no side effects. (ESM is the most effective way to enable tree-shaking)
  **Dynamic Require** - is part of the ES6 specification, where modules are on-demand/lazy loaded, via a Promise. Where they are conditionally loaded when the import function is called

## References

- [Exploring JS - Modules](https://exploringjs.com/es6/ch_modules.html)
- [CommonJS Wiki - Modules](http://wiki.commonjs.org/wiki/Modules)
- [Brief History of NodeJS | NodeJS](https://nodejs.dev/learn/a-brief-history-of-nodejs)
- [ECMAScript | Wikipedia](https://en.wikipedia.org/wiki/ECMAScript)
- [JavaScript Modules | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
- [JavaScript Modules and Code Bundling Explained](https://www.simplethread.com/javascript-modules-and-code-bundling-explained/)
- [Module Dynamic Import | Can I use](https://caniuse.com/#feat=es6-module-dynamic-import)
- [Tree Shaking | Webpack](https://webpack.js.org/guides/tree-shaking/)
- [Codesplitting | Webpack](https://webpack.js.org/guides/code-splitting/)
- [Lazy Loading | Webpack](https://webpack.js.org/guides/lazy-loading/)

## Other stuff

### CommonJS

### AMD

### RequireJS

### Webpack

### Rollup

### Babel
