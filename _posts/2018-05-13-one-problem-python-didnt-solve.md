---
title: Python Programming and Recruiting
---

# Python Programming and Recruiting

## Or: One Problem Python Doesn't Solve

_In which we revisit a recurring series of rants in which I am once again
tasked with the perennial unsolvable problem of "why can't we find
good engineering talent."_

One of the unusual aspects of software development as a career is
that, in general, things actually get more pleasant over the span of
one's career. When I went into the field, C++ was a luxury reserved
for the lucky; most people worked on C projects, with a few
lucky/unlucky few still doing assembler for certain parts. Projects
themselves were generally organized as "waterfall" projects taking
several months. If your team had a "daily build" it was one of a lucky
few; if the "integration phase" of development took less than two
weeks you were unbelievably blessed, and most projects were late by
six months the second you began coding. What was a luxury then is
table stakes now, and if you're on a C++ project, even if you have a
CI build with daily deployments, you're on two week sprints for
delivery targets, leaving you envying the developers
on C# and Node.js who are used to pushing out code that much faster.

And one of the most pleasing developments over my career is the
current near-ubiquity of Python. At our firm we've gotten to the point
that Python is the preferred language for all new development. On
paper, moving to Python is an enormous win, effort-wise: one can code
in minutes what would take an hour in a C++ program. To be fair to
C++, we're not talking an order-of-magnitude improvement in
development speed. Speedier coding isn't going to magically solve the
difficult algorithm and design issues that you (hopefully) spend most
of your engineering effort on; they'll be difficult no matter what
language you use. Coming up with a disciplined packaging approach and
settling on versioning and libraries has also been a difficulty under
Python, one that is a complete non-issue in C++ (where if something
gives you difficulty, you jist fix it by shoving the code into your
binary). So while it isn't all sunshine and unicorns, my experience is
an 8-point story in in C++ usually winds up being a 3-point story in
Python. This is a pretty big win - no matter how you account for it.

When our team started moving new development to Python, we also
anticipated another area where things would improve: recruiting.

In case it isn't obvious why, let me relay my experience.  If your
firm's primary language is C++, and you aren't doing very high-paying
positions requiring high-speed logic (like, say, trading engine at
hedge funds), you'll have very tough sledding with recruting. First,
very few developers now know C++ well enough to be fluent enough to
interview. And truth be told, advertising for a C++ is a red flag to a
lot of people, much as advertising for Perl has become. A warning that
"Thar Be Legacy Dragons Here."  As a result, even the sorts of
skilled, experienced engineers who once programmed extensiviely in C++
will casually leave off C++ experience from their resume, for the same
reason I don't list my VBA experience: to avoid being recruited for
positions where they'll be working on maintaining a 10-year-old
resume-eating legacy monster system.

So with Python programming, we figured we would be looking at a
massive improvement, resume-wise. And indeed, we probably had about
five times the number of resumes getting
through. Unfortunately, the variance of the candidates varied
widely. Incredibly so.

The result: our "yield" (as far as the
number of candidates invited in) was almost identical.

One thing we did not take into account is that C++, in an of itself,
is a bit of a weed-out. If someone is gutsy enough to highlight C++ on
their resume, it's usually someone who has been coding a while. A few
weeks in an introduction-level C++ course and a quick flip through
some Scott Meyers books is enough to warn someone that bluffing
through a C++ interview is no easy task. So while we had our share of
duffers on phone interviews, at least they weren't failing
fizzbuzz. And you can generally tell within five minutes if your
candidate really knew C++ or if he or she was
just a glorified C or Java engineer who was trying to bluff their
way in.

But Python is famously easy for beginners. It has become the
overwhelming first language of choice for computer science
sequences. For many hard science and engineering fields, it has become
the only language you need
to know. And it's easy enough that many summer camps for tweens offer
Python coding for those who outgrew Scratch in grammer school.

Lower barrier of entry means more candidates, right? You know where
this is going, right? Lots of less-qualified candidates? Well we
thought of that. So we changed the requisition to be something like
"Python, plus knowledge of one object-oriented language (Java, C++)."
Certainly, that should weed out the posers, right?

Our expectation was we wouldn't have much problems then. Python has
only really gotten serious traction with enterprise-level development
in the last few years. So we figured we'd have a fair number of
candidates who used Python now and had used Java or C# in prior
positions. So we sat, and waited.

Instead, we got different sorts of posers: Java programmers who knew _a
little bit_ of Python. For my initial weed-out problem, I asked a
question which could've been solved with a list comprehension very
quickly. It took me one or two minutes myself, and being that I'd been
doing Python at most a year, I figured most of our candidates should
have no problems. The results:
- I had one candidate (1) that banged this out within 30 seconds -
about as fast as he could type this;
- Everyone else that got through the resume screen (at least ten
others) took five to ten minutes, and did it with nested loops. Some
as long as a half-hour.

So what happened?

The best as we can tell, the problem is Python is too simple to
learn, and makes it far too easy to think you're done with the
learning process.
I learned Python the way many people do - by being asked to use it in
a project. Within a day or two, I was as productive as in C++, and it
wasn't much longer until I was much more productive. Of course, *I
didn't stop learning*. I knew there was a lot more to learn.
Not so with a lot of candidates we interviewed! My guess is that most
of these "Python candidates" were really "Java candidates who
*thought* they knew enough Python to bluff their way through an
interview."

The experience reminded me of the time I had in the 
late 00's interviewing Javascript programmers. At the time our company
was an early AJAX adopter; while Node.js wasn't even out yet,
frameworks like jQuery had convinced most developers that Javascript
was a language you had to take seriously, not just some scripting
language for cobbling together an ugly solution. But our Javascript
candidates did what our Python candidates are doing now - learned just
enough of the language to get by. It seems that no matter what the
language, there is no limit of candidates eager to exaggerate their
experience and hope the interview won't catch it.

So lesson learned. Given what our experience, it seems a more
"accessible" language isn't going to help you with your hiring
problems. We have a peer group using Scala, a powerful language with
a mixed reputation as a language that is difficult to learn and even
more difficult to use well. They get a lot fewer candidates than ours,
but a lot fewer posers. Just as there is no "silver bullit"
development technology or language
that will fix your core problems, there appears to be no such language
to fix hiring problems either.