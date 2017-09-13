---
title: Why Jekyll is the Best Thing for Your Development Blog
---
# Jekyll is the Best Thing for Your Development Blog

I have started and quit blogs several times now. I believe I have ended
this cycle. And I have Jekyll to thank.

[What, you may ask, is Jekyll?](https://jekyllrb.com/) Why, it's a static-site
generator that is the best thing for coding blogs since, ummmm, coding
blogs.

Jekyll is beloved by many people in the software industry for blogs
and coding. Some have cited its Git-centric nature of development. The fact
that GitHub Pages make it easy to host your own blogs on GitHub and
render them on Jekyll adds to this perception.

I, however, am old enough to remember when Git wasn't around. You could
do this just as well with any old CVS; in fact, if you aren't branching
(and if you're the only person doing development, you almost certainly
don't _need_ branching), anything will do. It helps to know Git so you can
use the theme repositories, but it isn't a must-have.

No, the main reason is that as an end-to-end tool, nothing beats the
environment for producing static blog pages. But first, a discursion on
why those _other_ platforms got on my nerves:

#### Here's the Problem with Blog Platforms

I started using LiveJournal (remember them?) in 2006, shortly after
the birth of my first son, as a mechanism for posting and sharing baby
picture. I also put in occasional personal blog posts. The price was
right (free!).  Posting there usually required picking some sort of
theme, deciding after much deliberation to use a free one, and posting
contributions. Posts were done using some online wiki-style WYSIWYG
editor. When I first started using it, I had no complaints, but it
didn't take long for it to get on my nerves.

The most annoying is was the whole edit/preview/post dance that you have
to do with any wiki-style blogging platform:

1. Start by drafting your post in a "real editor" like Word
2. Do copy-and-paste into it into the WYSIWYG editor
3. Hit "Preview" button
4. _"OMG it totally screwed up all my formatting!"_
5. fixfixfixfixfixfix
6. *Submit*
7. _"DAMMIT I missed that typo"_
8. Click edit
9. waitwaitwaitwaitwaitwaitwaitwaitwaitwaitwaitwait
10. Scroll to edit point
11. Make your edit
12. Go to 6 above and iterate a dozen times

In general, you wound up doing too much editing in a huge edit box that
was totally unsuitable for the task.
Also, if you wanted to put in a picture,
you had to do this weird thing where you organized it in an album, somehow
linked to the shortcut that you had to copy on notepad or you forgot
it... just a lot of nonsense. It was good for lightly edited diary posts,
but wasn't anything you'd show to anyone other than your friends.

In 2010 I decided to create a professional blog. LiveJoural (and
pretty much everyone else) was starting to lose traction and yield to
WordPress, so I set up my professional blog there. The experience and
community was better, but I was still stuck with the
submit-wait-scroll-edit cycle that I hated with LiveJournal.

The central problem with all of these is that as
blogs-as-wikis; you did all formatting work online, in an online editor
hardly suited for the task. I needed something that worked the way I
was used to working as a software engineer - that is,
productively. Enter Jekyll!

## So, Why Move to Jekyll??

By moving to Jekyll, I won back a lot of things, and gained some things
I didn't even know I missed:

1. Bye bye web-based editor.

  I had already migrated to using other sorts of editors for my
  drafts - all it took was a few frustrating sessions with LiveJournal's
  unwieldy HTML editor to convince me that was the way to go. But with
  Jekyll, your work is generally offline, where it belongs. You can use
  your favorite editor. Presuming you're working with raw Markdown or
  HTML, you can even use Emacs or (yuck) VIM.

2. Hello source control!

  By getting your editing offline, you get full ownership of files and
  can leverage Git, SVN, or whatever you desire. Given that many Jekyll users
  are using GitHub hosting, you already have a workflow that you can move
  straight into.

  You don't have to make the workflow ridiculously complex either - for instance,
  I generally just work on the master branch and push when I'm done. But it's
  good to have branches for keeping longform works or multiparts in progress.

3. Bye Bye to klunky HTML editors

  Jekyll uses Markdown by default, though you can use raw HTML if you desire.
  Generally I don't need the fine-grained control I get with raw HTML. But
  Markdown is easy to remember and use, and is much easier to edit than
  HTML. As a result, you can just work directly with your formatted text
  instead of swearing at the HTML editor for never properly putting the
  proper paragraph formatting for your bullet points, even though you manually
  fixed it 4 times already.

4. Hello themes

  If you use GitHub Pages, there are about a dozen miscellaneous themes. One
  of them should serve as a good "starter theme."

  However, if you are willing to host elsewhere and fiddle with your own
  Jekyll server, there are [thousands of good-looking themes available for your
  use](https://github.com/jekyll/jekyll/wiki/Themes). Given that most blogging
  platforms sell themes as add-ons, leaving you to choose only the blandest if
  you don't wish to pay, this is a little bit like free money.

5. Hello customization

  This is a biggie. But it's also the most work.

If you want to customize WordPress (presuming you host it yourself),
you'll get a lot of capability and an equal amount of pain. It is
listed as one of the most undesired technologies to work with on
StackOverflow, meaning two things:
1. It's unpleasant and,
2. If you
want to do customization, entirely necessary, so much so that there
are thousands of engineers making their living doing this alone.

Jekyll is more straightforward - it is a static-site generator. [The
documentation (done in Jekyll, of course), is some of the most straightforward
and thorough I've seen](https://jekyllrb.com/docs/structure/) for this
sort of project. If you don't want to do much to set it up, you don't
have to.

But most people will customize, and when it does, that's where Jekyll's
framework shines. It is very transparent; in particular, if someone has a
neat technique in their theme, it's very easy to find out exactly how they
did that and adapt your theme accordingly. This particular theme I'm using
is the rather straightforward "Dinky" theme, but I was able to use the
framework to quickly inject a title bar, and I used collections to set up
a tagging scheme so that posts were associated with different pages.

However, if you do customize, a word of caution - you want to set up your own
local Jekyll server. This isn't as hard as you might think, particularly if
you're the sort that is used to working on Linux VMs (in my case, I just have
a Vagrant image that hosts nothing but Ruby and Jekyll). But you'll need to
set it up so you can debug your theme. Otherwise, you're stuck with a painful
development process, as you will be pushing edits on at a time just to see
what works - definitely not the right way to go.

### Oh uh - Why Not to Move

Jekyll isn't for everybody. If your blogging will be:

- a straightforward sequential blog
- with limited need for formatting
- where you are ok using the blogging platform for hosting
- and you don't have a technical background

then Jekyll is actually going to be more work for you. You'll have to
pick up a few things (at least the basics of Git, and probably how to
run Jekyll itself), and you aren't going to use anything that
leverages Jekyll.

There are use cases like this, but I'm not sure how often people do this
anymore. But if you're still one of the remaining "message in a bottle" bloggers, and you don't have the patience to deal with the overhead of Jekyll, it
isn't for you.
