---
title: Developer Testing Part I: Testing Without Testing
---

## title: Developer Testing Part I: Testing Without Testing

... in which I attempt to summarize some thoughts I have on developer software testing from a
longtime practitioner. This is Part I on a series on software testing for software developers.

If you are a software developer, you are hopefully also a software tester. Back when I
began programming, it was not unusual to hear of companies that hired software testers as
a specific role. It sort of made sense, if you were a corporate bean-counter; software
developers are expensive, testing software is time consuming, and testing software could
be done by any moderately-skilled office worker. And so -tada- your engineering organization
had a dedicated group of modestly paid office workers doing nothing but testing.

Time has proven this organization to be ineffective. Modern software proved too complicated to
hand off to less skilled employees, who generally lacked the expertise to automate
the more common aspects of software testing. Meanwhile, many developers took it as a
license to make sloppy code, knowing that "QA" would find anything left behind; developers
would ship first and move onto the new job, leaving someone else to fix their bugs.

The organization I presently work at takes a rather different approach: software developers are
responsible for testing their own code, **period**. You write it, you ship it, and if it
croaks in production at 2:00am, you fix it. If you write garbage, you're going to pay
for your sins. Somehow, this seems to guarantee that software developers spend a
lot of time doing testing.

But the bets way to do testing is to not do it if you don't have to! Remember, when
you write test code, you're writing code that will never ship! Aside from getting rid
of bugs, the test code you write is useless. So if you can eliminate bugs before you even
run your code, do that. So in Part I of this series, I'll tell you how to avoid testing. 

### Strict Type Systems

When python caught on as a serious server-side language, many serious programmers were aghast.
Most had spent years outside of the university, where the last serious
interpreted language they learned was LISP, and most commercial interpreted languages
were horrid dialects like VBScript and Javascript, poorly-design monstronsities that
were barely tolerated by engineers and that nobody attempted to do 
enterprise-level coding with. Python, unfortunately for them, was not
so easy to laugh off. It's simple, uniform design and easily-learned syntax helped
quickly embed it universities, and from there it became an irreplaceable language for
data analysis and machine learning. Serious programmers found themselves having to
work in an interpreted languge and go without a *drumroll* compiler!

Yes, programmers actually missed compiling! Pure-play python programmers reveled in
the lack of compiler, but old C++ programmers knew better - the mere fact of having
a compiler enforces a raft of checks of code validity, checks that otherwise have
to be made through unit testing.

But the fact is, you don't need a compiler to check your code, and even if you have
a compiler, you may not be getting the code checking you need. To this end, it is
necessary to introduce: _strict type systems_. A whole host of problems can be 
eliminated by using strict typing. 

Some of you will get this for free in your language of choice, but most languages
won't keep it strict enough for you. You C++ coders are used to casting objects
willy-nilly; those of you working in Java and C# all know how about putting things
in Object containers; it seems every language has a hole. If you work in Python or
Javascript, you can get typed extensions through PEP and Typescript respectively,
but those won't enforce it. That's because strict typing is an _approach to programming_
more often that in is a feature of your language.





### Design By Contract

Design by contract is an old concept that traces back to a language called Eiffel.
This concept is much written about in software engineering circles. My experience
is that I've never met a single persion who has worked with Eiffel, and I have
rarely seen design by contract used.

But that doesn't mean the idea is a bad one. The idea of design by contract is that 
for each subroutine/method/function/whatever, you have three things:

1. Preconditions
2. Postconditions
3. Invariants

These are exactly what you think. There are design-by-contract frameworks around;
I've never seen any used, and that's probably because a) assertions work just fine
and b) you rarely need to deal with all three. For instance, in a good object-oriented
design, you rarely have preconditions. The most common precondition I've seen
is "don't call this method until you call a special setup method" and the reason
it's rarely noted in the comments is because any programmer who did this is
rightly afraid his code won't make it past review - because this is bad object
oriented design. Preconditions are usually a code smell, except perhpaps to
indicate that your arguments don't need validation.

Which gets to the main point - if there is a problem, it's that in most bad
code, _nobody ever thought about a contract_. It was done to just enough to
get the code out of the door. That's not a problem; the problem is if you do
just enough to get the code out the door _and you don't tell anyone else_. A
code contract, even if it exists only in comments, is invaluable to tell
future maintainers just what is supposed to happen and not happen in the code.
And if you're one of those people who has a philosophical aversion to writing
code comments because they fall out of date (admit it, you just don't like
writing), assertions are more than enough.

When to use them? The answer is the bothersome _it depends_. But what it depends
on depends on the answers to some questions:

Q1: Where do you do validation? You don't want to wastefully daisy-chain validation
throughout your coding call stack. Presuming you have a well-defined set of entry
points into your service or library, you must validate your data at the entry
point and then subsequent validation makes little sense.

Q2: Did you embed a state machine in your class? Some classes are brittle,
state-specific creaters where APIs must be called a certain way lest undefined
behaviors occur. This is always a horrible idea, but sometimes this is required
because you're wrapping something even more horrible.

The above are perfect uses for preconditions.

Q3: Do you have method calls and want to ensure there are no unexpected side-effects?
For many of your method calls, you will not change state, and if you're a c++
or java-style programmer, you'll want to use the 'const' modifier to ensure
your code cannot be changed. Your compiler will make sure you don't accidentally
bungle something. But there are some cases where you want to make sure some things
don't change. Anything like that?

This calls for an invariant.

Q4: It's generally good practice, in your methods, to _either_ return a value, or
to change the state of the object, but not do both. I'm not talking about the case
where a value is returned, but it's just a return code; I'm referring to something
where the purpose of the call is to get the data you want. Indeed, you could even
make it a const.

I'm guessing you don't have this consistently, do you? Well, in this condition,
you can use a postcondition. You've changed the state, so the postcondition can
test it. Better yet, you can 



## Static Code Analysis



## And A More Complicated Feature: DSLs/Metaprogramming


Conclusion: Unit Test only what you cannot cover above.
