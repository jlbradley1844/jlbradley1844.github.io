---
title: The Personal Project Doom Loop
---

About a month ago, I laid to rest a parfectly good personal project. I
spent some time in denial thinking I just had other things to do, but
I know I probably won't revisit it for a while.

Although everything was well thought out, this project, like all
personal projects, seemed to die a horrible death. Not because it had
gone bad, but because I had simply given up heart. Given that this has
happened several times before, it's worth analyzing why it keeps
happening on my personal projects. This is particularly frustrating
because I'm a senior engineer. People give me critical projects
because they know _I will deliver_. I will ensure the code gets done
and is clean and tested, I will plan properly, I will properly
document and communicate with stakeholders - the whole mess. Yet in my
personal projects, done for fun on my own time, at the finish line I
usually have nothing but an uncompileable lump of sad that I'm ashamed
to push up to GitHub.

Why is that? Well...

This particular project fell victim to "*the personal project doom
loop*." This blog post is a postmortem dedicated to this particular
example, and an attempt to learn for my mistake - and publicly
humiliate myself as penance.

In hindsight, the root
cause for its death, and probably all my failed prior personal
projects, is the death-by-thousand-cuts caused by unnecessary
risks. Unfortunately, unlike many other personal projects, this one
was different: I had a real, feasible goal, the product would've been
useful, and it would have been a real service to others, who would
have benefitted from its completion. Yet I still loaded it up with
other challenges which could most kindly be phrased as "research items."

The project was: A search engine for searching religious texts.

That's it. Straightforward, eh?

The goal was to replace a venerable program I have called Ocean. This
program is a Baha'i-produced program which useful, available, and free
[and available here](http://bahai-education.org/). Ocean indexes a
number of religious texts, across many relgions, making it ideal for
my own research and anyone interested in comparitive religions. The program is
impressive as heck, and the price is right. But it has its
limitations. First, this is someone else's personal project, and in spite
of it being a _successful_ project, is generally the recipient of
inconsistent effort. Additionally, it does "string search" matches,
requiring usually a dozen searches to hit just the right term. It is
evident that the writer spent most of the development on the user
interfaces and collection and collation of texts - important
points. But I figured my angle would be to improve the search itself.

Fortunately, I knew Python, and libraries like
[Spacy](https://spacy.io) have made it much easeir to do natural
language processing (NLP). I could focus on sophisticated search now,
and work on UI and text later. The search portion seemed trivial at
the outset: read in a
library of documents, use the parser and stemmer, use the
sophisticated search language, and write an API wrapper to make this
available to the UI as a sophisticated search engine. Easy, right?

Not to happen. Instead, it wound up in the personal project doom loop.

The reason I call it a doom loop is because this is the trap where you
endlessly iterate, one roadblock after another after another, without
actually converging on project completion. Visible progress is
followed by roadblocks and setbacks that obviate all work to that
point. The reason this happens is that because, knowing it is a
personal project and I'm doing it for _education_, I make all sorts of
tradeoffs that would be unrealistic in my day job. This both in the
name of learing new stuff and, ironically saving time. As a result, I
loop around running into one roadblock after another, never actually
achieving closure. The more I work, the more unachievable the goal
becomes.

So, on to the postmortem. Here's the rough sequence of highlighted
actions, going back over a year and a half. Worse yet, this isn't the
whole thing, just the most "epic fail" elements. The problem
practically diagnoses itself:

1. Get an idea for a personal project. Unlike other ideas I have
(i.e., bad), this one is realistic and doable in a reasonable
timeframe.

2. Pick the language which is going to be.... Scala! Yes, that's
right. I don't know Scala, but a small group at work is using Scala
and that's interesting and cool and Functional and so productive so
let's try doing that.

3. Set up a VM for scala. Of course I have to have a VM for my
development, you don't expect me to just bare-metal this on my PC, do
you? I mean, that's what I do at work, but...

4. Oh, someone at work was telling me I should be using
Vagrant. Great, I'll be able to program my own configuration. Vagrant
it is! And it shouldn't be too much trouble to use.

5. Ok that took a while, I made that more complex than it should've
been, but finally a VM I can use! Oh wait... scala Emacs mode isn't
working.

6. Well, scala emacs mode turned out to be real screwey and not at all
easy to install, but I finally got all this stuff working, and Vagrant isn't
completely automated, but it's sort of where I need to go. Onto my
project! I just need to... pick an NLP library.

7. Uh oh. No good NLP libraries, they all seem to be Python
nowadays. Also, tried to do a few toy programs in Scala. This is
hard. I don't get any traction learning the language until buying my
third text. (BTW Recommendation: Horstmann's [_Scala for the
Impatient_, 2nd edition](http://horstmann.com/scala/index.html).)

8. Screw it. Six months I've made no progress. Python it is! At least
it has NLP libraries.

8. Ooooo look the [Pivotal Tech
Radar](https://www.thoughtworks.com/radar) (now ThoughtWorks) is out
now, all these cool technologies. [This one called
spaCy](https://spacy.io) looks interesting, and seems more lightweight
than the others. Let's run with that.

10. Oh, now I have to set up Vagrant boxes that I can run python
on. Ok, better go do that. Ok, so.... Ubuntu, check. Python, check. Emacs and
IPython, check. Finally ready to code!

11. CODING FINALLY WOOOOOOOO. (Picture hollywood montage of your
humble author crouched over a computer, his face bathed with blue light...)

12. Uh oh, I was reading a bad version of the API. For certain
critical elements, I need to use spaCy v2.0 to do the sort of searches
I want. But to do that, I need a new version of Python... but the
vagrant box I want doesn't use compatible libraries...

13. Rebuild more vagrant boxes

14. Oh geez I have a bunch of stuff to recode because I moved from
Python 2 to 3.

15. CODING FINALLY WOOOOOO

16. First practical code and it CRASHES. Out of memory. Looks like
spaCy can't handle book-size documents. But if it can't handle these
documents, and if it takes several seconds to parse chapter-size
documents, and if I have thousands of those...

17. Posted requests for assistance on both spaCy forum and relevant
Stack Overflow forums. Nothing but crickets. Meanwhile, memory
monitoring indicates I'm probably off by an order of magnitude with
these scaling requirements. Uh oh.

18. Redesign... I don't think NLP libraries is the way to go. At first
I avoided Solr because it only does brute-force string searches, but
apparently it has a "stemmer" add on that can do the sorts of flexible
matching I needed. Maybe I can go that direction.

19. But that requires a recode.

20. Read up on Solr... right?

Wrong. Because that's the point where I gave up and went onto
something else. About a month or to ago. Even if I take up the
challenge again, there is very little usable code to migrate over to a
solr-based solution. So I'll be starting almost from scratch.

It's pretty evident where I went wrong. I didn't need to learn Scala,
I didn't need to learn Vagrant, I didn't need to fiddle with a process
for making immutable dev boxes, I didn't need to migrate to the
latest, hottest NLP library, indeed, I didn't need to use NLP, truth
be told... all these things I didn't have to do. And I wouldn't have
done it at work. I would've made a lot more practical tradeoffs.

But somehow,
because this was a personal project, I convinced myself all these risks
were worth it, and "at least I have fun." Except, the things I learned
aren't applicable to work, and... it wasn't really fun.

As an aside, I had thought of giving "the Doom Loop" a different name of "Bryan Cranston Sydrome," after this classic scene:
["Malcom in Middle", light bulb changing][https://www.youtube.com/watch?v=AbSehcT19u0 "The Classic Light-Bulb Changing Scene"]

--------------------------

This is the point in my essay where I'd normally say HERE'S HOW I
SOLVED IT AND YOU CAN TOO. But unfortunately I can't do that; I have
to write up these lessons when they're fresh in my mind. Meaning I'm writing this before I have an answer.

But what I do notice is that in my personal projects, I seem to
jettison some habits that are second nature to me at work. Why?
Because I care if I fail at work. And perhaps its ok if three quarters
of these toy projects die horribly after a few months. But better if I
have a few successes.

So here's what I vow to do in the future. In a sense, make it more
like work. Basically, like work if I didn't have to worry about the business.

* Any personal project should involve at most two technologies I'm
  unfamilair with, in the broadest sense. For the search engine, that
  realistically means the NLP library and Python 3; everything else
  the same as at work. In other words, don't compound it by trying to
  learn Chef in the critical path of deploying your technology, pick
  up VS Code instead of emacs just to try that out, etc. If I'm
  learning a new computere language and a new IDE, then that's it - no
  other new technologies for that project!

* For new technologies - and let's face it, personal projects are all
  about the new technologies - do a quick pilot of the risk
  elements. In the above case, I knew I was going to operate on dozens
  of book-length documents; surely I could've spent some time early in
  the project to find out if spaCy was going to choke on book-length
  documents, rather than just presuming "oh, it says it's
  production-ready, I'm sure it can halde it!"

* Remember that in a personal project, you're on your own. Personal
  elements are thought to be more conducive to exploring new
  technologies - because, hey, nobody's watching you. But at work
  there are generally other experts to lean on. And at work, if you get stuck
  for a few days on an open-source project, you can afford to sink a few
  days to get to the bottom of things. But on your personal project, every
  hour counts, and being stuck for several hours can easily turn into no
  visible progress for two weeks.

* "Plans are worthess, but planning is everything." As a Baha'i,
  perhaps it is incongruent to live by the dictates of a military
  general, but Dwight Eisenhower was dead right on this one. Planning -
  the exploration of risks and contingencies - is an essential
  element in anything you take seriously; and you should take perosnal
  projects seriously. At first, it sounds like a plan is pointless,
  since your plan is just a loose purpose to learn something and maybe
  have something when you're done. However, the second you want to
  have something to show for your efforts, then risks, contingencies
  and dependencies all become important. The fact you have so little
  time to spend on personal projects make planning more important, not
  less.

Want to comment? Would love to hear your comments! Except I have to
add a discourse link. Except I don't know about how to do that in
GitHub Pages. Maybe I need to learn jekyll better. Oh but once I do
that, I need to refactor these posts, I really didn't like the way I
did that. So to do that I'll need to learn Liquid, the layout
engine. Oh and I have to worry about authentication and
spamming. There's supposed to be this great other plug-in that handles
that, but not sure it works with the version of Jekyll on GitHub
pages, maybe I need to move this blog to another site...
