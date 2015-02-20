title: Fearless JavaScript
output: index.html
theme: theme
controls: false
logo: theme/logo.png

-- title

# Fearless JavaScript

-- presenter

![Kevin Barabash](http://www.gravatar.com/avatar/de8cd250d9fe39b78f1c0f98b718670d.png?s=200)

## Kevin Barabash

* [<i class="fa fa-github"></i> kevinb7](https://github.com/kevinb7)

--

# Agenda

- JavaScript
- Tools
- Interacting with the Community
- APIs & libraries
- Final Words of Wisdom
- Questions

-- title

# JavaScript

--

# JavaScript

- Language
  - keywords: `if`, `for`, `var`, `function`, etc; operators: `+`, `&&`, `===`, `!==`, etc.
- Standard Library
  - String, Array, Function, RegExp, Date, Object, Math, setTimeout, etc.
- DOM
- 3rd party libraries

--

# Learn the Language First

Why?
- solid foundation to build on
- easier to understand other code you're using
- easier to find bugs and fix them

--

# Learn the Language First

What?
- `this`
- closure (lambdas)
- pass-by-reference vs. pass-by-value
- prototype chain
- function scope
- type coercion
- automatic semicolon insertion

--

# JavaScript the Good Parts

<iframe width="640" height="480" src="https://www.youtube.com/embed/hQVTIJBZook?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

--

# Other Resources

- [JavaScript Garden](https://bonsaiden.github.io/JavaScript-Garden/)
- [JavaScript on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [JavaScript the Weird Parts](https://www.youtube.com/watch?v=MihuqHhnFVo)

--

# How to make it stick

- Don't just read it, try it out as you read it
- If you forget it, try writing some code to verify it
- write code
- read other people's code
- modify other people's code

--

# REPL uses

- validate understanding
- explore objects
- experiment

--

# REPL tips

- be careful, browser dev tools will eat "var a = ...", use "a = ..."
- hit shift-enter to type multiple lines of code

--

# Example (value of "this")

- [MDN this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)
- [How "this" works (JavaScript Garden)](https://bonsaiden.github.io/JavaScript-Garden/#function.this)

--

# Simplifying Mental Models

- long blog post enumerate every single way in which "this" can be used (bad)
- bounds vs. unbound (good)

--

# Bound vs. unbound

- new -> bound
- calling a method via dot syntax -> bound
- binding a "this" object via .bind -> bound
- using .call or .apply with a "this" object -> bound

Everything else is unbound and "this" will be window (or global in node.js)

--

# Example: bind, call, apply

- [bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
- [call](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)
- [apply](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

--

# Closure

    for (var i = 0; i < 5; i++) {
        button.onclick = function() {
            alert("I'm button #" + i);
        }
    }
    
- The onclick handler uses whatever the value of `i` when the event handler is 
called.  
- When is onclick called?  During the `for` loop or after?
- What is the value of `i` at that point in time?
- What does this program do?

--

# Closure

    var createHandler = function(i) {
        return function () {
            alert("I'm button #" + i);
        };
    };
    
    for (var i = 0; i < 5; i++) {
        button.onclick = createHandler(i);
    }

Why does this make a difference?

--

# Example: exploring prototype

Let's look at how to add a method to `Array`

- Object.getPrototype
- Object.getOwnPropertyDescriptor
- Object.defineProperty
- [ECMAScript 5 Objects and Properties](http://ejohn.org/blog/ecmascript-5-objects-and-properties/)

--

# Replacing methods

- polyfills (add mising functionality)
- instrumenting
- mocking/stubbing when testing

-- 

# Example: addEventListener

instrument a single instance, class, or everythhing

pattern:
- store the original implementation
- create our own method that calls the original and does some other worker


    Element.prototype.addEventListener = function(type, handler, capture) {
        console.log("adding event '" + type + "' to: %o", this);
        aEL.call(this, type, handler, capture);
    };
 
-- title

# Tooling

--

# Tools

- IDE/Editor: WebStorm, Sublime, Atom, emacs, vim, etc.
- dependency management: npm, bower, jspm
- module loading: requirejs, systemjs
- build system: grunt, gulp, browserify, webpack, etc.
- Browser Dev Tools: debugging, profiling, etc.

-- 

# IDE/Editor

- easy navigation
- collapsable regions -> structure
- refactorings
- multiple cursors
- keyboard shortcuts

--

# Protect Yourself

- lint: jshint (automate it)
- write tests, automate tests (travis-ci)
- source control: git, hg, svn, etc.
- externalize storage: github, bitbucket

--

# Debugging

- breakpoints
- exceptions
- conditional breakpoints
- [https://developer.chrome.com/devtools](https://developer.chrome.com/devtools)
- [http://discover-devtools.codeschool.com/](http://discover-devtools.codeschool.com/)
- videos from previous Google I/O on devtools

-- title

# Interacting with the Community

--

# Things to do

- report bugs
- verify bugs
- suggest features
- fix documentation
- fix bugs (and write tests)
- add features

--

# Etiquette

- assume good faith
- observe proper netiquette
- try to make your code fit it
- don't try to change everything

--

# Finding a Project

- https://github.com/gre/glsl.js/pull/12
- https://github.com/WebAudio/web-audio-api/pull/339
- https://github.com/Khan/live-editor/pull/188/files

--

# Starting a Project

- http://jenniferdewalt.com/
- write some functions to make something easier -> library
  - generate random colors - [npmjs.org search](https://www.npmjs.com/search?q=random+color)
  - drawing circles and lines using HTML5 Canvas
  - something to make postMessage look like an EventEmitter - [poster](https://github.com/kevinb7/poster)

--

# Finishing a Project

- add documentation and example code to README.md
- put a live demo on gh-pages (free static hosting)
- write a "Show HN" post

-- title

# APIs and Libraries

--

# Browser APIs

- [dive into HTML5](http://diveintohtml5.info/)
- [http://html5please.com/](http://html5please.com/)
- Blobs, BlobURLs, native drag and drop, native notifications, dialog element,
  web workers, WebGL, SVG, Canvas, localStorage, audio/video elements, 
  getUserMedia, TouchEvents, DeviceOrientation, etc.
- [MDN](https://developer.mozilla.org/en-US/)

--

# Using the new and shiny

- [caniuse.com](http://caniuse.com/)
- use polyfills when necessary

--

# Libraries

- Web Sockets -> [socket.io](http://socket.io/)
- WebRTC -> [rtc.io](http://rtc.io/)
- WebGL -> [THREE.js](http://threejs.org/)
- Web Components -> [Polymer](https://www.polymer-project.org/)

-- title

# Final Words of Wisdom

--

# JavaScript Masterclass

<iframe width="853" height="480" src="https://www.youtube.com/embed/v0TFmdO4ZP0?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

-- title

# Questions
