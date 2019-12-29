---
layout: post
title:  "Which Jenkins plugin provides pipeline step X?"
description: "When writing a Jenkins pipeline, have you ever wondered if the pipeline steps you're using are built-in, or provided by a jenkins plugin?"
date:   2019-04-23 00:00:00 +0300
categories: blog
tags: [ci, jenkins, testing]
---

I’ve just started playing around with the [homeaway/jenkins-spock](https://github.com/homeaway/jenkins-spock) 
framework for writing some unit tests for a Jenkins Shared Library.

Even though the examples folder in the above linked Github repo is pretty useful in 
understanding how to get started (and this video presentation even more so — in fact, it’s a 
must-watch), I hit a bit of a wall pretty soon after. I’m leaving this as a kind of 
note-to-self-that-you-never-remember-you-wrote-and-hope-it-matches-the-keyword-you-use-to-search-next-time-you-have-this-problem.

So, the error message was this:

    During a test, the pipeline step [withCredentials] was called but there was no mock for it.
     1. Is the name correct?
     2. Does the pipeline step have a descriptor with that name?
     3. Does that step come from a plugin? If so, is that plugin listed as a dependency in your pom.xml?
     4. If not, you may need to call explicitlyMockPipelineStep('withCredentials') in your test's setup: block.)
         (types)  : Closure$$EnhancerByCGLIB$$5d606cf6.call(GStringImpl)

The error message is already pretty helpful (thanks for thinking about your users, HomeAway.com folks),
so I was sure that my problem was (3).

> But how could I find out which of the Jenkins plugins I already have installed in my master 
provides this step?

Well, one of my colleagues, [Jacob](https://github.com/werne2j), had already hit that wall 
before me it seems, and was happy to share his solution! Big hat tip! ;)

Here is how I managed to find out the maven dependency, so I could add it to the `pom.xml` :

1. Open the jenkins.io pipeline steps reference
1. Search for the name of the step (in our case withCredentials )
1. The step will appear under the plugin that provides it. NOTE: sometimes you’ll have to look at the link behind what the plugin is called on that page, to find the actual name of the plugin
1. Go to https://mvnrepository.com/ and search for that plugin. (Make sure to switch to the Jenkins Releases tab)
1. Go to your Jenkins master — Settings — Plugins to find the version number of the particular plugin you have installed.
1. Finally, copy the maven dependency from mvnrepository.com and paste it into your pom.xml. Do NOT forget to add <scope>test</scope> .

Hope that helps!

Good luck & happy testing!
