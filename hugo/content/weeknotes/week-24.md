---
date: 2019-01-18
title: "Week 24: Preparing Fluidkeys for Teams"
author: Paul Fawkesley
---
**Protecting liberty by simplifying security**

_Recap_: We’re building Fluidkeys to help teams safeguard their source code and protect sensitive data.

## The short version:

Ian returned from his travels this week, fresh and enthusiastic! It's been great getting stuck back in with renewed focus.

* Experimented with encrypted email using Mailvelope
* Automated signing commits with git and Github
* Started work on Fluidkeys for Teams proposition

## Experimented with encrypted email using Mailvelope

[Mailvelope](https://www.mailvelope.com/en) is a browser extension which adds PGP support to webmail like Gmail, Yahoo mail and others.

Until recently, Mailvelope did everything *inside* the browser, including storing your keys. That makes it difficult to integrate with Fluidkeys (which currently stores keys in GnuPG).

Mailvelope recently released a [new version](https://www.mailvelope.com/en/blog/mailvelope-3.0) which uses [native messaging](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Native_messaging) to communicate out of the browser to GnuPG.

Since Fluidkeys pushes into GnuPG, in theory that change means that Mailvelope should now *just work* with Fluidkeys, which is pretty exciting.

![Mailvelope compose email window](/images/2019-01-18-mailvelope-fluidkeys-gnupg.png)

We spent some time this week compiling the latest GnuPG for Ubuntu 18.04 (unfortunately Ubuntu ships old versions of GnuPG) and seeing how it feels using Fluidkeys + Mailvelope as an email encryption solution.

It wasn't seamless, but it was a good spike and I think there's promise for this sort of integration. Fluidkeys could automate the installation and configuration of third-party apps like Mailvelope, leveraging the existing community of open source tools.

## Automated signing commits with git and Github

In the same spirit, we built a proof of concept to automatically configure `git` and Github for signing and verifying commits. There's a few moving parts to get that "Verified" badge on Github and it seems Fluidkeys can turn this into a simple five minute task.

<pre class="terminal">
<span class="prompt">></span> fk git setup
Fluidkeys will configure git, GnuPG and Github to sign and verify
commits and tags.

You'll see ☑ Verified on Github and you'll be able to check
signatures locally using <span class="information">git --verify</span>.

 ▸   Git is configured to commit as paul@example.com
 ▸   Fluidkeys has a PGP key for paul@example.com

Fluidkeys will:

     [ ] Configure git for signing:

         user.signingkey        => 309F635DAD1B5517
         commit.gpgsign         => true
         tag.forceSignAnnotated => true
         gpg.program            => /usr/bin/gpg2

     [ ] Ask you to create a Github personal access token
     [ ] Check paul@example.com is listed in your Github account
     [ ] Upload the public key to Github
     [ ] Check if your organisations have Fluidkeys for Teams
     [ ] Fetch public keys for everyone in your organisation

Configure git, gpg & Github for <span class="information">paul@example.com</span> [Y/n]
</pre>

## Started work on Fluidkeys for Teams proposition

We started articulating what you actually get with Fluidkeys for Teams, how it looks and how it works.

Until now we've struggled to a think about the difference between Fluidkeys for Teams versus Fluidkeys for *individuals* — what should you be able to do with or without a team?

Ian had an insight that really none of Fluidkeys makes sense for individuals: there's little point signing and verifying your own commits, or sending yourself secrets.

With that in mind, it's hugely simplified how we think about Fluidkeys.

In the 1.0 release, Fluidkeys will be more akin to Slack than, say, Thunderbird. The core concept will be the team. In the same way as Slack, perhaps there'll be a concept of a *visitor* or guest account that can interact with a team, but we think that'll be the limit.

We're working on some pages to illustrate Fluidkeys for Teams and in the next couple of weeks we'll be getting out there testing whether it resonates with the teams we're already talking to. Exciting!

Thanks for reading.

— Paul

*All* feedback is welcome, pop us an email to
[hello@fluidkeys.com](mailto:hello@fluidkeys.com)
