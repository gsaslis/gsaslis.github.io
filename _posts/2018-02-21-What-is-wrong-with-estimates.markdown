---
layout: post
title:  "What’s wrong with estimates?"
description: "Nothing... Apart from pretty much everything with the way we use them..."
date:   2018-02-21 00:00:00 +0300
categories: blog
tags: [productivity, programming, agile]
---


# What’s wrong with estimates?

Nothing… Apart from pretty much everything with the way we use them…

{% include image.html path="posts/estimates_dilbert.gif" path-detail="posts/estimates_dilbert.gif" alt="" caption="http://dilbert.com/strip/2009-12-07" %}

If you are one of the people who actually enjoy spending their time **giving** estimates for how long a piece of software will take to write, you might as well stop reading this post. The last thing I ask of you is to leave me a comment below, so we can get to know each other. I’ve never met *one of your kind*…

If, on the other hand, you are one of the people who has spent long nights working on deadlines, overcommitted on work you couldn’t deliver, or been held accountable for estimates gone wrong for reasons not entirely within your control, (and we’ve all been there) then I would invite you to read on.

First, let’s go back, for a second, to look at **WHY** we are being asked to provide estimates.

Some of you will immediately think about *planning. S*ome may think that they lead to *predictability* in software development iterations. Some may suggest we need them in order to make *cost-based decisions. O*thers may argue that the analysis during the estimation process and breaking down into small tasks help *better understand the requirements*. Some may even go so far as propose that making good estimates shows you’re a good professional (*“how well do you know your job, if you can’t provide a good estimate”).*

I have heard *all* of the above arguments. And there is *some* truth in them all.

Yet, there is an equal amount of bullshit.

## Let’s start with Planning

Clients want to know **when** they can finally get their hands on the feature you are working on. And they want to know that so they can plan other activities, coordinate with marketing, sales, etc. Right?

*Wrong.*

In fact, this is where the problem starts. Because if we unroll the statement above, we’ll see that you, my dear fellow developer, are now working on a **feature** that some client expects at **a specific date and time**.. Obvious? Why so?

My first problem is the “feature” part.

It seems someone has managed to convince the client to buy the **outcome** of (some weeks or months of) your work. Well, bravó to the sales person cause, in my eyes, what they’ve just done is… sell them a part of the future.
> # Selling software features is selling the future.

This is a subtle, but important point: they have not sold them your **services** for this period of time. We are talking about the *outcome* here, so they have sold them something which **does not yet exist**.

It may sound strange that I am insisting on this point, because “that’s just how the software industry works”, so you may consider it a given.

However, for me, this is a fundamental concept in our industry that is plain **wrong.** We have trained our customers to expect **features** (I’ve always liked how that word resembles “future”), rather than **services**.

And what is the problem with features, you may ask?

First of all, there’s … the communication gap:

{% include image.html path="posts/estimates_communication.jpeg" path-detail="posts/estimates_communication.jpeg" alt="Communication is difficult" caption="Communication is hard" %}

We all know the above cartoon to be an exaggeration of what is happening in software development, but we all also know there’s some truth in it. The feature the client is expecting is different than what the team has built.

Agile Software Development comes to address that problem through iterative development and closer collaboration with the client. And yes, this can help, but only when the client is buying *iterations*, **not** features. Not when we are working in fixed scope, fixed budget contracts, with milestones and deadlines.

## Estimates == Commitments

So, let’s talk about deadlines. And let’s start all the way up (on the business level), because once we have taken the first step in this direction, it’s **very hard** to go back.

Since you’ve decided to sell features (in fixed scope contracts), you also have deliverables. Therefore, you have a need for commitments. Because, remember, **the client wants to know** **when the feature you’re working on will be ready**.

And that was when they asked you for an estimate. And you gave some story points. BUT by providing one, you have just made a commitment. **A commitment to deliver**.

This is what we fail to understand about estimates. Estimates are treated as commitments.
> They didn’t really ask “how much work is this”. They asked “when is it going to be ready”.

And to put it in our own terms, so that it’s clear:
> # You probably gave a *java.time.Duration*, they were looking for a *java.time.Instant.*

Which brings us back to *selling the future*. I am asked to make an estimate that is treated as a commitment that something will happen in the future.

And this is how I feel when that happens:

{% include image.html path="posts/estimates_psychic.jpeg" path-detail="posts/estimates_psychic.jpeg" alt="" caption="This is how predicting the future makes me feel." %}

*And this is all without touching the “Estimating in hours” pitfall. I am taking for granted that — as an industry — we have moved past that.*

tl;dr

Estimates as a planning tool runs the **great** risk that they estimates are treated as commitments and not as forecasts for the amount of work a certain backlog item includes.

Enough with planning. Let’s move on to the other reasons for estimating:

## Predictability

The main thinking here is: “If we keep track of how many points / hours / fruit sizes / etc. we’ve burned in the last few iterations, we will be able to start predicting what we will do in the upcoming ones”.

And, yes, I have seen this happen.

But just because it worked for somebody else, it doesn’t mean it will work for you. So, let me pose some challenges, as food for thought for the way you approach predictability:

* *Are your iterations always a fixed length?*

If some iterations are 9 days and others 11, you have already introduced one variable into your predictabilityCalculationEquation.

* *Does your development team also do support?*

If yes, you will have serious **capacity** fluctuations during your sprints. Nobody can predict how much support will come from clients during a certain iteration. Here’s another variable.

* *If your development team does support, is there an explicit separation between support / development?*

The concern here is context switching. The two are different kinds of activities, so you might want to consider ways to completely separate them. Some ideas include: rotating a person that is dedicated to support per day / week, or having the team group all support requests / tasks in a specific time of the day. Context switching is another variable.

* *Does your development team accept interrupts from other departments?*

If they do (and worse, if they also do support), then you are probably killing your devs’ *flow*. But that’s a whole other blog post on its own. Flow greatly affects how effective your developers are and that is very (very) hard to measure. With your understanding, i’ll call it a *superVariable* for your equation.

On the other hand, tracking effectiveness can be surprisingly simple. I don’t remember where I heard this concept from to attribute it properly, but I absolutely love it:
> # If you only count the **number of uninterrupted hours of work, you already have a pretty good idea of how effective your team is!**

Compare that to all the effort around tracking predictability…

* *Does your team accept unplanned work during their iterations (of otherwise frozen requirements)?*

If it does, and this is not support, then perhaps you should think whether iterations offer you much value anyway. Either way, the amount of unplanned work is another variable to consider.

* Do retrospectives take place after every sprint?

If it is predictability you’re after, do your teams actually spend time actively pursuing it? Or is this left to chance? Are you even tracking all the variables in your predictabilityCalculationEquation?

The point I’m trying to make with all this, is that predictability is affected by a bunch of factors that have very little to do with how accurate your team’s estimates were. But more on that when we talk about *velocity* below.

## Cost-Based Decisions

Ask any businessman and he will tell you he needs to know what each feature is going to cost him before he can sign off on you building it.

I would too.

What makes all the difference in the world, however, is precision. Clearly, a few cents won’t make a difference. Neither will a few dollars / euros. A few tens of euros/dollars *probably* won’t either. When we start getting to hundreds, *chances are* you’ll start raising some eyebrows. Thousands, *yup probably*… But then again, it still depends on the project and the feature itself. What’s a few more thousand on a million dollar project?
> # It’s all relevant.

So, if your customer doesn’t really care whether a task takes 4 hours or 6, why are you being forced to estimate on **hours**?

Does it matter when you are delivering **value** **that will greatly outweigh the** **cost**? Remember: the value of a product is not the same thing as its price. A product with the exact same price probably has a different value for each of you reading this post.

And in most cases, your features are sold for their value (to the customer). Not their cost (your work hours). This is a crucial distinction in the business model of a company, so it is important to know what kind of company you work for.

As a general note before closing off this cost-based decisions part, please note: the focus here is on the *estimate* part, so that a decision can be made based on the cost. It doesn’t go into the retrospective part of tracking down what developers are spending their hours on, whether for lack of trust, or for understanding cost centres.

## Better Understanding The Requirements

Moving on. Another reason for using estimates was that the estimation process typically undertaken at the start of an iteration (e.g. in a sprint planning meeting), allow you to refine the requirements and better understand what the customer wants.

I won’t go into too much detail on this one. Not only do I agree we need analysis, but, in fact, we are probably not doing enough upfront design. Some Agile Software Development methodologies don’t allow for too much of it.

Regardless, this still doesn’t go to say that this should come *through* estimates.

## Professionalism

I won’t even go there. People who have brought up this argument have confused professionalism with empiricism. Being a good professional is not the same as being an experienced one.

## Time for solutions

So… rants can be fun! Unfortunately, they’re not constructive unless they end up with some suggestions. Here are mine, because I don’t think estimates are completely worthless…. BUT:

* there *IS *a lot of **waste** in trying to reach **accurate** estimates. We spend significantly more time improving the accuracy than what the business case justifies.

* we should **stop using estimates as commitments**. This will allow us to eventually come up with more realistic planning — one that’s not based on deadlines.

* we should stop worrying about *predictability* and** simply care about *effectiveness***. If we trust our team, we should only care that they are being as effective as possible.

* tracking Velocity is fine, as long as we are tracking just the Unit; not the actual number. If you have heard about using fruit sizes for estimates, then this will sound similar. However, the idea here is that we split the backlog items we estimate into 4 categories/buckets: “Hours”, “Days”, “Weeks”, “Months”.

This means:

* “hours to complete” vs.

* “days to complete” vs.

* “weeks to complete” vs.

* “months to complete” (you can probably make do even without this one).

*I call these **Time Unit Buckets**.*

In doing so:

* First of all, we are considerably **reducing the error margin** for estimates.

* We are keeping units of time which are **easier for humans to relate to**.

* We are clearly communicating to other departments that** they should not expect hard deadlines from r&d**. Which is not a new thing btw, considering everyone already knows the truth about deadlines…

{% include image.html path="posts/estimates_deadlines.jpeg" path-detail="posts/estimates_deadlines.jpeg" alt="Deadlines" %}

* We make estimating / forecasting **very (very!) fast**. Once the main clarifications have been made, consensus doesn’t take more than a minute or two.

* We can still track velocity as number of items in each bucket. And then **go back to tracking effectiveness**.

Please note what I am suggesting here is not entirely new or original. In fact, this is a similar approach to [t-shirt sizes](https://www.mountaingoatsoftware.com/blog/estimating-with-tee-shirt-sizes), or [pieces of fruit](https://jkwerner2.wordpress.com/2011/03/11/introducing-agile-planning-with-apples-chikoos-raspberries-jackfruits-and-watermelons/). The important thing to keep in mind is **relative sizing.**

However, the trouble is, people still like to think in terms of **time**. I’ve witnessed many teams who always bring the discussion back to… hours. They may be talking to you about story points, but you can just tell… in their heads, it’s all “hours” and “days”.

And this is why i like the **Time Unit Buckets** analogy. Because it forces people to think in relative terms — and in so doing, it helps everyone understand that estimates are not commitments. But it also offers an easier mental model: time is easier to relate to…

All you have to do is **forget the number** you would put in front of the time unit, and just **keep the unit itself**.
