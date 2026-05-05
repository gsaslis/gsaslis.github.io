---
layout: post
title:  "Working on a better home for Open Source"
description: "GitHub is giving us even more reasons to consider alternatives. I'm so happy I'm 
working on one of them!"
date:   2026-05-04 00:00:00 +0300
categories: [blog]
tags: [work, open source, github, microsoft]
---

It's been a few years since I've posted on this blog. In that time, I can't count how many times 
I've said "I should blog more" or "this would be a nice blog topic". It's just one of those
things... But I'm now almost ready to move this blog off of GitHub Pages (finally!), so, it is a 
good opportunity to publish a couple of pieces I've had in the back of my mind.

First up, I've been wanting to blog about why I think we need a new, **better home for Open 
Source Software (OSS)**. 

I had given a short talk on this topic a couple of times already:
- in the Greek FOSS communities' yearly meeting (FOSSCOMM) [in late 2023](https://pretalx.fosscomm.gr/fosscomm-2023/schedule/#),
- in JFall in the Netherlands, [in November 2025 ](https://jfall.nl/timetable-2025/), 
- as a quick lightning talk [in a DevStaff.gr meetup](https://www.meetup.com/devstaff/events/305237200/?eventOrigin=group_events_list)

But, yeah, I never got to writing the blog post to go with that. Never got to explain "The 
Problem with GitHub", as my title talk went, in writing. And it looks like now, with all the 
recent events surrounding GitHub's uptime, (just [check their status page history](https://www.githubstatus.com/history), 
if in doubt) Microsoft/GitHub has gone and done all the explaining for me! 😆

But even before all the reliability issues, my thesis was simple: 
- OSS is a Digital Public Good, 
- By definition, public goods should be accessible by everyone, anywhere ("nonexcludable"),
- Therefore, it is **incompatible** to host our public goods on a platform that is: 
  - proprietary, 
  - controlled by a single entity, with specific terms of service it, alone, can set and change 
    at will, 
    - that is also a tech giant, with interests not aligned with those of the public,  
    - US-based, (not in the sense that US law is bad, but in that we are dependent on just one 
      country), 

So, there are lots of reasons I'm excited about Radicle, as the alternative to hosting the world's 
OSS! Here are my top 5: 
1. peer-to-peer (p2p) architecture is the right fit: it ensures 
  - accessibility and
  - resilience, 
2. works on top of git - adds what's missing: [Issues](https://radicle.dev/guides/user#working-with-issues), 
[Patches](https://radicle.dev/guides/user#working-with-patches) (Pull Request equivalent), 
   Discoverability,
3. all you need is a key pair, which is great for both privacy and security (more on that in a 
   different post), 
4. it's extensible, through its [Collaborative Objects (COBs)](https://radicle.dev/guides/protocol#collaborative-objects) 
   (🌽 pun intended),
5. it's [owned by a non-profit](https://betterinternet.foundation/), not Venture Capital,


I won't go into each point in detail - each one could be its own blogpost. I'll just 
highlight that out of all the GitHub alternatives, Radicle is the **only** one 
that is truly **peer-to-peer** in nature. Which is not only the right architecture for the problem, 
in my opinion, but it also makes things interesting! 
Who doesn't like a bit of fun with distributed systems? ;) 

In a way, Radicle is like BitTorrent: In Radicle, you "seed" (🌱 pun intended) git repos, similar 
to how you seed the torrents you want to keep online. Not all the similarities carry (e.g. 
torrents don't change over time, whereas git repos do. There is no distributed hash table (DHT) 
and so on...), but the main idea is the same: you run a Radicle node to seed the git repos you 
want to keep online (and also to sign the commits, issues and patches you work on).  

If you want to learn more about Radicle, the [guides](https://radicle.dev/guides) should already 
help with the introduction. For more questions / information, you can just hop over to the Radicle 
[Zulip](https://radicle.zulipchat.com/) (an open-source Slack/Discord replacement - yet another 
post for another day) and ask us there! 
