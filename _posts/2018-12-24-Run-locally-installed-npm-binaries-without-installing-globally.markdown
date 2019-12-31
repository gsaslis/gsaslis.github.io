---
layout: post
title:  "Run locally installed NPM binaries without installing globally"
description: "I try to avoid installing things on my laptop. Installing NPM binaries globally, just because some project needs them, is bad form..."
date:   2018-12-24 00:00:00 +0300
categories: blog
tags: [npm, bash]
---

This is probably really obvious to folks who work with node.js / npm on a day-to-day basis, but:

a. I don’t
b. ~~googling~~ duckduckgoing for this wasn’t very helpful, so I thought I’d keep a note-to-self here.

My problem was that I downloaded a project whose instructions said something along the lines of:

> Install with `npm install -g <binary_name>` and verify installation by running <binary_name> --version .

I don’t like that -g which stands for `--global`, and requires root permissions, so I just wanted to install this package locally.

So I just ran `npm install`.

And skipping the `-g` meant there was no <binary_name> to be found anywhere and I tried quite a few places (from the google search:

* `.bin`
* `.node_modules/.bin`
* `lib/`
* `$(npm bin)`

In the end, the solution was to look inside the `package.json` and find the `bin` section:

```json

{
  "name": "binary_name",
  "version": "1.0.0",
  "description": "some awesome binary",
  "main": "index.js",
  "scripts": {
    "test": "echo \"no tests\" && exit 1"
  },
  "bin": {
    "<binary_name>": "./index.js"
  },
  "author": "Some cool person",
  "license": "MIT",
  "dependencies": {
     ...
  },
  "devDependencies": {}
```

In that section, you’ll see that there is a `.index.js` as the `binary_name`.

## tl;dr Solution

It was as simple as creating an alias in my shell :
```bash
$ chmod +x index.js
$ alias <binary_name>="$(pwd)/index.js"
$ <binary_name> --version
1.0.0
```

_Needless to say, but: substitute `<binary_name>` for the name of the binary you’re struggling with._