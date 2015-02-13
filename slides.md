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
- Browser APIs
- Interacting with the Community

--

# JavaScript

Language, Standard Library, DOM, jQuery, Backbone, etc.

--

# Learn the Language First

- this
- closure
- pass-by-reference vs. pass-by-value
- prototype chain
- function scope
- type coercion
- automatic semicolon insertion

--

# What's the value of "this"?

    function Foo() {
        console.log("this == " + this);
    }
  
    Foo();      // this == [window]
    new Foo();  // this == [instance of Foo]

--

# What's the value of "this"?

    Foo.prototype.bar = function() {
        console.log("this == " + this);
    }
  
    var foo = new Foo();
    foo.bar();          // this == foo
    
    var bar = foo.bar;
    bar();              // this == window/global
  
--
 
# What's the value of "this"?

    var foo = {
        bar: function() {
            console.log("this == " + this);
        }
    }
    
    foo.bar();          // this == foo
    
    var bar = foo.bar;
    bar();              // this == window/global

--

# What's the value of "this"?

    function FooBar() {}
    var foobar = new FooBar();

    foo.bar();            // this == foo

    foobar.bar = foo.bar;
    foobar.bar()          // this == foobar

--

# Bound vs. not bound

- new -> bound
- calling a method via dot syntax -> bound
- explicitly binding "this" via .bind -> bound
- explicity setting "this" via .call or .apply

--

# .bind

    var foo = new Foo();
    var bar = foo.bar;
    var boundBar = bar.bind(foo);
    
    bar();              // this == window/global
    boundBar();         // this == foo

--

# .call & .apply

    Foo.prototype.bar = function(x,y) { return x + y };
    var bar = foo.bar;
    
    bar(5, 10);              // this == [window] w/ args 5, 10
    bar.call(foo, 5, 10);    // this == foo w/ args 5, 10
    bar.apply(foo, [5, 10]); // this == foo w/ args 5, 10

--

# .bind /w args

    Foo.prototype.bar = function(x,y) { return x + y };
    var bar = foo.bar;
    var boundBar = bar.bind(foo);
    var boundBarAndArgs = bar.bind(foo, 20, 30);
    
    boundBar(5, 10);          // same as foo.bar(5, 10);
    boundBarAndArgs();        // same as foo.bar(20, 30);

--

# Closure

    var x = 5;
    
    var foo() {
        x++;
        console.log(x);
    }
    
--

# Closure

    for (var i = 0; i < 5; i++) {
        button.onclick = function() {
            alert("I'm button #" + i);
        }
    }
    
The onclick handler uses whatever the value of `i` when the event handler is 
called.  When is it called?  What is the value of `i` at that point in time?
What does this program do?

--

# Closure

    var createHandler = function(i) {
        alert("I'm button #" + i);
    };
    
    for (var i = 0; i < 5; i++) {
        button.onclick = createHandler(i);
    }

Why does this make a difference?

--

# Closure
  
      var createCounter = function() {
          var i = 0;
          var counter = function() {
              return i++;
          }
          return counter;
      }
      
      var c = createCounter();
      console.log(c());   // 0
      console.log(c());   // 1
      console.log(c());   // 2
  
--

# Closure

    var createCounter = function() {
        var i = 0;
        var counter = function() {
            return i++;
        }
        return counter;
    }
    
    var c1 = createCounter();
    var c2 = createCounter();
    console.log(c1());   // 0
    console.log(c1());   // 1
    console.log(c1());   // 2
    console.log(c2());   // 0

--

# Really Learn the Language

- JavaScript Koans
- use a REPL to validate understanding

--

# Protect Yourself

- lint: jshint
- write tests, automate tests
- source control: git, hg, svn, etc.
- externalize storage: github, bitbucket

--

# Browser APIs

- dive into HTML5
- http://html5please.com/
- Blobs, BlobURLs, native drag and drop, native notifications, dialog element,
  web workers, WebGL, SVG, Canvas, localStorage, audio/video elements, 
  getUserMedia, Touch, 

--

# Using the new and shiny

- caniuse.com
- find polyfills

--

# Libraries

- websockets -> socket.io
- webRTC -> webrtc.io
- webGL -> THREE.js
- 

--

# Interacting with the Community

- github
- gh-pages

--

# Finding a Project

--

# Starting your Project


-- sponsors

# Our Sponsors

![Assembly](img/sponsors/assembly_logo.png)

![Village Brewery](img/sponsors/village_brewery_logo.png)

![Startup Calgary](img/sponsors/startup_calgary_logo.png)

![PetroFeed](img/sponsors/petrofeed_logo.png)

--

# Last Month

* Something awesome
* More awesomeness

--

# Next Month

* Something awesome
* More awesomeness
