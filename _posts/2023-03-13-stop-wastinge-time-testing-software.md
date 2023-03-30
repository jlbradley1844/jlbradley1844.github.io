---
title: Stop Wasting Time Testing Software
---
## Stop Wasting Time Testing Software

Ok, apologies for the clickbait. If you're a software developer, you should be testing your software.
But you should never forget: tests never ship. Time spent writing test code is time not delivering value
to customers.

To limit this, do something better than testing: use techniques that _guarantee your software will
work_. Or at least, limit the "surface area" you have to test. This article presents some nearly labor-free ideas for
achieving the results of testing, without writing one test. Plus a few more ideas that take time
but, when put into practice, dramatically reduce bugs.

_Use "High-Reliability" Language Features_: 

Most languages have statements that can eliminate 
frustrating low-level bugs by replacing common but error-prone language features:

|  Bug type   |  Error-prone feature                |  Use this instead                                   |
|-------------|-------------------------------------|-----------------------------------------------------|
|  Off-by-one errors  |  Loop iterators using count variables |  Range-based iterators, iterator objects  |
|  Variable aliasing  |  Mutable variable reuse     | Immutable variables; static types (see below)       |
|  Failure to check null |  Nullable types          | "Option" types. Better: avoid such logic            |
|  Memory errors (c++) | Raw pointers, raw memory access | Smart pointers, containers, numerous others    |

Look at the error-prone features. They all have something in common:
* They're all old features that every language seems to have
* They're features taught immediatly in most introductory programming classes

Frustratingly, many of these "safe" features are only covered in books, or in "advanced" courses. If you learned
your language in a single college course and then just stopped, you'll have to keep learning on your own.
You really have no choice; working with a crippled language subset, particularly one with only the buggy parts, is
programming malpractice.

_Want to learn more?_ Start by making sure you language features and proper style; don't just
learn the basics. Python coders should "Pythonic" coding style to avoid issues.
Typescript and "modern javascript" introduce features meant to avoid bugs; use them.
For C++, learn the _Core Guidelines_; they even include a header-only library that helps you avoid
bad language
features (for example, replace your nullable type by usign the Optional<> type). 
Many languages have publications by language authorities
that recommend "the good parts" of the language and show how to avoid "the bad parts." Learn those, and
you won't have to write extra unit tests to catch your null-assignment bugs.

Ideally, the language itself would address the bugs.
A twenty-year old version of this list would have listed GOTO statements, a feature nearly all languages
had in spite of the fact it made code hard to understand and debug. Modern languages made these bugs impossible by
eliminating GOTO. It would be great if nobody had to learn about error-prone features, but it's impractical. You
can't choose what language you use (usually), but you can choose the parts you use.

_Linters and Static Code Analysis_:

We make mistakes. If you have code reviewers, they make mistakes. Computers make far fewer
than you. So: a [linter]<https://en.wikipedia.org/wiki/Lint(software)> is a program that checks
your code to find common bugs. You should know what these are in the language of your
choice and *use it*. Sometimes you also have tools for "static code analysis," which are more heaviweight
than linters, and find even more issues.

I've found there are three ways to invoke linters, and I have this preference, in order:

1. Through a source-code hook that runs it every time you commit (or push), and prevents you from adding bad code;
2. Through a continuous-integration system that reports back issues to you;
3. Manually

The more "junior" you are in the role, the less control you have over doing 1 and 2, so you may be stuck
doing it manually. If so, invest the time tuning the linter _configuration file_. Linters
are notorious for reporting false alarms. Turn off everything you know you're going to ignore, so you don't
get in the bad habit of ignoring linter errors. If you're more senior, invest the time getting in CI, as indicated.

And if you are using a compiled language with a "treat warnings as error" flag, use it! The compiler writers
know iffy code when they see it. If you're compiling without the "treat warnings as error" flag, you're probably
junior enough that you could benefit from turning it on.

_"But I don't have a good linter for [your language here]!!"_ You probably do. You may need to search open 
source docs, or discussion boards like reddit or stack over flow.
There are linters even for shell script languages! And if you have little utility language you're using,
read the full documentation on the command parameters; there's probably a "debug flag" that can help find
errors in your code.

_More on that_: Browse <https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis> for a list
of "static code analyzers"; some of these go beyond source code anlysis to look at deeper issues. Scroll to
the bottom of the page for linters on the most common dynamically-typed languages.

_Strict Type Systems_:

Strict type checking isn't static type checking. "Static types" are a function of a language; it means that
variables are declared with a particular "type" and once declared they cannot be changed. Python and javascript
fanbois hate static types, mainly because they don't have those. After all, the original purpose of static
types was to
tell the compiler how to interpret the blotch of memory the variable contained; dynamic types keep track
of it for you, which seems like a commonsense thing to do.

"Strict types" instead are focused on making sure you use your variables only for one sort of thing, by
making sure you don't accidentally use it for the wrong thing. Do you have it? It depends on the language.
* Some languages are strongly typed - OCaml/F#, Scala. They are very strict and require you to plan variable use.
* Others are potentially typed - as long as you avoid workarounds like generic "Object" types. Java and C# are like that. C++ has so many workarounds some refer to it as "weakly" typed.
* Finally, for some, you need language extensions. For javascript, typescript is used. Python has PEP 484 "type hinting."

A common objection to strict typing is that it makes certain programming techniques hard, and forces
one to spend time designing types rather than working on the problem at hand. This split probably explains
why brilliant young programmers love dynamic typing and the grizzled veterans who manage them prescribe
strict typing systems. Designing your types poses a challenge if you don't know the problem domain
deeply enough - meaning perhaps you aren't ready to code. My office is full of OCaml fans, some of which
are perversely proud of the fact you can't write a line of code until you understand exactly what 
it is you need to do.

Dynamic language fans don't agree. Perhaps not wanting to yield ground, 
they call their systems "type hinting": optional typing systems that can be used strictly as needed,
but not when it gets in the way. And indeed, the recommendation is to use them
only as needed - where it takes care of validation, or self-documennts and enforces proper
contract use. Declaring everything with a type is generally unneeded and adds a lot of verbosity.
Conversely, thinking of numerical types as units (for instance, using 'millisec' instead of 'int') not
just documents usage, but prevents the common errors caused by mixing up your units - the errors your
physic teacher constantly warned you about.

_Design by Contract_:

This concept was made popular in Eiffel, a rarely-used but influential object-oriented programming language. 
In "design by contract," every routine (or method, function, etc.) checks three things:

* Preconditions
* Postconditions
* Invariants

Preconditions are assertions that check exactly what state an object must be in when entering the routine. 
Postonditions are assertions
that check exactly what state the object must be when exiting. And invariants are assertions that check
things that must not be changed inside the rotuine.

Eiffel never caught on as a language. And from the paucity of open-source frameworks, it seems that 
design-by-contract generally hasn't caught on in the industry. So why is this recommended?

Two reasons. The first is to get you in the habit of thinking about these things. The second is that it
_is_ used in the industry, but in nonobvious ways.

If your language has assertions, you don't need a framework, and you can apply this as needed. Those of you
working in compiled language can use a compiler directive to apply these runtime checks only in "debug" builds.
In practice this isn't as much work as it appears. Note that there's no need to always do all three sorts
of checks! Use only the one or
two that are necessary. 

This is why I say design-by-contract is used in industry in nonobvious ways.
If you're looking at an old, well-maintained piece of object-oriented code, it's
common to find a method called IsValid() called at important points in the code. That is probably someone doing
design-by-contract; it's a common way of enforcing invariants or postconditions.

The main purpose of design-by-contract was to properly managed states in objects. Program state is very 
important in object-oriented
code, but mishandling state causes errors. Instead of using contracts to manage states, consider getting
rid of states. In functional programming languages, the focus is
on ensuring immutability and statelessness. It is impossible to get errors caused by mishandling state when there
is no state! Many languages support more functional features than you realize; Javascript and Python support
many common functional idioms. "Modern" C++ allows for many functional 
techniques through algorithms and new standard library
features; using these will both shorten you code and reduce bugs.

_Designing Quality Into Code_:

Other than that, the only way to avoid putting bugs into your software is to not write 
anything. If you write software, you will create bugs.
Stopping it isn't a matter of willpower, or being clever. You'll have
to learn habits for making higher quality code; "try harder" won't work.
So much as it may risk being off topic, improving code and reducing the "surface area" you
have to test is one last thing I'd like to mention.

There are many books to guide you.  
Books like Robert Martin's _Clean Coding_ are classics because they teach you
actionable ways to produce objectively better code, ones that are less likely to have bugs.
Steve McConnel's _Code Complete_, which covers some of the same ground, is still in print, even
though first edition came out in the nineties! Studying these books and _applying these techniques_ will
give you habits that are less likely to put bugs in.

The best way to reduce bugs is by reducing the amount of code you have to write! You probably don't know
your libraries nearly as well as you think - or know just how flexible they are. The "algorithm" library
in C++ is both very powerful and very low-level; if you find yourself doing sorting, searches or filtering,
you should be using it rather than rolling your own. Most languages have their own variants. Don't overlook
the low-level libraries, either! Admittedly, if your code is nothing but a sequence of library calls,
it feels like you aren't "really programming"; that gives rise to the commonly-heard complaint "All I do
is paste together APIs, I don't even program anymore!" Unfortunately, nobody gets paid for creative
fulfillment. If more code means more bugs, the way you deliver
quality code is by delivering _less code that does more_. 

Finally, some engineering departments, deciding "enough is enough," have moved to languages that specifically
avoid certain sorts of bugs. The system language Rust eliminates a whole host of memory problems. Functional
languages are "buzzy" because their stateless designs eliminate variable aliasing problems and make impossible
many of the locking errors associated with multithreaded code. Some functional languages like
Scala and OCaml/F# enforce strict typing for higher quality. The challenge is actually
learning such languages well enough to avoid putting in different sorts of bugs! Unfortunately, such languages
are more well-loved than used, and openings are rare, particularly for the eager-to-learn inexperienced developer.
Best to learn to love your language by learning to use it well.
