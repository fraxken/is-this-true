# is this true ?

> !!! WORK IN PROGRESS !!!

These last years i've read a lot of arguments against Node.js and JavaScript. In this article I will try to navigate through these different reviews and answer them **honestly**.

Most criticism was often wrong (technically distorted or no longer relevant). Not to mention people who simply **hate** JavaScript with no real technical reason...

The article does not aim to defend JavaScript (ECMAScript) against other languages/runtime etc..

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

The problem is very common within the community, a lot of TypeScript developer trully beleve that JavaScript is not object oriented... This can be explained by the difficulty of understanding prototypes.

Fortunately things tend to improve with modern JavaScript.

The bad kid will surely try to get back into the subject with the lack of **'Encapsulation'**.. But sorry we are in 2019 and ECMAScript now have a complete support !

Sources:
- [Learn prototypes from MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

## JavaScript is a `scripting` language.
Arggg...... my heart ! This one is terrible because haters often use it to trash talk:
> A "scripting" language designed for web (noob) developer!

Yes, JavaScript was originally designed for the web (And I think this is a force for today's back-end developers).

Since ECMAScript 6, the specification describe the language as **A general purpose, cross-platform programming language**. This explain why the language evolve these last years (to answers more production and enterprise use cases). Node.js surely played an important role in this.

We will see at the end of the article some incomplete parts of ECMAScript.

Sources:
- https://www.ecma-international.org/publications/standards/Ecma-262.htm

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

These examples are very often used to explain Promises A/+ which is unfortunately the opposite of a good practice within an event loop.

Articles:
- [How does javascript actually work](https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf)

## JavaScript is weakly typed.
<center>
    <img src="https://media.giphy.com/media/26ufaJh2hfUtuSo6s/giphy.gif">
</center>

The most beloved one... So many developers use this argument without being able to explain what is a "**strongly typed language**". Nowadays, for me types are many things at one time:

- Types annotations (for development/debug purpose).
- Memory management.
- Runtime safety (AOT Compiler).

The question is: can we achieve that in (**modern**) JavaScript ? **YES** !

### Types annotations
Types annotations are possible in JavaScript with Flow and/or TypeScript. And with a modern editor (like VSCode) you can achieve the same in pure JavaScript with TypeScript definition files and/or JSDoc.

Example of a pure JavaScript code:

![](https://cdn.discordapp.com/attachments/157206345949511680/462556289302790154/add.PNG)

### Memory management
Modern JavaScript bring `TypedArray`, `ArrayBuffer` and even `SharedArrayBuffer` to allocate a given amount of bytes on RAM. (Note: Engines are free to implement what they want).

Managing memory is a task that requires a high amount of rigor. Writing random types will never optimize the memory consumption of a program.

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Typed_arrays

### Runtime safety
Runtime safety is the ability for a program to throw "types" errors at compilation (with an AOT Compiler). JavaScript run with a JIT (Just in time) compiler, so this kind of security can't be achieved in the language itself.

But nothing stop you from doing the exact same things with a strict TypeScript (errors will be throw at Compilation too).

## JavaScript ecosystem isn't mature and reliable.