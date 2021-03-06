<a name="session-01---012317---installation--openframeworks-basics"></a>
# Session 01 - 01/23/17 - Introduction to Algorithmic Sound / Installation / openFrameworks basics

<!-- MarkdownTOC -->

- [Session Overview](#session-overview)
- [Algorithmic Sound](#algorithmic-sound)
    - [Why?](#why)
    - [Challenges?](#challenges)
    - [Application Fields](#application-fields)
    - [Reading Material](#reading-material)
    - [Examples](#examples)
    - [Synthesis Techniques](#synthesis-techniques)
    - [Other tools](#other-tools)
    - [Why C/C++?](#why-cc)
    - [Why openFrameworks?](#why-openframeworks)
    - [Downsides?](#downsides)
- [Topics](#topics)
    - [Installation](#installation)
    - [openFrameworks folder structure](#openframeworks-folder-structure)
    - [Creating a project](#creating-a-project)
    - [Project structure](#project-structure)
    - [Xcode Walkthrough](#xcode-walkthrough)
    - [Main Entrypoint](#main-entrypoint)
    - [Headers, declaration files, .h files](#headers-declaration-files-h-files)
    - [Source files, definition files, .cpp files](#source-files-definition-files-cpp-files)
    - [OpenFrameworks Commands](#openframeworks-commands)
    - [Coding Style](#coding-style)
    - [Basic window setup: framerate, shape, fullscreen](#basic-window-setup-framerate-shape-fullscreen)
    - [Keyboard Interaction](#keyboard-interaction)
    - [Mouse Interaction](#mouse-interaction)
    - [Window Events](#window-events)
    - [Introductory Coding Topics](#introductory-coding-topics)
- [Where to find stuff](#where-to-find-stuff)
    - [OpenFrameworks](#openframeworks)
    - [C++](#c)
- [Homework](#homework)
- [Lab](#lab)

<!-- /MarkdownTOC -->

<a name="session-overview"></a>
# Session Overview

This session will introduce you Algorithmic Sound, a field that tries to generatively create sound as well as the tool of choice for exploring this vast topic, openFrameworks, a creative-coding toolkit written primarily in C++.  It brings together many frameworks for a cross-platform coding environment capable of real-time audio visual analysis, graphics, sound processing, 3D, multithreading, communication protocols, and plenty more.  In this session, we'll see how to navigate openFrameworks, build a project, compile existing examples, and find additional resources.

<a name="algorithmic-sound"></a>
# Algorithmic Sound

a.k.a. procedural sound, generative sound

Algorithm: computational procedure for solving a problem (Al-Khwarizmi, roots for Algebra as well).

* Algorithmic: Computational procedure for solving a problem.
* Nonlinear:  As compared to a recorded piece of audio, the audio can be dynamic, ever-changing.
* Procedural:  Depends on inputs, outputs, time, behavior, sensors, etc...
* Agency:  Can build a sense of being/self/ego by incorporating movement, position, continuity.

<a name="why"></a>
## Why?

Media is becoming increasingly algorithmic.  Authoring tools still rely on heavy narrative elements.  Can we bring advances in pattern recognition, machine learning, and deep learning to creative sound practice?  If we can, then we can build smarter interaction, deeper algorithmic behavior, and more nonlinear and procedural sound into our compositions.

Think about sound and soundscapes as a parametric, procedural, and generative process which we can describe with code.  Describing traditionally fixed media as an algorithmic process allows for infinite generation and endless possibilities. Will eventually learn to use machine learning to help us understand sound collections, organize them, and procedurally control their playback.

This course will emphasize techniques that target more "low-level" organization of sound.  If you explore these topics in more detail, you can eventually learn to organize sound at longer temporal scales and target more musical primitives.

<a name="challenges"></a>
## Challenges?

* Dynamic: we want an algorithm that allows us to explore many outputs.
* Narrative: we want to be able to develop a story, relate the ideas the algorithm tries to portray in the result.
* Long term structure: we want to be able to relate ideas over longer periods of time, not just instants of time.
* Coupling interaction: we want to be able to allow users/viewers/listeners to change the process.
* Overcoming 1:1 correlation with audio/vision: we want to be able to allow the design of sound to follow trajectories that build continuity across changes in visual media.
* Beyond "one-size-fits-all" approaches: we want to understand the constraints of our work.

<a name="application-fields"></a>
## Application Fields

* Film (foley) sound
* Virtual Reality
* Augmented Reality
* Game design
* Musical sound practice
* Software development
* Installation artwork

<a name="reading-material"></a>
## Reading Material

* _Sound Design : The Expressive Power of Music, Voice and Sound Effects in Cinema_ by David Sonnenschein
* _Audio/Vision_ by Michel Chion
* _Sonic Experience_ by Augoyard Torgue
* _Procedural Sound_ by Andy Farnell
* [In the Blink of an Eye](https://www.amazon.com/exec/obidos/ASIN/1879505622/filmsounddesign/) by Walter Murch
* [Current directions in Procedural Audio](https://www.youtube.com/watch?v=nGmZ2PioNwI) By PhD students Christian Heinrichs and Roderick Selfridge with introduction by Andy Farnell

<a name="examples"></a>
## Examples

* [RjDj](https://www.youtube.com/watch?v=vWsc2bwRkI0)
* [Inception app](https://www.youtube.com/watch?v=Kgh63r-1Cd8)
* [Dimensions app](https://www.youtube.com/watch?v=7-caFZJ1-oM)
* [No Man's Sky](https://www.youtube.com/watch?v=BgAslKUaNx4)
* [Spore](https://www.youtube.com/watch?v=zi2GvqboQfY)
* [Papa Sangre](https://www.youtube.com/watch?v=lWCQwBV0lzM)
* [Pugs Luv Beats](https://www.youtube.com/watch?v=V0i18_--8Yc)
* [Sonifying Sorting Algorithms](https://www.youtube.com/watch?v=kPRA0W1kECg)
* [Fantom](https://www.youtube.com/watch?v=timya2kIV4M)

<a name="synthesis-techniques"></a>
## Synthesis Techniques

* AM
* FM
* Physical Models
* Additive
* Subtractive
* Concatenative
* Granular
* Binaural
* Ambisonic
* Wavefield

<a name="other-tools"></a>
## Other tools

* PD, libPD
* Max/MSP
* Blueprint (Unreal Editor 4)
* SuperCollider
* Chuck
* Auraglyph
* Cinder

<a name="why-cc"></a>
## Why C/C++?

* Extensible:  E.g., can write externals in C/C++ which are supported by most of the above tools.
* Fast:  Often audio demands high samplerate.  Working with procedural audio often demands many more resources than fixed media.  Multiply these together, and you need a very fast implementation capable of doing more.

<a name="why-openframeworks"></a>
## Why openFrameworks?

* Community:  A lot of support online and through other users.
* Libraries:  Integrates with nearly every C/C++ library out there.
* Creative:  Mostly focused on artists and creators.
* Quality:  Because it is so performant, you can often push more boundaries than in any other platform.

<a name="downsides"></a>
## Downsides?

* Low-level:  Often hard to iterate on ideas working at the level of C/C++, as compared to node-based languages.
* Portability:  Often the SDKs which your application are built against only last 1-2 years.
* Difficult:  Related to the other downsides, but it is often a lot more difficult because it is so much more of a blank canvas.

<a name="topics"></a>
# Topics

<a name="installation"></a>
## Installation

Download the zip file and place it somewhere.  E.g. ~/dev/openFrameworks

<a name="openframeworks-folder-structure"></a>
## openFrameworks folder structure

- /addons
- /apps
- /docs
- /examples
- /export
- /libs
- /other
- /projectGenerator
- /scripts

<a name="creating-a-project"></a>
## Creating a project

- [EASY] Project Generator
- [MEDIUM] Copy existing project but maintain "hierarchy" with relationship to base oF directory
- [HARD] Makefile based projects just need to refer to the base oF directory and use an existing makefile + addons.make

<a name="project-structure"></a>
## Project structure

- /src  
- /bin  
- /bin/data  
- ../../../addons  

<a name="xcode-walkthrough"></a>
## Xcode Walkthrough

- Folder navigator  
- Schemes  
- Target executable  
- Project and application settings

<a name="main-entrypoint"></a>
## Main Entrypoint

Every c++ program needs a "main" function.  This is where the program begins and then continues execution, line by line.  We can put everything into main.cpp and play with a camera like so:

```cpp
#include "ofMain.h"

class ofApp : public ofBaseApp{
public:
    // i get called once
    void setup() {
        cam.setup(width, height);
        ofSetWindowShape(width, height);
        ofSetFrameRate(1);
    }
    
    // i get called in a loop that runs until the program ends
    void update() {
        cam.update();
    }
    
    // i also get called in a loop that runs until the program ends,
    // just after update is called.
    void draw() {
        cam.draw(0, 0);
    }
private:
    ofVideoGrabber cam;
    int width = 640;
    int height = 480;
};


int main(){
    ofSetupOpenGL(1024, 768, OF_WINDOW);
    ofRunApp(new ofApp());
}
```

<a name="headers-declaration-files-h-files"></a>
## Headers, declaration files, .h files

Generally instead of putting everything into a giant file, we split them up into headers, or declaration files, and source files.  The header files provide an interface to everything that will be defined.  For those of you that haven't programmed before, this won't make much sense right now but stick with it.  The header files is like a blueprint.  It doesn't actually define anything, meaning you can't actually execute any of this code.  It is just showing you all the code that once it is defined, can be executed.

So let's see a simple example:

```cpp
void addTwoNumbers(int a, int b);
```

This is an example of a function declaration.  It's curly braces haven't been opened and the function isn't defined.  It's just the declaration.  I'm declaring that I will define it at some point.

**ofApp.h**

```cpp
#pragma once
 
#include "ofMain.h"
 
class ofApp : public ofBaseApp{
 
    public:
         
        // declaration of functions
        void setup();
        void update();
        void draw();
};
```

<a name="source-files-definition-files-cpp-files"></a>
## Source files, definition files, .cpp files

**ofApp.cpp**

```cpp
// i get called once
void ofApp::setup(){
     
    // do some initialization
     
    // set the size of the window
    ofSetWindowShape(250, 250);
     
    // the rate at which the program runs (FPS)
    ofSetFrameRate(30);
     
}
 
// i get called in a loop that runs until the program ends
void ofApp::update(){
     
}
 
// i also get called in a loop that runs until the program ends,
// just after update is called.
void ofApp::draw(){
     
}
```

<a name="openframeworks-commands"></a>
## OpenFrameworks Commands

oF commands all start with "of".  If you are using an IDE w/ code completion, this makes coding a lot easier.

<a name="coding-style"></a>
## Coding Style

Stylistically, be consistent.

<a name="basic-window-setup-framerate-shape-fullscreen"></a>
## Basic window setup: framerate, shape, fullscreen

- Program flow

    * `main()`  
    * ...
    * `void setup()`  
    * `void update()`  
    * `void draw()`  
    * `void update()`  
    * `void draw()`  
    * `void update()`  
    * `void draw()`  
    * ...
    * `void exit()`  

- Framerate functions

    * `ofGetFrameRate()`  
    * `ofSetFrameRate(int rate)`  

<a name="keyboard-interaction"></a>
## Keyboard Interaction

- `void keyPressed(int key)`  
- `void keyReleased(int key)`  

<a name="mouse-interaction"></a>
## Mouse Interaction

- Called on the active window when the mouse is moved:
    `void mouseMoved( int x, int y )`
- Called on the active window when the mouse is dragged, i.e. moved with a button pressed:
    `void mouseDragged( int x, int y, int button )`
- Called on the active window when a mouse button is pressed:
    `void mousePressed( int x, int y, int button )`
- Called on the active window when a mouse button is released:
    `void mouseReleased(int x, int y, int button )`
- Called on the active window when the mouse wheel is scrolled:
    `void mouseScrolled(int x, int y, float scrollX, float scrollY )`

<a name="window-events"></a>
## Window Events

- resize  
- dragEvent  
- fullscreen  

<a name="introductory-coding-topics"></a>
## Introductory Coding Topics

### What is a function?

They are blocks of code that run when you "call" them.  They have a return type, which can also be "void", meaning they don't return anything, and can have parameters, which are things that you must give to the function in order for it to run.  Here is a simple function (also known as a method):

```cpp
int addTwoNumbers(int firstNumber, int secondNumber)
{
    return firstNumber + secondNumber;
}
```

The return type is `int`.  Its name is `addTwoNumbers`.  And it takes two parameters of type `int` and `int`.  The names of the variables of these parameters are not important or necessary for us to know in order to use the function.  We can call the function by using its name, `addTwoNumbers`, and giving it values that are the same type as the required parameters it needs.  There are 2 required parameters in this function, both which should be integers.

Here is an example of how we'd call this function:

```cpp
cout << addTwoNumbers(10, 20) << endl;
```

This will call the function giving the value of 10 to `firstNumber` and 20 to `secondNumber`.  The code moves from the function call of `addTwoNumbers(10, 20)` to the function declaration `int addTwoNumbers(int firstNumber, int secondNumber)`, replacing the values of the variables `firstNumber` and `secondNumber` with 10 and 20.  Then the function executes, and returns the result of 10 + 20;

The `return` type of this function is `int`, meaning there is an integer returned. If it were `void`, we would not have had to return anything.

### What are variables?

Variables are ways to store information.  They have a type, such as `int` for integers, `float` for floating point values, or `string` for strings.  Variables can also store more complicated types such as "instances" of a `class`.  We could have called the function above like so:

```cpp
void setup()
{
    int someNumber = 10;
    int x = addTwoNumbers(5, someNumber);
}
```

The value of x is now 15.

### What is a `class`?

A `class` contains a set of methods and variables. We can instantiate an object in a very similar way as we do with an `int` or `float`, by simply creating a variable, e.g. `ofVideoGrabber camera`; When we create this object, we can call the public methods that are defined in the class definition.  That's unlike the `int` or `float` variable which does not have any methods.

### What is the difference between a *method* and a *function*?

They mean the same thing. 

### What is the difference between a class definition and a class declaration?

A definition is often contained in the .cpp file, and is the code that is run when a function is called. This is the code that goes between the curly braces after the function’s re-declaration in the .cpp file. A class declaration appears in the .h file, and only provides syntax for what the return type of a function is (e.g.: `void`, `int`, `float`, `string`, etc…), and what parameters the function takes.

### What's the difference between an object and a class?

An object is an "instance" of a class.  Consider a simple class like so:

```cpp
class Box {
    public:
        int x, y, width, height;
};

Box box_1, box_2;
```

`Box` is a class, and we created two instances of it called `box_1` and `box_2`.  We could have called it whatever we wanted, e.g. `zebra`.  But often we try to use names of variables that are meaningful.

### What are `if`/`else if`/`else` statements

`if` statements are ways to control the flow of execution.  They take "boolean" logic in order to understand whether to execute a block of code, or continue onto an `else` statement.  An example is below:

```cpp
if(5 > 2) {
    // do something
}
else if(4 > 2) {
    // this will never happen
}
else {
    // this will never happen
}
```

### What are boolean operations?

* `>`: greater than
* `<`: less than
* `>=`: greater than or equal to
* `<=`: less than or equal to
* `==`: equal to
* `||`: or
* `&&`: and

### For loops

`for` loops allow you to repeat the execution of a block of code, keeping track of the number of times the block of code has been executed.  This is useful for things like iterating over a list of elements, or a collection of some sort.  Or for doing something many times, perhaps with some slight variation each time.  Here is a simple example of a for loop:

```cpp
for(int i = 0; i < 10; i++) {
    cout << i << endl;
}
```

### Comments
    
Comments allow us to add notes that aren't compiled/linked/executed.  These are handy for documenting your code.

```cpp
int x; // one line comment
/* 
block
comments
span
multiple
lines
*/ 
```

### What is the difference between compiling, linking, and executing?

So there are three stages essentially for your program.  Compilation, linking, and execution.  And these each have their own types of errors.  Compiler errors, linker errors, and runtime errors.

What's compilation?  Once you have coded your program, you run a program called a compiler.  The compiler takes the c++ code, parses it, analyzes it, generates an abstract syntax tree, generates some immediate representation code, optimizes it, creates some assembly level language which some hardcore programmers actually write directly.  This finally produces what's called object code and is often just a .o file.  Every one of your header/source files generates 1 .o file.

After compiling, the linker combines all of the object files that you told it to compile into an executable file.  If you refer to some symbol in another object file, then the linker will be the one to tell you if you forgot to define it.  The compiler won't care.

Finally, once you have created your program and it is running, there can be runtime errors.  Maybe it tries to load a file that doesn't exist.  That is not a compiler or linker error.  It's more of a logic error.  The program expected it could do something and it couldn't.

So it's handy to know the basic difference between compilation, linking, and runtime errors.  Compilers care about the syntax.  Linkers care about whether you have actually defined what you said you would.  And at runtime, you just hope that everything happens as you thought it would.

<a name="where-to-find-stuff"></a>
# Where to find stuff

<a name="openframeworks"></a>
## OpenFrameworks

- [ofBook](http://openframeworks.cc/ofBook/chapters/foreword.html)
- [Forums](https://forum.openframeworks.cc/)
- [Documentation](http://openframeworks.cc/documentation/)
- [ofxAddons](http://ofxaddons.com/categories)

<a name="c"></a>
## C++

- [C++ Tutorial](http://www.cplusplus.com/doc/tutorial/)  
- [Another C++ Tutorial](http://www.cprogramming.com/tutorial/)  
- Bjarne Stroustrup’s The C++ Programming Language  
- Deitel & Deitel’s C++ How to Program  
- StackOverflow  

<a name="homework"></a>
# Homework

Your homework is two parts:

1.) [50 percent] I want you to have a look at the examples, compile them, run them, explore the code, and make sure you don't have any issues getting code to run.  Try making tweaks and explore what you can do with just the examples.  They are a great place to get a sense of what is possible.  Make sure you have compiled at least one example project.

2.) [50 percent] I'd like you to find an example of algorithmic sound and attempt to explain the algorithm.  I want you to describe the process from start to finish, what the context for the work is, and how it is aided if at all by algorithmic thinking.

For next week, you will present your homework to your classmates: the compiled patch as well as the example that you have found using 5 minutes for each.  If you do not want to present in class, you can submit an up to 5 minute video for either portion of the assignment and submit it to the forums.

<a name="lab"></a>
# Lab

For the next 50 minutes I'd like to make sure everyone has a working installation of openFrameworks and can create a project w/ the Project Generator and run an example.
