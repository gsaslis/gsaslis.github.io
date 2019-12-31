---
layout: post
title:  "Groovy SDK is not configured with IntelliJ + Homebrew Groovy"
description: "i.e. how to tell IntelliJ where the Groovy SDK has been installed by Homebrew. Hint: it’s a 'hidden' path and IntelliJ doesn’t see that by default."
date:   2018-08-21 00:00:00 +0300
categories: blog
tags: [oss, community, devstaff]
---

I started my day early this morning. And I got one of those situations where you get an error message in your IDE that you’d really like to get rid off — so you can get on with your morning cup of coffee — but some stupid thing is getting in your way…

Now, usually, you’re in the middle of something else at the time and you can’t afford the context switch to fix it, but you’ll keep running across it and it will annoy you every time. At least, it does for me…

The notes below are primarily an attempt to save myself the trouble of going through this again (cause it really is a simple fix, no magic here), but hopefully it helps others too…

## 1. The Error Message

{% include image.html path="posts/intellij_error.png" path-detail="posts/intellij_error.png" alt="IntelliJ error" caption="The original error message that shows up in IntelliJ, prompting you to configure the Groovy SDK" %}
{% include image.html path="posts/intellij_error2.png" path-detail="posts/intellij_error2.png" alt="IntelliJ error" caption="Setting up the Groovy SDK as a Library..." %}

No options showed up in my dropdown…

Checked Groovy language plugin was installed in IntelliJ… Yes.
Global Libraries… ? can’t select “groovy sdk” there…

So I clicked on Create…

## 2. The Problem

{% include image.html path="posts/intellij_error3.png" path-detail="posts/intellij_error3.png" alt="IntelliJ error" caption="IntelliJ finder popup not showing hidden files and folders..." %}

The problem with the above screenshot is that hidden files and folders don’t show up in IntelliJ’s finder popup window.

The reason I need to see the hidden files and folders is because I installed Groovy with Homebrew ( `brew install groovy` ) and that means that the path for my Groovy SDK lies in: `/usr/local/opt/groovy/libexec`. Thus… I can’t select the actual path I’d like due to IntelliJ not showing the hidden files and folders ( `/usr` is one of those hidden folders ).

Tried the old `defaults write com.apple.finder AppleShowAllFiles YES` again, (the command-line way to show hidden files and folders in finder), but no luck with that too…

## 3. The Solution

The way around this is to use a very (very) useful finder shortcut — which, btw, Apple seems to have buried away from its user interface — that allows you to manually insert the path you would like to navigate to in finder.

This is the “Go to Folder” menu option that you would normally only find in the finder menu, as shown below:

{% include image.html path="posts/intellij_error4.png" path-detail="posts/intellij_error4.png" alt="IntelliJ error" caption="The `Go to Folder...` menu option in Finder" %}

Unfortunately, this menu doesn’t show up in IntelliJ, so the only way to access it is by using the keyboard shortcut `Cmd+Shift+G`, as is also shown in the screenshot above.

Once you do, you can finally insert the path you like, regardless of whether it’s hidden or not:

{% include image.html path="posts/intellij_error5.png" path-detail="posts/intellij_error5.png" alt="IntelliJ error" caption="Finally being able to insert the Groovy SDK path, regardless of whether if it’s hidden or not..." %}

Hope this helps someone out there…
