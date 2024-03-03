---
titles: Correctives for Your Unit Tests
---

## Correcting Your Unit Tests - Common Issues
I have been _attempting_ unit tests ever since they were pushed at me in the mid-naughties,
long before they became _de rigeur_ with the agile crowd.
But in spite of the fact that even students coming out of the college know how to do themi nowadays,
many developers don't do them, or do them wrong. I did it wrong for years.
It probably took me eight years of trial and error to do it right.

Those of you who are doing it right probably know you are - because your unit tests are useful,
speed coding, and improve your quality. If any one of these things missing, or if you have
decided they aren't worth the effort, then it's probably because you're missing a few
critical things, things their proponents never pointed out properly.

_The "Real World" Isn't a Toy:_ Books and blog posts that illustrate unit testing don't do their
readers any favors by showing unit-testing done on toy examples with no dependencies. That sort
of coding I've seen in very few places: perhaps low-level library coding and interview questions. Every place
else, you have dependencies to deal with and APIs that must be called. In many cases you're having
to do your fix in the middle of a much larger environment with no tests. Toy examples won't help.

**Why TDD Goes With Unit Tests:** One reason test-driven development is important, then, is because
unit tests are just so hard to do if your code is already written. Probably, the first time someone introduced
you to unit tests, you had an already-written piece of code you needed to retrofit. Retrofitting involves these common
nightmares:
* Dependencies: You'll have tons of APIs you haven't stubbed
* Class creation: You'll be instantiating concrete classes directly, with no way to inject mocks
* Hidden state: You could wind up with a class that accidentally or not, embeds a complex "state machine" within, requiring a ridiculous amount of setup to exercise the logic fully
* Untestable error clauses: due to inability to actually exercise the included states.

Given that most people asked to add unit tests are working with an existing code base, it's no wonder
more experienced developers say unit tests aren't worth it. And it's no wonder that the unit testing books
show how to do it using toy examples than anything practical.

While there are ways to address all of these these problems - seams for APIs, the addition of IOC construction for
class creators, utilities for API stubbing (including even monkeypatching and link-time interception),
they require both effort, time and creativity. Sometimes, a unit test isn't the way to go.
If the work you're doing to get your old legacy code testable seems like a waste, listen to your gut.
It's probably because it is.

Things are a little better if you are
adding tests for brand new, already-written code, but you'll still find yourself redoing a lot of work you just did. It
just isn't practical.

Unfortunately, the only _practical_ way to do unit tests is to write them _at the same time as the
code it is meant to test_. This doesn't necessarily mean "write all the tests first." What it does
mean is that if you are writing code, and you find something that makes your code hard to unit test,
you may need to make your code more testable. It may even make your design better - something that
will likely not happen if you have to retrofit existing code with unit tests.

That won't help those of you with legacy code; if thats you, keep reading.

**What not to Unit Test:** Another reason I see for people failing with their tests is they test code which really has
very little likelihood of having actual bugs a unit test can catch. Let's take a realistic example:
a 20-line routine consisting of nothing but API setup and outbound API calls, which returns a callback routine.
No if clauses, no loops, nothing.

You will benefit very little from unit-testing such a piece of code! Should you decided to unit test,
the unit test will actually test
a) the mocks you wrote to allow you to test the code and b) the unit test itself. You will not
test the code at all.

One of the ironies here is that this is actually a good, modular way to write code! If you're like
me, then the entry point of your APIs or service consists of some preprocessing and postprocessing
(such as a de-/serialization), a try/catch handler, and within that try/catch handler, the sort of "straight-line"
code I'm describing, with business logic in various handlers and other "helper code" routines. The "helper code" 
is very amenable to unit tests; the straight-line code at the top is not.

The solution is to realize not all of your code is unit-testable, and not all of your tests 
need to follow unit-test rules! If you have nothing but "glue code," then
**integration tests are the way to go**. The only way to know if your API calls will work
is, after all, to actually call those APIs. Of course, your integration test will require just as
much special handling as a unit test, such as attention to statelessness, reproducibility, and proper
setup.

If you have an old legacy piece of code, this is actually your solution, as painful as it is.
Unit test new pieces of code as you write them; everything else must be integration tested.

Some engineering firms, rather than focus on unit tests, instead make a distinction between "short" and "long"
tests. The "short" tests are run like unit tests, but need not follow all the rules of unit testing!
Instead they simply need to run quickly. This may mean running under special test environments, using
techniques like in-memory databases instead of the real thing, and locally-hosted service stubs developed
entirely for such testing purposes. These will actually catch bugs, which are likely to be in the integration
itself, not the straight-line coding.

**Avoiding nondeterminism in your code:** Another problem people run into (and this is in testing in
general) is doing things in the code that render the code trace nonreproducible.

The most obvious problems I've seen here are:
* Date/time functions like `now()` that always deliver the current date/time
* Random number generation
* Access of program environment information, such as the user ID or host name
* "Session" information that contains useful data, but is never the same from one test to the next.

This sort of thing is done so commonly that it's easy to overlook, and it doesn't _seem_ nondeterministic;
at least, not the way that a multithreaded piece of code does. But all of the above are sources of nondeterminism;
change where the code is run, when it run or who runs it and the code changes. And sometimes the
developers themselves, not realizing it, attempt to work around the problem.

The solution here is to take the determinism out of the code! Date information and random numbers can
be passed in; seeds for random numbers ca be passed in; environment information can be passed in or
supplied through a test harness where you can control all inputs.

Thanks for reading, and I hope that helps!
