# is this true ?

> !!! WORK IN PROGRESS !!!

These last years i've read a lot of arguments against Node.js and JavaScript. In this article I will try to navigate through these different reviews and answer them honestly.

Most criticism was often wrong (technically distorted or no longer relevant). Not to mention people who simply **hate** JavaScript with no real technical reason...

Let's start with the list below:

- JavaScript is not Object Oriented.
- JavaScript is a "scripting" language.
- JavaScript is hard to learn because of Asynchronous (?!).
- JavaScript is weakly typed.
- JavaScript ecosystem isn't mature and reliable.
- V8 Engine is not a "mature" Virtual Machine.
- Node.js runtime is not configurable as JAVA EE (example).
- Node.js have no thread support (Less efficient with CPU-intensive operations).
- Node.js is just a "hype".
- Node.js Asynchronous is hard to master.
- NPM is not secure.
- No serious IDE.
- Bad for long-term projects

These are the most popular arguments among **developers**. Note that there are very few critics of the gaps in the language itself (What I find today very surprising, i will back on it later).

![](https://media.giphy.com/media/104c5NA7rLnCs8/giphy.gif)

## JavaScript is not Object Oriented.
JavaScript always supported the OOP with **prototypes** (The whole language has been designed with prototypes). Nowadays most people often tend to think that OOP is just about `class` keyword and nothing else (widely spread by `JAVA`, `C++`, `C#` etc...).

Nowadays, a lot of TypeScript developer trully beleve that JavaScript is not object oriented... This can be explained by the difficulty of understanding prototypes. Thing are getting better with modern JavaScript.

## JavaScript is a `scripting` language.
Arggg.. my heart ! This one is terrible because hater often use it to trash talk:
> Yeah.. JavaScript ? A "scripting" language designed for (web) noob developer!

Since ECMAScript 6, the specification describe the language as **A general purpose, cross-platform programming language**. This is why the language evolve these last years (to answers more production use cases).

## JavaScript is hard to learn because of Asynchronous
JavaScript is **SYNCHRONOUS** ! These are mainly beginners who mix concepts between them (Promise, Node.js event-loop etc..). This is terrible because beginners suddenly have a tendency to believe that it is possible to launch code in parralel:

```js
const result = await Promise.all([
    Promise.resolve(10 + 10),
    Promise.resolve(10 + 5)
]);
```
It's the worst thing possible (and it will achieve the same work as the code below).

```js
const result = [10 + 10, 10 + 5];
```

These examples are very often used to explain Promises A/+.

## JavaScript is weakly typed.
![](https://media.giphy.com/media/26ufaJh2hfUtuSo6s/giphy.gif)

The most beloved one... So many developers use this argument without being able to explain what is a "**strongly typed language**". Nowadays, for me types are about:

- Types annotations (for development/debug purpose).
- Memory management (control the consumption of bytes in / out).
- Safety before runtime (error during compilation).

Types annotations and Memory management can be achieved in modern JavaScript:
- with TypeScript/Flow (even in pure JavaScript with JSDoc and d.ts file).
- with TypedArray, ex: `new uint8Array([1, 2, 3])`

And the third is not possible because we run on `JIT` compiler. If you want these, just find the right language for the right need...
