---
layout: post
title:  "A Dev Env for Jenkins Pipelines"
description: ""
date:   2019-01-03 00:00:00 +0300
categories: blog
tags: [jenkins, ci, testing, productivity, oss]
---


Because as with any “code”, we’d expect “Jenkins pipelines as code” to have a decent development environment too, right?

Well...

{% include image.html path="posts/jenkins_pipelines_1.png" path-detail="posts/jenkins_pipelines_1.png" alt="Jenkins Pipeline" caption="" %}


tl;dr it’s not a dream landscape today…

In the sections below I’ll be keeping some notes (mainly to self, but that will hopefully help a few others who are getting into writing Jenkins pipelines) as a reference for getting up & running. It’s a WIP — and feedback is welcome too!

You see, the team I’m on is now working on extending the automation it has in place, around what we call the “productization” process, here in Red Hat. This is the process that handles releasing a “product” version from an “upstream” open source project.

Our open source projects are on the [3scale GitHub org](https://github.com/3scale) — and 3scale is a Red Hat — led fully open source solution to API Management (think auth*, rate limiting, monetization, reverse proxy, etc. as an extra component you deploy in front of your API so you never have to implement that logic in your own codebase. We’ve done it and it’s OSS! Go use that instead! </pitch>).

Back on topic… The automation that is in place is **based on Jenkins** (we need the flexibility) so even though the pain of maintaining — and upgrading — a self-hosted Jenkins and its plugins over the years hasn’t made me its biggest fan, there is little choice on the matter (for some very valid reasons).

Anyway, let’s start looking into the various points of our development environment for Jenkins pipelines, starting with… the language our pipelines are written in!

## Groovy DSL vs. Job DSL vs. Pipeline DSL (Dynamic Pipeline vs. Scripted Pipeline) vs. Dynamic DSL vs. Groovy

… what a mess…

* Here is a good StackOverflow answer [explaining the **difference between Job DSL and 
Pipeline DSL**](https://stackoverflow.com/a/39214771), as this is the main separation 
(tl;dr Job DSL is for **creating** the Jenkins jobs themselves, Pipeline DSL is what their 
**implementation** is written in. If you’re now thinking, “so I need both?”, unfortunately the 
answer is “yes”, and if you’re thinking “well that’s not very good, is it?” the answer is — 
again — “unfortunately, yes”)

* [GroovyDSL (or **GDSL**) is a scripting framework](https://confluence.jetbrains.com/display/GRVY/Scripting+IDE+for+DSL+awareness) 
used in IntelliJ to support external DSLs (like the Jenkins Job DSL). So you basically **export 
a gdsl file from Jenkins**, install it in IntelliJ, and it now knows how to do some syntax 
highlighting and code completion for the Job DSL.

* Considering that the Job DSL is a Groovy-based DSL, yes, **you can also write Groovy in your Job DSLs**. 
Helpful, but only up to a point. Remember that the Job DSL adds lots of extras, so any groovy 
tooling you might be hoping to use won’t necessarily cover all your needs here.

* **Dynamic Pipeline vs. Scripted Pipeline**: first of all, remember we are in the “Pipeline DSL” 
BoundedContext. We’re talking about the implementation of the pipelines, not jobs. To 
understand the differences, [this is the right place to look](https://jenkins.io/doc/book/pipeline/syntax/).
  tl;dr **Declarative** is more limited, but has **lower learning curve**, making it an ideal choice 
  for simpler pipelines. **Scripted** provides very few limits, but comes with steeper learning 
  curve (Groovy), making it an **ideal choice for power-users** and those with more complex 
  requirements. To make matters more complicated (and flexible), you can use `script` blocks 
  even inside Declarative pipelines, where you can use Groovy.
  
* _Dynamic and Scripted_ above are not to be confused with the [**Dynamic DSL**](https://github.com/jenkinsci/job-dsl-plugin/wiki/Dynamic-DSL), which is part 
of the Job DSL plugin. That’s the part of the Job DSL that adds support for plugins. Is it confusing 
yet?

## Valid syntax & IDE support

Being used to code completion and automatic syntax highlighting / corrections available at my 
fingertips, I find it immensely distracting & inefficient to have to focus on getting the 
syntax right. I mean, I should be focusing on getting the code to do what I want. Syntax is 
an implementation detail and IDEs abstract that away nicely...

So I normally use IntelliJ. First thing I tried was to find a plugin for the various DSLs 
used in Jenkins.

* There is a Jenkinsfile plugin, but it’s [not that great](https://plugins.jetbrains.com/plugin/10127-jenkinsfile-idea-plugin) 
unfortunately…
* Then I went to the [official docs](https://github.com/jenkinsci/job-dsl-plugin/wiki/IDE-Support) 
about IDE support. tl;dr Dynamic Job DSL is not supported, but, yes, you can get some syntax 
highlighting / auto-completion working (through GDSL we mentioned above).

The problem with Pipeline DSL is that the available constructs depend on the plugins that are installed in the Jenkins instance being used.

Here is an example of the [most complete GDSL export](https://gist.github.com/ggarcia24/fc5acec3288812b34c64a4f2b8f9bca9) I have come across.

Or you can download your GDSL by going directly to https://<Jenkins>/job/<Job Name>/pipeline-syntax/gdsl, as shown below

{% include image.html path="posts/jenkins_pipelines_2.png" path-detail="posts/jenkins_pipelines_2.png" alt="" caption="" %}

Exactly because the syntax available in the DSL depends on the plugins installed in your Jenkins instance, it would be ideal if some IDE could check the syntax of my files against the actual Jenkins server that’s going to run them.

## Enter VSCode…

{% include image.html path="posts/jenkins_pipelines_3.jpeg" path-detail="posts/jenkins_pipelines_3.jpeg" alt="" caption="" %}

Well, Visual Studio Code comes with an extension that does exactly that! The 
[Jenkins pipeline linter connector](https://jenkins.io/doc/book/pipeline/development/#visualstudio-code-jenkins-pipeline-linter-connector).

Reason enough to move away from IntelliJ! (for this project only… for now…)

## Other useful tools / links:

* [Jenkins Job DSL Playground](https://job-dsl.herokuapp.com/): a heroku web application that allows you to test your dsl and verify that the correct XML is generated for the configuration of your job.
* [the official Job DSL API reference docs](https://jenkinsci.github.io/job-dsl-plugin/#)
* https://jenkins.io/blog/2017/05/18/pipeline-dev-tools/





## Testing Jenkins Pipelines

The reality is that developing Jenkins pipelines today still relies on **a lot** of manual 
testing to make sure everything is working correctly.  : (

Testing the CI server is a big topic in itself and is probably worth a (few) blog post(s) of 
its own. For now I’ll just leave you with these thoughts:

How easy is it to test the following sequence:

1. Spin up a jenkins worker node (this could be an AWS EC2 instance / another cloud VM / a container, etc.)
1. Run init scripts for VM (install some basic tools — e.g. git)
1. Run jenkins pipeline and verify steps where executed as meant to.

That is… how is it to verify that the environment that is being set up to run the other verification tests is correctly set up in itself?

You see, many of the test failures that come up when you are **developing** the pipelines themselves — i.e. when you are still in the development phase — are because of some misconfiguration in the environment itself.

Test failures don’t usually come from broken tests by a developer on your team. That happens later on, once the pipeline is out of development and in “production” — i.e. in use by the development team.

Traditionally, testing across [SUT](https://en.wikipedia.org/wiki/System_under_test) barriers like in the example above usually happens with [test doubles](https://martinfowler.com/bliki/TestDouble.html).

I will leave it for a future post to elaborate on this — but just leaving this here so you know it’s there.

Also, some links, for further reading:

* [Jenkins Test Harness](https://github.com/jenkinsci/jenkins-test-harness)
* [Running your pipelines locally](https://liatrio.com/local-development-using-jenkins-pipelines/)
* https://github.com/homeaway/jenkins-spock/tree/master/examples/shared-library
* https://blog.grdryn.me/blog/jenkins-pipeline-library-testing.html

## Visual wizard for creating Jenkins Pipelines

There is actually a pretty neat editor inside Jenkins itself (once you install the [Blue Ocean](https://jenkins.io/projects/blueocean/) plugin).

The trouble is this editor is pretty well… hidden… **I only came across it by accident**!

Here’s [how to access it](https://jenkins.io/doc/book/blueocean/pipeline-editor/#starting-the-editor)!
 (I am linking to the docs, rather than write the instructions here, considering that blue ocean is still under pretty active development and they might change).

It’s great for getting started and putting a basic pipeline together.

You’ll quickly find not every field is fully supported, but — hey, at least it gets you going! ;)

## Useful?

I know the information is not particularly well organized, but it’s meant more as a place to 
keep links / mindmap rather than a proper post. If enough folks find this interesting I can 
put some more effort into organizing / expanding the sections here and maybe even creating a 
series of posts to cover the various points separately.

Oh, and… Thanks for reading this far!! Didn’t think you’d make it… :P :D  