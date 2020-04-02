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
JavaScript always supported the OOP with **prototypes** (The whole language has been designed with these). Most developers often tend to think that **OOP** is just about `class` or similar **wide-spread inherance patterns** (like `JAVA`, `C++`, `C#` etc...).

The problem is very common within the community, a lot of TypeScript developers trully beleve that JavaScript is not object oriented... This can surely be explained by the difficulty of understanding prototypes and how things work behind the hood.

Fortunately things tend to improve with modern JavaScript.

Even the definition of OOP is not clear either by the way.. I guess everyone should read this: [proposal for Simplified, Modern Definitions of "Object" and "Object Oriented"](https://wcook.blogspot.com/2012/07/proposal-for-simplified-modern.html).

> Note: My goal here was not debating whether we have to use OOP or ADT...

Sources/Articles:
- [On Understanding Data Abstraction, Revisited](http://www.cs.utexas.edu/~wcook/Drafts/2009/essay.pdf)
- [Programming Paradigms for Dummies: What Every Programmer Should Know](https://www.info.ucl.ac.be/~pvr/VanRoyChapter.pdf)
- [JavaScript Objects Introduction](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects)
- [Learn prototypes from MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [New ECMAScript6 OOP features](http://2ality.com/2014/12/es6-oop.html)
- [JavaScript inheritance](http://2ality.com/2012/01/js-inheritance-by-example.html)

## JavaScript is a `scripting` language.
Arggg...... my heart ! This one is terrible because haters often use it to trash talk...

Yes, JavaScript was originally designed for the web in 10 days. Since ECMAScript 6, the specification describe the language as **A general purpose, cross-platform programming language**.

JavaScript is nowadays used across platforms (Cloud, Back-end, IoT, Robotics). So the language have to evolve to answer these platforms needs!

Sources/Articles:
- [JavaScript: The First 20 Years](https://zenodo.org/record/3710954#.XoWSPogzaUk)
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
This one has been surely introduced by the arrival of [NPM](https://www.npmjs.com/). JavaScript have a massive community and a big ecosystem (**1,000,000+ packages on npm**) with a lot of goods packages but also with a lot of **bad** designed packages (or packages that only contains one or two lines with no real interest). There is no community where everything is white or black so please **stay respectful** (and it's the same for javascript developers).

> Note: This does not mean that there is no point in making a package even for a need that takes two lines (example: [flatstr](https://github.com/davidmarkclements/flatstr)).

However you'r free to choose and use a package or not. Some packages are created with simplicity in mind, others with more complicated layers (they surely score higher on performance & security checks .. but with an accessibility cost). People are just trash talking a whole ecosystem because of "**few**" packages.

Note that it is often not possible to compare ecosystems with each other because they are not comparable:
- We have very low entry barrier (**which is very positive**).
- ECMAScript never break. Your code will still work in twenty years (everyone seems to forget about this.. but it create a lot of problems on how we deal with the language day to day).
- Lack of STD (Proposals in progress: https://github.com/tc39/proposal-javascript-standard-library)

## V8 Engine is not a "mature" Virtual Machine.

It's a much rarer criticism but i've already met him a few times. To begin, you must know that V8 engine [has celebrated its ten years](https://v8.dev/blog/10-years) recently.

**Compiler** and **Virtual Machine** are complicated projects that evolve every day. Of course we have mastered some optimization patterns since 10/20 years (or even more) but this does not mean that nothing remains to be optimized ! (Look JAVA with [GraalVM](https://www.graalvm.org/)).

V8 Engine is nowadays one of the most powerful JIT... So what do you mean by "**matury**" ?.

<p align="center">source: https://blog.cloudflare.com/cloudflare-workers-unleashed/<p>
<p align="center">
    <img src="./images/cloudflare.png">
</p>

## Node.js runtime is not configurable as JAVA EE (example).
