---
layout: post
title:  "PGP with Protonmail and Keybase"
description: "A quick guide on how to set up PGP on Protonmail, using Keybase"
date:   2018-11-22 00:00:00 +0300
categories: blog
tags: [privacy, technology]
---

[Protonmail](https://protonmail.com/), the email provider you should choose if you care about keeping your emails private, recently released support for [PGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy).

What that basically means is that you can now send encrypted emails to users outside of Protonmail (emails between protonmail users were already encrypted).

Be default, Protonmail creates a public / private RSA key pair for you, but I wanted to use my own key pair which I had already published on keybase.io.

Here’s how I set it up:

1. Import pgp key to keybase and assign to email address (I had already done this)
1. Export from keybase:

`keybase pgp export --secret -q <key_id> > /some/path/to/keybase-pgp-private.key`

This command on the keybase CLI is not very well-documented:

* The --secret instructs keybase to export your private key, so be careful where you store this and the permissions you assign to this file.
* The -q is short for — query but it is not much of a full-blown query for the moment, as it just expects the key id.

You will be asked to provide a password that will be used to encrypt your private key. You will need this below, in step 3.

3. Now, head on over to Protonmail settings to import your private PGP key:

> Protonmail -> Settings -> Keys -> Import Key

Import your previously saved file here. You will be asked to decrypt imported key, with password you selected in keybase export step.

4. Finally, enable PGP automatic signing, so that you use this by default:

> Protonmail -> Settings -> Security -> External PGP Settings

{% include image.html path="posts/protonmail_pgp.png" path-detail="posts/protonmail_pgp.png" alt="Protonmail settings" caption="Protonmail settings" %}


* Enable automatic signing of external messages
* Enable automatically attaching public key

Hope that helped!

Happy encrypted emails!!!