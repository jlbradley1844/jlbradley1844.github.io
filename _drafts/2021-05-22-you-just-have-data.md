---
title: You Don't Have Big Data, You Just Have Data
category: articles
---

## You Don't Have Big Data, You Just Have Data. Or: Why Your ML Project Doesn't Work

Back again after a long hiatus. A lot of topics to address, but most
of them require more research.

Not this one. I've noticed a common mistake with ML projects.

In my firm - and in many technology firms like it - there is a lot of interest in
Machine Learning. This is for a lot of reasons:

* "Big Tech" firms like Google, Microsoft, Amazon, Baidu, you name it - have all
  had a lot of success with these technologies.

* Business analysts and commenters have breathlessly hyped Artificial Intelligence
  as the next big productivity breakthrough for businesses. Most engineers are aware
  that such articles are referring specifically to Machine Learning.

* Many technology employers have a lot of pilot projects involving ML, and employees
  working on these projects get a lot of visibility and project attention.

* Recruiters eagerly look for engineers with ML experience, and counsel anyone
  who will listen to get experience with technology to ensure their future
  employability.

* Engineers concerned about their career trajectory and eager for the inflated salaries
  some ML engineers are rumored to pull in use Machine Learning approaches even when
  they are unsuitable, a syndrome some have called "Resume-Driven Development."

* A plethora of open-source tools have made applying Machine Learning dramatically
  easier than five years ago. What was once a skill that took years to learn in
  a well-placed position can now be learned over a few dedicated weekends.

Do you know what HASN'T been the result of all these attention?

* The use of Machine Learning to rapidly bring to production projects that would have 
  been much more time time consuming otherwise.

It is now becoming apparent that ML is not a panacea for difficult projects, and
some engineers who are "ahead of the curve" are afraid of another "AI Winter" due
to the overpomise of this technology.

We've been here before, very recently in fact.
A few years ago "big data" was the hot thing for software developers to put on 
their resume. This was mainly thanks to stories and rumours of
engineers bringing in 300-400K salaries for doing what
was called "data science". Back then, a software engineering manager and myself were 
bemoaning the tendency of young engineers
to play with the latest "toys" in an attempt to better this resume in this
direction, introducing tools like Spark, Hadoop and every noSQL you can think of
in use cases where a plain unadorned relational database would have been easily
sufficient and much faster to deliver. Giving the eye-watering salaries that accompanied
those skill sets, one can hardly blame them, but it led to simple, obvious solutions
being bypassed. One of us (can't remember who) said

>  The problem isn't that you have "big data." The problem is
>  you just have data.

People have moved on. The news articles on "big data" salaries resulted in
lots of engineers and lots of new tooling and now essentially there is no salary
differential. 

Now engineers are now looking for ML projects to get them the 600K+ salaries  reported
in the press. Probably sooner rather than later, salaries for ML
professionals will drop down to baseline salary for other engineers as engineers
flood what is otherwise a niche market and ready-to-use tooling continues to
appear. Just as happened with "data science" before it. But in the meantime, 
engineering managers have to deal with project
proposals involving ML in areas where ML has no business being introduced.

What's the main problem? It's actually the same as with that noSQL project
that everyone was trying to get on the team for ten years ago:
 
>  The problem isn't that you have "big data." The problem is
>  you just have data.

I actually have some background in this. In the nineties, I did my PhD in
an area of artificial intelligence known as "Knowledge Representation."
Back then, neural networks were two layers only, data was hard to come by,
and machine learning projects were something you did after taking tons
of statistics courses and building your own programs to do everything from
scratch. Due to both development effort and lack of data, the idea of an
ML system that could magically learn everything was a pipe dream. Instead,
you needed to spend time on knowledge representations and models to take advantage of the paucity of
data you did have available. Unfortunately, that was labor intensive, and
this apprach quickly fell out of fashion as soon as
big data architectures and "deep" neural
network approaches made ML approaches technically feasible.

What made the difference was data. And it is true - we have a lot more data
and these solutions are now feasile. But it isn't entirely true that those
first ML projects completely ditched traditional AI techniques such as 
knowledge representation and modeling. Think back to those first successful
initial applications of ML programs - in Google, in DeepBlue, in Watson. The
amount of data was truly stupendous compared to initial applications. But
that wasn't all that made the difference. The AI researchers, disciplined
from years of not having enough data, still used hybrid models to constrain
the dimensions of search. Chess engines used
heuristics to prune the search space; handwriting recognition used existing
grammar parsers to get reasonable candidates for matches; image detection
applications were targeted at specific domains where you already knew much
about what an image should look like (e.g. license plate readers).

Why is this important? Because the boosters of ML seem to have forgotten
much of the lessons that made these applications successful. Instead, the
technology itself is hyped as being able to solve any problem without
any analysis or modeling whatsoever. Modeling and
knowledge representation is claimed to be obsolete - the deep structure of
the neural network will figure it out all for you. Software was once said
to "eat the world," but now machine learning and neural networks are now going
to eat software and render it obsolete.

This hype misses the fact that if you bypass modeling entirely, you are
dramatically increasing search space. This causes your data requirements
to increase to an astounding, unheard-of degree. One rule of thumb is 
that for every additional
dimension of the data you need to look at, you need to increase the data you
need *by an order of magnitude*.

Boosters of the ML-only outlook normally work for or are consultants of
"Big Tech" companies like Google and Facebook. Lost in all of this is the fact
that these companies have truly *enourmous* amount of data available for their
tasks - think **peta**bytes, not terabytes. Given enough data and enough expenditure
on computer time, it is no surprise that they are able to get their solutions
to work. But I guarantee that if you are reading this, then this does not
apply to you. You have terabytes of data - if you're lucky; my experience
is that most of these pilot projects have tens of gigabytes of clean data
at most. You have yourself,
or perhaps a team of people like yourself, to clean up the data. If you have the
background necessary, you'll know how to prepare the data, e.g., by ensuring 
it is stationary and factors out seasonality effects. If not,
you'll have to simply hope these factors don't render your ML model useless.

Given these facts, it is no wonder that these in-house ML solutions
haven't produced the breakthroughs needed to eliminate traditional software
solutions. In many cases, lack of data or proper data cleaning processes has
meant producing brittle models that react poorly to future data streams or fail
to improve as more data is given to them. And where efforts are successful, it
still requires a disciplined approach:
an acquire-clean-refine-retrain cycle that is usually no less time-consuming 
than the
traditional code-debug-test cycle of hand-coded AI solutions.

So what to do? The key is to remember that there are already solutions
that exist. They just may not be the ones that look good on your resume.

* Don't ignore knowledge representation and pick a model. Your *data*
(or rather, how much of it you have after cleaning) should tell you 
how complex your model can be. Even if another model is
"better," it will do no good in practice if you wind up with a model
that's overfitted due to lack of data. 

* When you have to choose amoung equally-effective models, you're often
better of with the simpler one. There's a reason your ML course
always started with least-squares linear fitting - sometimes that's the
most effective model you have.

* Scope your data architecture *after*, not *before*, you have an idea
what data model you need to use. If you're dealing with gigabytes of data,
you'll probably be just as happy with a relational database as you will
with some over-the-top Storm architecture. Heck, for some ML projects,
even an in-memory database will cut it just fine.

Regard your business problem as a problem to be 
solved, not as an "ML Problem" to impress other engineers. I suspect
that in two years, the resume screeners will breeze right past the ML
project you hype on your resume, just as they will with the rest of the
alphabet soup of open-source technologies people list to look good.
You know what will look good on your resume? Using your brain to solve
problems. With or without machine learning.
