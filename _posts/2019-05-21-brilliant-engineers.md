---
title: The Trouble with Brilliant Engineers
---

# The Trouble with Brilliant Engineers
Have you been trying to get continuous integration running in your
company, or continuous deployments? Have you tried upgrading your
forensic tools to make it quicker to find bugs? Upgrade the team's
development tools? Do you have a team of good engineers - possibly
great or brilliant - but for some reason these initiatives never catch
fire? In spite of making obvious recommendations and steady improvements?

The problem may be: you may have an influential engineers who is just
_too good_.

I've worked in several jobs, in a variety of environments. Some were
then-desireable Fortune 500 companies; others were scrappy startups or
research labs. They were all engineering teams that I would say were
"good" or better. Now, in some of these organizations, not everyone
could've worked at Google; quality definitely varied, depending on the
company. But the teams were solid, with all but one or two engineers being very good - eager to improve, eager to learn, reasonably easy to
manage. No miracles, but this is work.

Except for the current job. Here, the people seem to be uniformly
good, and occasionally brilliant. Most engineers could probably work
for a Google or a Facebook if they did the proper prepping, and even
the rest are no slouches.

So you'd think that working with uniformly bright people would be a
dream. An unalloyed good with no drawbacks. Well, I believe I've found
one.

The past couple jobs I've had, I've pulled the unenviable duty of
being "the process guy." The person who has to re-engineer the build
system, or map out the support operations flowchart, or figure out how
to simplify the test environment so the automated tests don't fail a
different bizarre way every time you run them. I often get upset about
the state of documentation too, as that is something that impacts me
more than most people, since I frequently get bounced from project to
project depending on what is causing the most trouble (no, they tend
to stick me on the _more_ troublesome projects to bring them in line,
but thanks for asking), and I also have the long-term memory of a
goldfish. So sometimes I have to be the one to tie up loose ends in
process and documentation, if for no other reason than I'm the one
that is impacted the most. I have no love for "process" jobs, which
are many times rightfully not considered "real work."  Unfortunately,
because I get visibly irritated by these "process problems," the
various other middle managers or CTOs have figured they can leverage
my irritation my telling me to please fix whatever's bothering me and
slowing everything else down too. So I do it.

When I go off on these little projects to improve process (which are
completely in addition to my _real job_, of course), people tend to react
differently. Good engineers generally know what I'm aiming for before
I even propose it, respect what I'm doing, and offer help when they
can. If I have a team of solid engineers helping me, all I have to do
is map out a direction and the team helps direct and implement it
organically - I do practically no work other than coaching and my
share of the work. When done, it's "the team's" improvements, not
mine, and at completion we have a repeatable build, or reliable rollout,
or can retire the old manual regression suite. On the other hand,
marginal engineers generally grumble, because they hate changing their
slow-as-molasses processes, but they go along with it. They may even
start hitting their dates for a change, once the improvements are in
place.

The problem is the brilliant engineers.

I have to confess I'm probably not a "brilliant engineer." My grades
and other credentials indeed tell me I'm _very smart_, and I've
produced a solid track record as senior engineer and team lead over,
say, fifteen years. But I started out pretty poorly. And good as I may
think I am now, I still doubt my co-workers think of me as
"brilliant," the sort of guy who's destined to found the technology
behind a billion dollar startup or invent the next open-source
framework used by thousands of enterprises. Particularly since I have
had plenty of years to demonstrate those qualities, were they latent
within me. I'm solid, and let's just leave it at that.

Well, here I come with a mapped out process, for doing
whatever-it-is-I'm-doing, and I need to get the brilliant engineer on
board. What do you think he says?

"Oh yes, a build pipeline for the department, that's a good idea! Ah,
but you see, I already have my own build process, it pulls everything
out from git, and dpkg'es it and deploys it throughout the system. I
bet you can use it... oh, but it only runs on my Apple. Oh, and I see,
you're using Jenkins... yes, but that's too heavyweight for me."

"Yes documentation is good, but the problem is it gets out of date,
you see. I've found the only way to do this is to read the code. No,
you can't rely on those comments, you have to look at the code and
understand it."

"No, the current diagnostic system seems fine, I don't know why people
can't just read the logs. Whenever there's a failure, I know _exactly_
what needs to be fixed by looking at the logs."

"Debugging tools? Some people need it, as a crutch. I've never found
the need for such things."

"I realize these c++ dependencies make everything slow, but I've nver
found it to impact my productivity. I just go work on something else,
and forty minutes later it's done. Of course, some people are careless
and have to compile again and again [_at this point, your humble
blogger starts to feel a little accused_], but I don't think it's worth
spending days improving."

In short, every idea proposed by myself, even the by-the-books ideas,
are seen as unnecessary. Not wrong, but unnecessary. The problem is,
the brilliant engineer is right. He doesn't need any of this stuff!
After all, he's the sort of guy who always knows all the ridiculous
the ins and outs of git, even though he's the _one_ person I would
trust to not use source control.

Oh, brilliant engineers have their own toolings and improvements of
course, but they tend to be seriously under-leveraged by the rest of
the group. Usually process toolin is the only sandbox they get to play with,
so their implementation is the technical equivalent of classical Greek:
a build tool using Scala/SBT even though none else on the group has used
anything but Java 8 in the past 10 years; test drivers written in
OCaml for defect injection that are impressive as heck but only
sort-of work; comprehensive linters built in half a day with a
combination of perl and awk that produce tons of warnings but "don't
worry, I know exactly which ones to ignore, it isn't worth spending
two hours on cleaning that up."

I'm not sure my experience is unique. I talked with a colleague of
someone who actually worked at Google for some time. He said that, far
from having the most productive tool stack ever, in many cases Google's
development tooling was behind even ordinary companies. Some of this was no
doubt due to expectations; Google has a lot of legacy, meaning plenty
of [dark matter]() engineers, and there's no reason to expect they'll
have any less than any other large successful busines whose main
product is over fifteen years old. But part of it, he conjectured, is
the fact they have so many bright people over there. Poor tooling
doesn't slow them down as much as it would for other engineers, and
when frustrated, people blame themselves for not keeping up with their
colleagues, instead of saying there's a problem holding them (and
everybody else) back.

But unforunately, everyone else on your team needs these tool, they need
them to be reliable, and need them to be usable by mere mortals. So as
a manager or technical lead, you have two choices:

1. Optimize around brilliant engineer
2. Go ahead and do your improvements anyway, and hope brilliant
engineer doesn't get too miffed at your "waste of time."

In my career, I've always done #2. Why? It's because of two things:
brilliant engineers tend to get hired away, and if you're fortunate
enough that they stick around, eventually brilliant engineer will make
use of your efforts, more than he or she will care to admit.

But really, the problem isn't brilliant engineers; it's the
second-order effect. And what is that second-order effect? It's the
fact _everyone else_ knows that brilliant engineer is doing great
without those tools. The reaction is that when it comes time to think
of improvements, everyone clams up because they think - "Maybe the
reason I need these tools _is_ because I'm too mistake prone. I just
have to 'be careful' and be better at my job." Indeed, because
brilliant engineer is so effective, it may not even occur to them that
their problem is their tooling, not themselves. Or possibly, "Great
engineers have great tools, I should create _my own_ tools. After all,
that's what the real hot shot engineers do." Or they'll go off and
learn the weird language brilliant engineer used in his tools, hoping
that maybe they can gain those superpowers and maybe put it on their
resume too.

Well, yes, all well and good, but these attitudes keep the group from
working together. The truth is, you will run into few of these
brilliant engineers in your life, and your goal is to optimize
everyone's performance, not just theirs. Sure, everyone will tell you
to cull out the nonperformers, and there's something to that advice
(though honestly, if you work in a good company, there simply isn't
that much incompetence; frequently, it's just bad management inducing
bad performance). Instead, this means optimizing the performance of
those that are merely very good. That may mean getting them on your
side with improvements - all the while knowing that you aren't the
brilliant engineer, and you'll have to do something different to keep
him or her happy.
