---
title: Clojure Notes
layout: post
---

Day1: 08/Sep/2020

### What is Clojure?
Clojure is a delightful and powerful programming language with Lisp heritage.It is developed by Rich Hickey (with weird hair style). Clojure gives you better tools to tackle complex domains like Concurrent programming, parallelism et.al which is generally a bit complex using traditional tools.

It is important to keep in mind the distinction between Clojure language and the Clojure compiler. The Clojure language is a Lisp dialect with an emphasis on functional programming and is independent of any implementation. The Clojure compiler is an executable JAR file(clojure.jar), which takes code written in the Clojure programming language and compiles it into JVM(Java Virtual Machine) bytecode. This distinction is necessary because unlike most programming languages (Python, Ruby, C, C++ et.al) , Clojure is a hosted language. Clojure programs rely on JVM for core features like threading and Garbage collection.

Some of the concepts that we have to keep in mind while learning Clojure are,

* JVM processes execute Java bytecode.
* Java compiler produces Java bytecode from Java source code.
* JAR files are collections of Java bytecode.
* Java programs are usually distributed as JAR files.
* Java program clojure.jar reads Clojure source code and produces Java bytecode.
* Java bytecode is then executed by the same JVM process that is already running the clojure.jar

> As of this notes preparation the Clojure version is [org.clojure/clojure "1.10.1"]

Day2: 09/Sep/2020

### Leiningen
Most Clojurists (a term used to refer to a Clojure developer/practitioner) use Leiningen to build and manage their projects. We'll focus on the following main tasks here,
1. Creating a new Clojure project
2. Building the Clojure project
3. Running the Clojure project
4. Using the REPL

<br>
#### Installation & other needs to begin,
```bash
> java -version (**To check the Java version, must be higher than JDK1.6**)
> sudo apt-get install -y curl (*Install the curl command*)
> curl https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein > lein (*Get the latest stable version of lein script*)
> sudo mv lein /usr/local/bin/lein (*Move the script to user programs directory*)
> sudo chmod a+x /usr/local/bin/lein (*Give execute permissions to the lein script*)
> lein version (*To check the installation, and version of lein. It'll download clojure.jar*)
```

Day3: 14/Sep/2020

#### Creating a new Clojure Project:

```
$ lein new app clojure-noob
```

A simple "lein new app [app-name]" creates the skeleton for the project. A basic project set up looks like this,

```
~/learning/clojure/clojure-noob$ ll

-rw-r--r-- 1 statnuts statnuts   778 Sep 14 16:23 CHANGELOG.md
drwxr-xr-x 2 statnuts statnuts  4096 Sep 14 16:23 doc/
-rw-r--r-- 1 statnuts statnuts   125 Sep 14 16:23 .gitignore
-rw-r--r-- 1 statnuts statnuts   162 Sep 14 16:23 .hgignore
-rw-r--r-- 1 statnuts statnuts 14372 Sep 14 16:23 LICENSE
-rw-r--r-- 1 statnuts statnuts   479 Sep 14 16:23 project.clj
-rw-r--r-- 1 statnuts statnuts   987 Sep 14 16:23 README.md
drwxr-xr-x 2 statnuts statnuts  4096 Sep 14 16:23 resources/
drwxr-xr-x 3 statnuts statnuts  4096 Sep 14 16:23 src/
drwxr-xr-x 3 statnuts statnuts  4096 Sep 14 16:26 target/
drwxr-xr-x 3 statnuts statnuts  4096 Sep 14 16:23 test/
```

project.clj - is a configuration file for Leiningen. <br>
src/clojure_noob/core.clj - contains the source code of the project.

```
$ lein run (produces output for this toy program)
```

#### Bulding the Clojure Project:
Using [lein run], we can test out our code. But, if the need is to share the work with people who do not have Leiningen installed, then the best option is to build the project to create a .jar file, that can be run on any machine with Java installed. To do this, run the following command:

```
$ lein uberjar
```

This is what happens when you run the above command:

```
$ lein uberjar
Compiling clojure-noob.core
Created /learning/clojure/clojure-noob/target/uberjar/clojure-noob-0.1.0-SNAPSHOT.jar
Created /learning/clojure/clojure-noob/target/uberjar/clojure-noob-0.1.0-SNAPSHOT-standalone.jar
```

The above command creates a .jar file in the /target/uberjar/ folder. You can execute this file by running the following command,

```
~/learning/clojure/clojure-noob$ java -jar target/uberjar/clojure-noob-0.1.0-SNAPSHOT-standalone.jar
I'm a little teapot!
```

#### Using the REPL (Read - Eval - Print - Loop):
REPL is a tool for quick experimentation with code. In a PM's (Product Manager) worl, it's akin to quick prototyping and testing a simple feature/experiment. This enables quick feedback cycle to enable developers to change the approach if required. To start REPL, run the following command:

```
$ lein repl
```
It generates a bit of verbose info and helps in knowing the version of Clojure & namespace, which is usually in line with your src/[app-name]/core.clj.

```
~/learning/clojure/clojure-noob$ lein repl
nREPL server started on port 44171 on host 127.0.0.1 - nrepl://127.0.0.1:44171
REPL-y 0.4.4, nREPL 0.7.0
Clojure 1.10.1
OpenJDK 64-Bit Server VM 11.0.8+10-post-Ubuntu-0ubuntu118.04.1
    Docs: (doc function-name-here)
          (find-doc "part-of-name-here")
  Source: (source function-name-here)
 Javadoc: (javadoc java-object-or-class-here)
    Exit: Control+D or (exit) or (quit)
 Results: Stored in vars *1, *2, *3, an exception in *e

```

A basic trial run for the REPL leveraging the (-main) defined in the toy app (core.clj) and few other Lispy stuff,

```
clojure-noob.core=> (-main)
I'm a little teapot!
nil
clojure-noob.core=> (+1 2 3 4)
Execution error (ClassCastException) at clojure-noob.core/eval1619 (form-init5561836152289490106.clj:1).
class java.lang.Long cannot be cast to class clojure.lang.IFn (java.lang.Long is in module java.base of loader 'bootstrap'; clojure.lang.IFn is in unnamed module of loader 'app')

clojure-noob.core=> (+ 1 2 3 4)
10
clojure-noob.core=> (* 1 2 3 4)
24
clojure-noob.core=> (first 1 2 3 4)
Execution error (ArityException) at clojure-noob.core/eval1625 (form-init5561836152289490106.clj:1).
Wrong number of args (4) passed to: clojure.core/first--5384

clojure-noob.core=> (first [1 2 3 4])
1
clojure-noob.core=>

```
Note: Added few errors deliberately to remember, what happens when you are a human and make mistakes.

Conceptually REPL is similar to Secure Shell (SSH), the Clojure REPL allows you to interact with a running process. This is a powerful feature because, you can attach a REPL to a live production app and modify the program as it runs.


Day4:
### How to use EMACS, an excellent Clojure Editor?
As we learn along to master Clojure, and important aid(or tool) we will use during the journey is our editor. I choose to follow along with Emacs (wanting to learn this extensible editor for long, so no better excuse than to use it for learning Clojure programming). Emacs offers a very tight integration with Clojure REPL which helps us to create a tight feedback loop as we write programs. Emacs is also great for working with any Lisp dialect; as it is written in a Lisp dialect called Emacs Lisp.

#### Emacs Escape Hatch
CTRL + G is one of the most important key combination in the world of Emacs. This combination will help you get out of some of the most astounding situations/troubles during your Emacs journey. This will not kill the Emacs process, but just stops the current action.

Some important key bindings in Emacs,

|Keys| Description|
|--|--|
|C-a|Move to beginning of the line.|
|M-m|Move to fist non-whitespace character on the line.|
|C-e|Move to end of line.|
|C-f|Move forward one character.|
|C-b|Move backward one character.|
|M-f|Move forward one word.|
|M-b|Move backward one word.|
|C-s| Regex search for text in current buffer and move to it. Press C-s again to move to next match.|
|C-r| Same as C-s, but search in reverse.|
|M-<| Move to the beginning of buffer.|
|M->|Move to end of the buffer.|
|M-g g| Go to line.|
|C-x o| Switch cursor to another window.|
|C-x 1| Delete all other windows, leaving the current window in the frame.|
|C-x 2| Split frame above and below|
|C-x 3| Split frame side by side|
|C-x 0| Delete current window.|

Hail Killing and Yanking Text,

|Keys| Description|
|--|--|
|C-w| Kill region.|
|M-w|Copy region to kill ring.|
|C-y|Yank.|
|M-y|Cycle through kill ring after yanking.|
|M-d|Kill word.|
|C-k|Kill line.|


Editing and Help,

|Keys|Description|
|--|--|
|Tab|Indent line|
|C-j|New line and indent, equivalent to ENTER followed by TAB.|
|M-/| Hippie expand; cycles through possible expansions of the text before point.|
|M-\\ |Delete all spaces and tabs around point.|

Day 5:

#### Working with Files
The key binding to open a file in emacs is 
```
C-x C-f
```
To save the file after writing content to it,
```
C-x C-s
```

Few interesting key bindings that are useful,
```
C-x k -> to kill the current buffer.
C-x b [buffer_name] -> to switch the buffer
```
key bindings - what is it? Emacs actually binds keystrokes to commands, which are just elips functions. E.g. C-x b is bound to the function switch-to-buffer. Likewise, C-x C-s is bound to save-file.You can redefine functions, because at its core Emacs is just a Lisp interpreter. The freedome to modify Emacs using a powerful programming language is what makes Emacs so flexible and why some programmers really like it.

#### Modes
An Emacs mode is a collection of key bindings and functions that are packaged together to help you become productive when editing different types of files. Modes come in two flavors: major modes and minor modes. Many modes are distributed as packages , and they can be browsed and installed using the following commands.

```
M-x package-list-packages
M-x package-install
```

#### Core Editing Terminology and Key Bindings

|Keys| Description|
|---|--|
|C-spc|To mark set|
|C-w|Kill region.|
|M-w|Copy region to kill ring.|
|C-y|Yank|
|M-y|Cycle through kill ring after yanking.|
|M-d|Kill word.|
|C-k|Kill line.|
|Tab|Indent line.|
|C-j|New line and indent, equivalent to ENTER followed by TAB.|
|M-/|Hippie expand; cycles through possible expansions of the text before point.|
|M-\\ |Delete all spaces and tabs around point.|
|C-h k key-binding | Describe the function bound to the key binding. To get this to work, you actually perform the key sequence after typing C-h k.|
|C-h f| Describe function|

*Day 6 : 29/Sep/2020*
#### Using Emacs with Clojure
To work with Emacs while developing clojure applications, it is important to understand how to start an REPL process that's connected to Emacs, and how to manage Emacs windows.Post which we need to remember/practise a set of useful key bindings for evaluating expressions, compiling files, and performing other quirky tasks.

Emacs CIDER package is the most important package while working with Clojure applications on Emacs. To install,
```
M-x package-install cider
```

This package will allow us to open an REPL within Emacs, and provides us with the key bindings that helps us interact with the REPL efficiently.To start the REPL and create a new buffer use the following command, after navigating to the src/core.clj of your sample app.

```
M-x cider-jack-in
```
This will open up two windows, one for our core.clj file and the next one for REPL.

|Keys|Description|

|C-x C-e| Run the command cider-eval-last-expression.|
|C-u C-x C-e| Prints the result of the evaluation after the expression.|
|C-c M-n| Sets the namespace to the namespace mentioned at the top of your current file.|
|C-c C-k| Compiles your current file in REPL session|
|C-up/down arrow|Cycle through REPL history.|
|C-c C-d C-d| Displays the documentation for the symbol under point.|
|M-.| Will navigate to the code for symbol under the point.|
|M-,| Will return to your original buffer and position.|
|C-c C-d C-a|Let's you search arbitrary text across fn names and doc.|
|q| Remember this key, when you feel you're in the wrong place to exit from window.|
<br>

*Day 7: 30/Sep/2020*
### DO THINGS: A CLOJURE CRASH COURSE
Clojure's syntax is simple. Like all Lisps, it employs a uniform structure, a handful of special characters, and a hell lot of parentheses.

#### Forms *(means valid code or expressions in Clojure)*
All Clojure code is written in a uniform structure. Clojure recognizes two kinds of structures:
- Literal representations of data structures (like numbers, strings, maps and vectors).
- Operations (+, - , * ....)

All operations takes the form, and Clojure uses whitespace to separate operands, and it treats commas as whitespace.
```
(operator operand1 operand2 ... operandn)

Examples: following two expressions produces same results.
(+ 1 2 3)
(+ 1,2,3)

```

#### Control Flow (IF)

```
(if boolean-form
 then-form
 optional-else-form)

An Example:
user=> (if true
  #_=> "I swear by my life"
  #_=> "Damn you")
"I swear by my life"


user=> (if true
  #_=> (do (println "Success!")
  #_=> "By Zeus Hammer")
  #_=> (do (println "Failure")
  #_=> "By Aquaman"))
Success!
"By Zeus Hammer"

```

#### Control Flow (When)

Use when if you have many things to do when some condition is true, and always want to return nil when the condition is false.

```
user=> (when true
  #_=> (println "Success!")
  #_=> "abra cadabra")
Success!
"abra cadabra"

```

*Day 8: 03/Nov/2020*
#### nil, true, false, Truthiness, Equality and Boolean expressions
Clojure has true and false values. nil is used to indicate no value in Clojure. We can check whether a value is nil with the nil? function.Both nil and false are used to represent logical falsiness, whereas all other values are logically truthy.

```
(nil? 1)
; => false

(nil? nil)
; => true

(if "there is covid"
    "Better keep yourself isolated")
; => "Better keep yourself isolated"

(if nil
    "You dont have covid"
    "Stay safe, have fun at home")
; => "Stay safe, have fun at home"

```

Equality operator:
```
(= 1 1)
;=> True

```

Clojure uses the Boolean operators "or" and "and". 
<br>
"or" returns 
* either the first truthy value or the last value. 

<br>
"and" returns
* the first falsey value or if no values are falsey, the last truthy value.
<br>

```
// first truthy is ":large_I_mean_Venti: hence the answer.
(or false nil :large_I_mean_Venti :why_cant_I_just_say_large)
; =>:large_I_mean_Venti

// No truthies, so returns the last value "false"
(or (= 0 1) (= "yes" "no"))
; => false

//No truthies, so returns the last value "nil"
(or nil)
; => nil

// No falsey, hence the last truthy ":hot_coffee" returned.
(and :free_wifi :hot_coffee)
; => :hot_coffee

// First falsey "nil" is the answer.
(and :feelin_cool nil false)
; => nil

```


#### Naming values with def :
We can use def to bind a name to a value in Clojure. Please note the use of term bind, compared to the use of term "assigning" to a "variable" used in other languages.Here we treat "def" as a way of defining constants.

```
//A simple assignment - treat it like constant definition.
(def covid_heroes
     ["Doctors", "Nurses", "Attendants", "Other medical staff", "Support Staff"])

//Another approach, function error-message takes a single arg, uses it to determine the string to return.

(defn error-message
      [severity]
      (str "OH CRAZY! IT'S A DISASTER! WE'RE"
           (if (= severity :mild)
               "MILDLY INCONVENIENCED"
               "DOOMED")))
(error-message :mild)

```

*Day 8: 19/March/2021*
### Data Structures


<br>
## References
<br>
### Books:
<br>
### Links:
<ol>
<li>Beginner’s Guide to Emacs : http:// www.masteringemacs.org/articles/2010/10/04/beginners-guide-to-emacs/ </li>
<li>Emacs CIDER: https://github.com/clojure-emacs/cider/</li>
</ol>





