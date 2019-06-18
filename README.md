# is this true ?

> !!! WORK IN PROGRESS !!!

These last years i've read a lot of arguments against Node.js and JavaScript. In this article I will try to navigate through these different reviews and answer them **honestly**.

Most criticism was often wrong (technically distorted or no longer relevant). Not to mention people who simply **hate** JavaScript with no real technical reason...

The article does not aim to defend JavaScript (ECMAScript) against other languages/runtime.. Sometimes you have to know how to choose the right language according to your project needs.

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

<center>
    <img src="https://media.giphy.com/media/104c5NA7rLnCs8/giphy.gif">
</center>

## JavaScript is not Object Oriented.
JavaScript always supported the OOP with **prototypes** (The whole language has been designed with these). Most developers often tend to think that OOP is just about `class` keyword and nothing else (widely spread by `JAVA`, `C++`, `C#` etc...). Do not misunderstand me, i do not launch any attack against these languages !

The problem is very common within the community, a lot of TypeScript developers trully beleve that JavaScript is not object oriented... This can surely be explained by the difficulty of understanding prototypes and how things work behind the hood.

Fortunately things tend to improve with modern JavaScript.

The bad kid will surely try to get back into the subject with the lack of **'Encapsulation'**.. But sorry we are in 2019 and modern JavaScript bring encapsulation.

> Note: There is no question of debating whether we have to replace object-oriented programming with functional one!

Sources/Articles:
- [JavaScript Objects Introduction](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects)
- [Learn prototypes from MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [New ECMAScript6 OOP features](http://2ality.com/2014/12/es6-oop.html)
- [JavaScript inheritance](http://2ality.com/2012/01/js-inheritance-by-example.html)

## JavaScript is a `scripting` language.
Arggg...... my heart ! This one is terrible because haters often use it to trash talk ...

Yes, JavaScript was originally designed for the web in 10 days. Since ECMAScript 6, the specification describe the language as **A general purpose, cross-platform programming language**.

JavaScript is nowadays used across platforms (Cloud, Back-end, IoT, Robotics). So the language have to evolve to answer these platforms needs !

Sources/Articles:
- [ECMAScript Specification](https://www.ecma-international.org/publications/standards/Ecma-262.htm)
- [JavaScript 2018 - Blog NPM](https://blog.npmjs.org/post/180868064080/this-year-in-javascript-2018-in-review-and-npms)
- [Node.js EVERYWHERE](https://www.youtube.com/watch?v=NdISMdSDIaw)

## JavaScript is hard to learn because of Asynchronous
JavaScript is **SYNCHRONOUS** ! These are mainly beginners who mix concepts between them (Promise, Node.js event-loop etc..). This is terrible because beginners suddenly start to believe that it is possible to launch code in parralel:

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

These examples are very often used to explain Promises A/+ which is unfortunately the opposite of a good practice within an event loop.

Articles:
- [How does javascript actually work](https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf)
- [What's happening inside Node.js ?](https://www.youtube.com/watch?v=C8dwQw7M8Pk)

## JavaScript is weakly typed.
<center>
    <img src="https://media.giphy.com/media/26ufaJh2hfUtuSo6s/giphy.gif">
</center>

So many developers use this argument without being able to explain what is a "**strongly typed language**" (often the same who think that makes Javascript "**slow**" 🙉). Nowadays, **for me** types are many things at one time:

- Types annotations (for development/debug purpose).
- Memory management.
- Runtime safety (comes often with an [AOT](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) Compiler).

The question is: can we achieve that in (**modern**) JavaScript ? **YES SURE** !

### Types annotations
Types annotations are possible in JavaScript with Flow and/or TypeScript. And with a modern editor (like VSCode) you can achieve the same in pure JavaScript with TypeScript definition files and/or JSDoc.

Example of a pure JavaScript code:

![](https://cdn.discordapp.com/attachments/157206345949511680/462556289302790154/add.PNG)

### Memory management
Modern JavaScript bring `TypedArray`, `ArrayBuffer` and even `SharedArrayBuffer` to allocate a given amount of bytes on RAM. (Note: Engines are free to implement what they want).

Managing memory is a task that requires a high amount of rigor. Writing random types will never optimize the memory consumption of a program.

In a near future, WebAssembly and new ECMAScript features will surely bring **even more control on memory**.

Sources:
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Typed_arrays
- https://github.com/tc39/proposal-weakrefs (stage 3)

### Runtime safety
Runtime safety is the ability for a program to throw "types" errors at compilation (with an AOT Compiler). JavaScript run with a JIT (Just in time) compiler, so this kind of security can't be achieved in the language itself.

> ⚠️ However there is more and more work to implement new collection that bring more safety at the runtime.

But nothing stop you from doing the exact same things with TypeScript (errors will be throw at Compilation too).

---

Many people greatly underestimate the optimizations made by the modern virtual machine, take a look at these:

- [V8 TurboFan documentation](https://v8.dev/docs/turbofan)
- [V8 Elements Kinds](https://v8.dev/blog/elements-kinds)

## JavaScript ecosystem isn't mature and reliable.
This one has been surely introduced by the arrival of [NPM](https://www.npmjs.com/). JavaScript have a massive community and a big ecosystem (1,000,000+ packages on npm) with a lot of goods packages but also with a lot of **bad** designed packages (or packages that only contains one or two lines with no real interest).

Most of the problems we have come mostly from:
- Very low entry barrier (**which is very positive**).
- ECMAScript never break.. your code will still work in twenty years (everyone seems to forget but it create a lot of problems on how we deal with the language design).
- Lack of STD (Proposals in progress: https://github.com/tc39/proposal-javascript-standard-library)

But dear good... You'r free to choose and use a package or not. Some packages are created with simplicity in mind, others with more complicated layers (they surely score higher on performance & security checks .. but with an accessibility cost). People are just trash talking a whole ecosystem because of "few" packages.

I met someone who told me that copy/paste code was better.. 😬

## V8 Engine is not a "mature" Virtual Machine.
