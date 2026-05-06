---
layout: post
title: "Safely Running AI Coding Agents"
description: "Learn how to securely run Claude AI agents using Vagrant sandboxing and network isolation (DMZ). A step-by-step guide to safe autonomous AI workflows."
date: 2026-05-06 00:00:00 +0000
categories: blog
tags: [ productivity, technology, privacy, ai ]
---

In a nutshell, I think where coding agents really change the game is through
unsupervised iteration. They can
keep iterating on a problem until the Large Language Model (LLM)
hallucinations become irrelevant. You leave the agent running in the  
background, working on a problem for hours, iteratively querying the LLMs,
verifying the results locally against some guardrails you set around it and,
minutes or hours later, you finally have something useful.
(That's the plan, anyway. 😇 )

But there's a ⚠️ real danger ⚠️ in that first sentence: "unsupervised".
Without proper isolation, an agent running autonomously could inadvertently
delete
important files, access sensitive environment variables, or even start
scanning your local network if it goes off the rails. It's essentially
executing random code the LLMs suggest, which is the definition of a
security risk and the source of nightmares: arbitrary code execution.

Running AI agents can be a bit like inviting a powerful, but sometimes
over-eager, assistant into your digital home. You want them to be productive,
but you also want to make sure they don't accidentally knock over any
metaphorical vases—or worse, compromise your internal network.

Here is my personal workflow for every project where I start running agents:

### 1. The Supervised Inception

I always start with Claude in **supervised mode**. My first instruction is for
Claude to create a `Vagrantfile` that includes all the necessary project
toolchains and dependencies.

Once the environment is defined, I then tell Claude to install... Claude! (
Inception for the win!). This creates a self-contained environment specifically
for the agent.

### 2. Isolation via Vagrant

After the configuration is ready, I run `vagrant up` to spin up the virtual
machine. Inside this isolated environment, I can run Claude with the
`--dangerously-skip-permissions` flag. This allows me to let the agent work
autonomously for hours without constant manual approvals, knowing that it's
contained within the VM.

### 3. Network Guardrails

As @AdmiralAK very correctly suggested, I've added another layer of security:
from now on, I connect to my **DMZ WiFi SSID** instead of my internal network.

This ensures that while Claude has the internet access it needs to do its job,
it has absolutely no access to my internal network. It’s a simple but effective
way to maintain "air-gapped" security while staying connected.

---

*Side note: I am also exploring local models for local AI, but that's a whole
different story... and I don't exactly have 256GB of spare RAM lying around just
yet! 😅*
