---
title: Team Awesome vs. Team Sad in Tech
---

# The Team Awesome / Team Sad Split in Tech

We are coming into a tight job market in tech; one in which it is hard
to find good engineers, and hard to retain those you do hire.

This is not news. What is news is I still run into people from "the
business side" or middle management who a) believe it is news and b)
want to know how they can fix it and when it will go away. Rather than
write a long analysis on this, I'll just give you the tl;dr on it
which is that it won't go away, ever.

I'm writing this for engineering managers or tech leads, who know that
this has been true, since, well, forever. A lot of people on "the
business end" do not understand this, as the outsourcing binge of the
late nineties followed by the great recession of the late 2000s lulled
a lot of them into thinking that slack labor markets are _normal_, and
that salary inflation for professionals and job-hopping is unnatural
and some sort of violation of market principles. Hopefully you don't
have to work for such people; if you do, you probably have one foot
out the door, because that attitude is usually a red flag indicating
they still view tech staffing as a "cost center" which does nothing
but bleed the business.

But let's suppose you recognize that hiring and retention are tough,
and your superiors both realize this and appreciate your committment
to build a strong engineering organization. You can still do things
that torpedo retention and hiring, even with business support.

-----------------------------

One common antipattern I've seen is the "Team Awesome" / "Team Sad"
split. I've seen it in every engineering organization of more than a
dozen engineers, and it's prevelant enough that I'd like to stop it. If you're
an engineering manager, you'd probably want to stop it too, since it
is one of the biggest retention threats you'll have.

Here's what it looks like: you will have some group inside the company
- let's call it Team Awesome. They always seem to draw their new hires
from "the best and the brightest"; they always work with the latest
technologies; their stuff always involved in a hot new
field. Sometimes Team Awesome is an entire company division, where
they do "research," leaving the rest of the organization to do
"development" (which usually means a lead time of less than three
weeks). But usually Team Awesome is a particular peer department or
organization in an engineering division. You can tell Team Awesome out
because they always seems graced by enlightened HR practices and
blessed by bloated budgets. What are they working on?  Usually the
latest and greatest. Team Awesome always gets to attend the latest
conferences, on the company dime Sometimes they work on
successful products, but more often than not, their products are not
successful - at least, not _yet_. An air of cutting edge success hangs
around the team, and everyone in the company wants to transfer onto
Team Awesome.

Then you have Team Sad. They seem to be composed entirely of people
who wanted to be on Team Awesome, but aren't. They work with old
technologies. They are always overworked and nobody leaves before
7:00PM. Management may claim this is because the old technologies make
it hard to hire for. However, frequently this is usually a cover, as
Team Sad, unlike Team Awesome, always seems to have a shrunking
budget, so they are always told to "do more with less." Unlike Team
Awesome, Team Sad seems to always be in "code and fix" mode. Their
continuous deployment pipeline is in a constant state of brokenness
here or there; automated regression tests are a dream, and their
deployments are white-knuckle nightmares due to inadequate testing and
poor process. The codebase is a mess of steaming legacy, and nobody
has done either refactoring or greenfield development in years, so
every additional fix makes the codebase less maintainable. Unlike Team
Awesome, nobody on Team Sad gets reimbursed for attending conferences
or professional development events because the expense isn't
"justifiable to the business," since Team Sad is working with old
technology, though usually you'll find the most dedicated engineers
will do their best to keep up.

Here's the irony: Team Sad is usually the one owning the most
successful products in the company. This is not lost on Team Sad,
whose engineers generally view themselves as getting the short end of
stick - the smallest budget, the worst tools, the least capable
managers, the most unenviable technologies.  So you can guess what
happens to Team Sad. Team Sad, in spite of being responsible for much
of the revenue at that company, is full of unhappy, jealous employees
eager to ditch their no-win roles at the first opportunity. Those that
remain are fearful of their careers; each succeeding year their skills
get less valuable in the marketplace. To add insult to injury,
companies will "solve" retention problems by making it extremely
difficult to transfer to a role out of Team Sad. As a result, Team Sad
members will look for opportunities outside the company. This is not a
surprise.

What is a surprise is what happens to Team Awesome. It usually goes
like gangbusters, working on loads of blue-sky projects that always
seem to go the right direction. The are successful on paper - if not
always in the marketplace. However, all good things must come to
an end. Perhaps their product becomes successful, and they are told to
redirect to support. Perhaps their product is not successful, and
budgets are cut. Perhaps just the threat of less promising days is
enough to frighten them with visions of their own team turning into
"Team Sad." In any event, the end is swift - at the hint of any
unsteadiness in corporate committment, first a few, then several of
the "best and brightest" start fielding their resumes. Before you know
it, half of the team is gone. So much for Team Awesome. They are out
the door, with nothing left but a steaming pile of legacy. To be
picked up by those remaining at Team Sad.

---------------------------

So how did this happen? The surprising thing is, it usually
happens on purpose. And usually with the best intentions.

In the beginning there was: a successful technology product. This produce
was either successful in the marketplace, or it's used internally and
is now business critical. And Lo, the Engineers creating said product
were Respected. Having become successful, users want more and more
features, and complain about more and more bugs. Meanwhile, retention
is becoming a problem, as engineers start complaining about working on
"legacy product" with outdated technologies that make it hard to stay
"up to date" in the tech field. Hiring, meanwhile, is starting to
reflect that as well, as it becomes difficult to entice people into
working with older technologies. Middle and upper management, who
would rather be doing other things, have to direct their focus to
figuring out some sort of solution for the hiring and retention
problems they keep hearing about from their engineers.

The solution is a common one: aided and abetted by engineers who are
tired of working on legacy, the middle managers will create: "Team
Awesome." They don't set out to do this intentionally, but if you look
at the reorg powerpoints, that's exactly what it looks like.  Team
Awesome is a new team that is going to fix the technology problems of
the legacy system. Perhaps they're going to design a next-generation
replacement of it; perhaps it's for a new product that will make the
old one obsolete; perhaps this is a new line of business. Anway, Team
Awesome is geared to retain your best and brightest, and you find that
Team Awesome is much easier to staff up and retain; indeed, you're
luring the sort of people in that might work for the "big 5" tech
firms. Awesome, indeed! The company's future is hitched on Team
Awesome, and things are awesomer than sunshine and kittens.

But engineers will also see something middle management is too
oblivious to see: their career as an engineer depends on getting on
Team Awesome.

Much is written about what motivates engineers - working with
up-to-date technology and hot fields. The people who do this writing
are frequently HR types who have noted that the motivators for
software developers are quite different, but they seem to have no idea
what might be behind this difference! Frequently the writers express bemusement,
because it doesn't work this way in their own fields - "oh, how geeky,
they are so passionate about their TECH!" No, they are not passionate
about their tech (ok, maybe just a little). They are passionate about
CAREER SURVIVAL. Because the same HR types that don't understand why
engineers are motivated by working with new technologies are the same
ones who profess complaints like "We can't find any
engineers who are versed in hot technologies!", all the while
carefully planning the next layoff of engineers with justifications
like "These older engineers are expensive and their skills are out of
date!"

If you create a Team Awesome that gets to work with the latest stuff,
and shunted the unpleasant work to other teams, what you are doing is
creating an Opportunity Shortage. Engineers now have two distinct career
paths in the company: work on Team Awesome and advance your
careers, or don't work on Team Awesome and be slowly left behind. Team
Awesome will see staffing increases; everyone else will see
layoffs. As a result, all of your best, most ambitious engineers will
try to get on Team Awesome. These are the people who will move ahead
in their careers. Who doesn't want to move to Team Awesome? Only the
least ambitious and least capable. Staffing problems are an inevitable
result, as what was a bad recuriting situation now becomes even worse,
as new employees not on Team Awesome tire of working on the "B Team."

Now those not on Team Awesome are on a new team: Team Sad. Their
assignments are both less challenging and more vexing, as their work
becomes more restricted to maintenance and "urgent" issues (note irony
quotes).

You'll know when things have come to a pass that cannot be
resolved. Eventually, middle management, tired of seeing constant
jockying for internal transfers, takes measures to make internal moves
much more difficult. Basically, freezing all engineers in place and
barring internal hiring. This is meant to "fix" the situation. Instead,
the most capable engineers will leave. Then you really _will_ have a
situation where your entire maintenance engineering staff are duffers
who can be replaced with an Indian outsourcing firm.

By creating a Team Awesome to fix your hiring and retention problems,
you have two teams with horrendous retention problems. Now, if your
goal all along was to replace your whole engineering staff with an
Indian outsourcing firm, congratulations. Team Sad is now so incapable
as to be indistinguishable from an Indian outsourcing firm, and Team
Awesome, if left alone, will disappear as soon as you fix the blinking
light on the laser printer, thereby allowing the last resume in the queue to be
printed. Mission accomplished!

---------------------------

But most of you don't want that. However, if you're reading this, you
are either an engineer or a low-level engineering manager. What can
you do to prevent this in your organization?

I'd like to present a set of tested, foolproof guidelines to prevent
it. Unfortunately, I can't. What I can present instead is wild-@ssed
speculation in the guise of time tested wisdom and go with that. My
main hope is by seeing the problem, you have won half the battle.

As an individual contributor or manager, I can think of a few ways you
can help:

1. Everyone Works on Some New Projects. Avoid divisions between
"greenfield" and "legacy development," and avoid distinctions between
"development programmers" and "maintenance programmers." If you're
doing proper maintenance and rewrites, actual greenfield development
should be rare - most of your newest features can be based on extensions
of existing code and refactorings. And everyone must do
maintenance. Yes, maintenance stinks. But it should be recognized that
maintenance is harder than greenfield, and it should not be shunted to
"low status" departments. Just as the only way you get testable code
is to make the developers responsible for testing, the only way you
get maintainable code with proper logging, monitoring, and forensics
is to make those same developers responsible for maintenance.

2. Everyone Deserves to Do Good Engineering. This is my biggest pet
peeve. One of the things that makes Team Sad so sad is frequently they
have been told that *good engineering practices are not part of their
mandate.* Testing? Automated builds? Proper scoping and forensics?
"Why are you fiddling with that - we need features, we need bug
fixes." While this is often taken as a sign that "the bean counters"
are in charge, frequently it is the engineering managers that are
responsible for this attitude, an attitude that is frequently absorbed
by the engineers themselves, who were themselves shunted to this
department as "B Team" players. The answer? If you're in such a
department - step up. Sometimes the best leaders are arise without
being promoted to that level. If you're in middle management, realize
that there is no substitute for good leadership, and you should not
allow certain departments in your organization to be so low-status
that they languish with ineffective leadership.

3. Everybody Moves At Once. This is _not_ the same as "everyone moves
at the pace of the slowest deveoper." It behooves you to have enough
people in technical leadership positions that they can watch for
developing technologies and ensure pilots are done. Once piloted,
_everyone_, in the whole organization, should get the green light to
use the technology as appropriate. This may mean allowing people to
build infrastructure for this migration. The goal is to prevent
someone from informally designating a certain development team as "the
B Team" and saddling them as the unlucky saps prevented from ever
moving on.

And two last items for those of you in middle management or upper
management, this is for you. I can't claim any expertise in this area,
it is just a plea to be heard:

4. Just Stop It Already. Want a special team of alpha developers using
the latest tools to reinvent your core business? Please don't. The Big
Rewrite is a project that always fails. It sounds fun but [it usually
ends ugly](...). Meanwhile, those developers you wanted so badly to
retain by letting them play with the hottest technology? They'll leave
when it turns into a Death March. The only way to improve your
technology is through an incremental refresh. And speaking of which,

5. Drop "Research." Okay, there is a place for actual
research. Personally, I love working on the stuff. But the goal of
research is to move the state of the art forward, and most enterprises
have no need for this sort of research. But many insist on doing "research"
by this, I mean a special high-status division within the company
doing all sorts of neat things that nobody else gets to do. The proper
attitude to this should be that "research is everybody's job." Want to
use "research" to explore a new line of business? Great. But make it a
part of your regular developent organization. If you need outside
help, hire them and make them part of the engineering staff. Don't put
them in a separate location where they stand apart from the rest of
the organization, breeding envy during good times and resentment
during bad times.

If you care for other developers, you'll realize they all deserve to
work on Team Awesome. Make it your job to make it happen