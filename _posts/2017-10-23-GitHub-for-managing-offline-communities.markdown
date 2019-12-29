---
layout: post
title:  "GitHub for Managing Offline Communities"
description: "We all know GitHub as a great online collaboration tool for software projects. But what if we tried to use it to run an offline community?"
date:   2017-10-23 00:00:00 +0300
categories: blog
tags: [oss, community, devstaff]
---

{% include image.html path="posts/github.png" path-detail="posts/github.png" alt="GitHub" caption="GitHub helps build online communities. How about offline ones?" %}

This is what we sought to discover a couple of years back. That was when we founded DevStaff, a developer community here in Heraklion, Crete. We were just preparing for our first ever meet up and we needed to come up with some way for getting people involved in the community.

Collecting emails on a piece of paper just wasn’t good enough. Remember — this is a community for developers! Clearly, we needed some better way!

And that was when we thought of GitHub. I don’t remember if I was the one who proposed it, but, even if I was, it was certainly not my own idea. I had already heard of it on some podcast somewhere and — even though I can’t remember the rest of the podcast — the GitHub idea stuck!

> What better tool than GitHub, to bring a bunch of devs closer together?

Hesitations? Yes, plenty! Not everybody knows how to use it. Not everybody would already have an account on GitHub. It would make it more awkward for non-devs to participate that way. This wasn’t what GitHub was built for.

BUT.

The arguments for it were so much more overwhelming!

* If you’re a developer in 2015 (back then) who hasn’t used Git, we should really find any excuse available to help you try.
* If we’re focusing on developers, whose job essence really is learning, we shouldn’t be afraid of asking them to learn one more new tool.
* Learning how to use GitHub, the #1 place for open source projects, would make it easier for our community to start contributing more to open source! Because, OSS FTW!
* We’re picking a tool already built for developers.
* We wanted to build an open community. Choosing a tool that has served open source software so well sounded like a natural choice.
* Instead of using GitHub to build software, we’re using it to build our community. That invites us to think about our community like software. Regardless of how well this analogy works, it’s an interesting twist, you have to admit, that we thought might even invite skeptics to give it a try.
* Come on, isn’t it cool?!? Isn’t this the reason you’re reading this article anyway? :D

Long story short, we were ready to give it a try!

{% include image.html path="posts/github.png" path-detail="posts/first_devstaff_meetup.jpeg" alt="First DevStaff Meetup" caption="First DevStaff meetup, wayy back in July 2015… Unsuspecting developers came to hear about Git and found themselves joining us on GitHub." %}

But this was all back then… We’re now a couple of years down the line, so it’s time for a look back…

> But before we dive in, a necessary disclaimer: the below is nothing more but a personal opinion, in no way written to represent the views of the community as a whole. Hopefully, this will also spark some discussion within the community itself. ; )

Let’s now go through the jobs we hired it to do and see how well it fit our purpose.

## Job #1: Introduction to the Community

We needed some way to explain what our community is about and why people should join. 
Typically, in an open source project, this is handled in a `README` file and that’s what we 
started using as well.

In retrospect, I feel it has served us well for people who are already familiar with GitHub 
and know what to expect. For everybody else, we also built a [website](https://devstaff.gr)
, a [Facebook page](https://www.facebook.com/Devstaff/) and 
we also leveraged the [meetup.com](http://www.meetup.com/DevStaff-A-Developer-Community-Gathering-In-Crete/) 
group page.

**Pros**: Intuitive place to look (if you know what you’re looking for). No need to have multiple websites. Simple to maintain. Free (as in beer).

**Cons**: We could do with better onboarding experience and a more “attractive” look and feel, aimed at new members.

**Verdict: B**

## Job #2: Documentation

In an open source software project, after the “Quickstart guide”, you need a reference 
documentation: How the thing works, what the rules are, why it’s built that way, and so on.

Much of the same holds for our community. We wanted people to know — first and foremost — 
[what the rules are](https://github.com/devstaff-crete/DevStaff-Heraklion/blob/master/CodeOfConduct.md).
Being an open community, we wanted to provide clear guidelines on 
[how people can contribute](https://github.com/devstaff-crete/DevStaff-Heraklion/blob/master/CONTRIBUTING.md) 
(the standard `CONTRIBUTING` file was a natural fit). We wanted them to know why certain 
“design” decisions were made along the way — like our [sponsorship policy](https://github.com/devstaff-crete/DevStaff-Heraklion/blob/master/Sponsors.md).

**Pros**: Version control. Open to pull requests, in case people disagree! Living document — evolves as the community grows.

**Cons**: Not much comes in mind here.

**Verdict: A+**


## Job #3: Contributions

Let’s be clear. This was the big & most important one. Giving people a way to start discussions, to actively participate in the community, to share thoughts and views and provide feedback. We knew GitHub was great for that in the virtual, online world; we didn’t know yet how well it would do for a community in the physical “real” world.

DevStaff community members can contribute by (among others):

* helping us **choose upcoming meetup topics**,
* helping us **prepare and run successful meetups**,
* helping us **run the community itself**.

### Choosing Topics

As a generic developers community, most of our meetups have been about very different topics.
We are not a focused user group, nor do we all share the same love for specific technologies 
/ stacks, as it happens with many meetup groups in most bigger cities.

Coming from a small town (~200K population), with no active communities (to the best of my 
knowledge, back in 2015), our goal was to establish a broad community that would serve as the 
networking infrastructure for all these smaller / more focused communities to spring up.

As such, our meet ups could be about anything software-related. The specifics we left up to 
the community. We chose **GitHub issues** as a way to let people [propose their own topics](https://github.com/devstaff-crete/DevStaff-Heraklion/issues?q=is%3Aopen+is%3Aissue+label%3ATopics)
, so that others could upvote them. The most popular topic would get selected for the 
upcoming meetup.

The way we would count upvotes is by using comments with `👍` . We even built a tool that 
[helped us count](https://analytics.devstaff.gr/) the most popular topics, which, btw, is 
[open source](https://github.com/kabitakis/github-analytics). Later on, GitHub allowed emoji 
reactions, so we adapted to that and the aforementioned tool now supports that too.

(If you’re thinking of using GitHub issues for anything similar to what we did, I’d recommend 
you check it out. — disclaimer: I did NOT build that, so I’m not blowing my own horn here — 
It just made things so much simpler for us!)

The only problem here was that **not all proposed topics had available speakers**; but that’s not 
really related to GitHub. You see, people could still propose a topic even if they couldn’t 
or didn’t want to present.

Yet several of these topics became very popular, leaving the org team to have to get 
creative about finding speakers to satisfy the need. Clearly, this was not sustainable over 
the long term, so we quickly iterated and redefined our criteria such that the topics “with 
the most votes and at least 2 speakers” could be selected for upcoming meetups.

(Again, we added relevant features to our vote counting tool.)

### Preparing and Running the Meet Ups

Apart from **creating a separate GitHub repo for each meetup**, so that presenters could 
upload their presentations and some sample code, etc. GitHub wasn’t much help here.

We handled most of the preparations through direct IM chats (see below, under Communication).

### Running the Community Itself

I was hoping people would use GitHub issues to also raise concerns about how the community itself is ran, so that we could openly discuss and adapt to suggestions from the community. I was expecting this would be touching things like our CoC, discussion on meetup times, places, etc.

> This didn’t work as well as I was hoping…

Most feedback ended up coming in, in person, at the Org Team meetups.

### Overall

Even though some things didn’t go as well as I was hoping for, looking back, I can’t help 
but admit that it still **went much better** than I would have originally guessed.

**Verdict: A**

## Job #4: Communication

Looking back, I can see 2 main forms of communication that takes place online, within the 
community: announcements and p2p conversations (i.e. broadcasts and unicasts). Group 
discussions are more limited.

For **announcements**, GitHub kind of worked. Take new issues for example, or new pull 
requests (which we used, for example to handle announcement of [new job opportunities on our 
job board](https://github.com/devstaff-crete/DevStaff-Heraklion/tree/master/jobs)). It all 
worked fine, **as long as people were watching the GitHub repo**.

And not everyone was. Or even knew they had to do that… : (

For **p2p communication**, there is a complete disconnect. GitHub just fails flat out to enable 
that kind of interaction. Publishing a comment with an @-mention of somebody’s name, is not 
exactly p2p.

(Btw, I see a huge gap here. I expect GitHub to acquire some player in this space soon 
(the same way GitLab acquired Mattermost). )

**Verdict - C: Find some other way to enable your group’s communication.**

## Job #5: Shared Space

One final thing I saw our community had a need for was sharing copies of digital content. 
Whether that was copies of presentations, or document templates, or sample code, this all 
fell naturally within GitHub’s reach.

**Verdict — A: No major issues here. Even though you may need to provide some help / guidance 
to people on how to open PRs, etc.**

With that I will bring this looong reflection to an end. For now, at least… I hope you 
found some of this useful. : )

{% include image.html path="posts/devstaff_bitcoin.jpeg" path-detail="posts/devstaff_bitcoin.jpeg" alt="DevStaff Bitcoin meetup" caption="And that brings us to today… Talking about Bitcoin sure attracts big crowds!!" %}

If (you’re still reading this and) you found any good takeaways here, please feel free to 
drop me a line. I’d love to hear your views, suggestions and similar experiences on running 
a community!