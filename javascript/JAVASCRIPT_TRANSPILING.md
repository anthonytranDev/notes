# JavaScript Transpiling

**Created:** 2020-08-21T10:27:10Z
**Last Updated:** 2020-08-21T10:27:10Z

Note during the time of including these notes. Babel 7 is current transpiler is being used, with Babel 8 a work-in-progress, checkout [Babel 8 Milestones](https://github.com/babel/babel/milestone/16)

## Babel Setup Page

https://babeljs.io/en/setup

## TypeScript vs Babel Transpiling

The TypeScript compiler has a similar feature, enabled by setting target to something like ES5 or ES6. But the Babel configuration improves on this with [babel-preset-env](https://babeljs.io/docs/en/babel-preset-env/). Instead of locking in a specific set of JavaScript features (ES5, ES6, etc), you list the environments you need to support:

Babel uses [compat-table](https://kangax.github.io/compat-table/es6/) to check which JavaScript features to convert and polyfill for those specific target environments.

## Babel 7 working with TypeScript
How does Babel handle TypeScript code? It removes it.

Yep, it strips out all the TypeScript, turns it into “regular” JavaScript, and continues on its merry way.

### Advantages: It's Lightning Fast
However the Babel + TypeScript combo still provides faster compilation thanks to Babel’s superior caching and single-file emit architecture.

## Babel 7 and Beyond

One JavaScript compiler to rule them all
Whether your code has 
- ES2015 features
- JSX
- TypeScript

### Before Babel 7

By allowing Babel to act as the single compiler, there’s no need to manage, configure, or merge two compilers with some convoluted Webpack sorcery.

Chaining together two separate compilers (TypeScript and Babel) is no easy feat. The compilation flow becomes: TS > TS Compiler > JS > Babel > JS (again).



## References

[compat-table](https://kangax.github.io/compat-table/es6/)
[babel-preset-env](https://babeljs.io/docs/en/babel-preset-env/)
[Babel Setup Page](https://babeljs.io/en/setup)
[TypeScript With Babel: A Beautiful Marriage](https://iamturns.com/TypeScript-babel/)