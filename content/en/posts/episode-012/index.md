+++
title = "Episode 012 - Dinosaurs on the Package Hunt! Welcome to Dependency Hell"
date = "2026-04-19T10:00:00+03:00"
description = "The invisible nightmare of the modern developer: Dependency Hell! 3.1 million packages on NPM, the Axios attack, the absurdity of the 'everything' package, the Shai-Hulud worm, and the Notepad++ risk — welcome to package hell."
youtube_url = "https://youtu.be/N_mIqIcfMoQ"
youtube_id = "N_mIqIcfMoQ"
duration = "31:20"
tags = ["dependency hell", "package hell", "npm", "nuget", "axios", "package manager", "supply chain attack", "software security", "dependabot", "shai-hulud", "open source", "javascript", "node.js"]
notebooklm_url = "https://notebooklm.google.com/notebook/dcb9a3a5-8d23-43ea-95d7-43e9c94d406d"
draft = false
+++

## Summary

In episode 12, we tackled the invisible yet inescapable nightmare of the modern developer: **Dependency Hell**. With 3.1 million packages on NPM and 895 billion downloads on NuGet, everything we use is actually woven from other people's code. From the absurd story of the "everything" package to Axios's 100+ million weekly downloads, from the Shai-Hulud worm to the Notepad++ incident — we discussed the good, the bad, and the ugly of the package world. The conclusion: there's no escape, but survival is possible with the right strategy.

## Video

{{< youtube N_mIqIcfMoQ >}}

## Topics

- Why package managers have become an inseparable part of our lives
- The package world in numbers: NPM, NuGet, Crates, PIP, Gem
- 3.1 million packages and 17 million developers: the scale of the NPM ecosystem
- The "everything" package: the art of filling your disk with a single `npm install`
- Version conflicts and the birth of Dependency Hell (Axios 1.0 vs 1.1)
- Linux package managers and the App Store analogy
- The Axios security vulnerability and the 2025-2026 wave of attacks
- The Qix case and the hijacking of maintainer accounts
- Shai-Hulud: NPM's first self-propagating worm
- The two faces of AI: writing attack code and reducing our skepticism
- Dependabot, CVE bulletins, and PR automation
- The "one version behind" strategy
- The Notepad++ incident: risk now reaches the end user
- ThoughtWorks Tech Radar: seeking industrial validation
- GitHub Actions and the `pull_request_target` danger
- Escape strategies from hell and the defensive value of `package-lock.json`

## Deep Dive

### Welcome to Package Hell: The Invisible Dangers of the Modern Software World

#### 1. Introduction: Invisible Dependencies and the Modern Developer's Curiosity

In the modern software development world, none of us start from a blank slate anymore. Let's face the bitter truth we put on the table in this DKU episode: Writing code today is essentially applying a thin layer of polish over a massive pile of "other people's code."

But have you ever asked yourself: when you write just three lines of logical code and hit the compile button, how does that enormous `node_modules` folder end up taking megabytes — sometimes even gigabytes — of disk space? This is the first layer of the invisible, chaotic web we call **Dependency Hell**. For a modern developer, curiosity is no longer just about building algorithms; it's about having the cyber-awareness to ask: "Who has injected what into this code without my knowledge?"

#### 2. The "Everything" Package and Dependency Bloat

The number of packages in the NPM ecosystem has exceeded 3.1 million, and the community keeps multiplying these numbers every day. But this speed brought with it an uncontrollable phenomenon we call **bloatware**. The "everything" package case we discussed in the episode is the most tragicomic example: when you install a single package out of curiosity, the sub-dependencies spiral out of control, and you find yourself unknowingly downloading nearly all of NPM to your disk.

Let's put the size of this massive ecosystem into perspective with some numbers:

| Platform | Package Count | Total / Weekly Download Example |
| -------- | ------------- | ------------------------------- |
| NPM | 3.1 Million+ | Axios: 100+ Million Weekly |
| NuGet | 500K+ | 895 Billion+ (Total Downloads) |
| NuGet (Newtonsoft.Json) | — | 284 Million Downloads (single package) |

> "We're taking packages and using them without questioning... We need to stop and ask: 'Does this package really need that many sub-dependencies?'"

#### 3. The Trust Paradox and Maintainers as Targets

As developers, we place unshakable trust in packages downloaded millions of times per week. However, the **Qix case** in September 2025 showed just how fragile this trust is. The account of Qix — maintainer of foundational libraries like `chalk` and `color-convert` — was compromised through a fake "2FA reset" phishing email.

The scary part: Qix co-maintained these packages with Sindre Sorhus, one of NPM's most prolific contributors. By seizing Qix's account, attackers gained control over a "blast radius" of 2-3 billion weekly downloads. A single mistake by a maintainer in a moment of stress is enough to paralyze the entire global software supply chain.

#### 4. Versioning Strategy: Is the Newest Always the Best?

In the software world, the myth that "newest is best" can turn into a dangerous misconception when it comes to security. The **"stay one version behind"** strategy we recommended in the episode is actually a modern survival guide.

The freshest example is the **Axios 1.14.1 incident** from March 31, 2026. The North Korea-linked UNC1069 group hijacked the Axios maintainer account and planted a backdoor named `plain-crypto-js` into the package. Those who updated immediately in their desire to stay "cutting edge" welcomed the WAVESHAPER.V2 malware — running on Windows, macOS, and Linux — into their systems. Those who stayed cautious and delayed the update read about the disaster only as a news story.

#### 5. The Weaponization of Build Environments

Attackers are no longer sneaking into just the code, but into the build processes where that code is packaged — the kitchen itself. The **Ultralytics** and **s1ngularity (Nx)** cases demonstrated how deadly "script injection" vulnerabilities on GitHub Actions can be.

The monster hiding in the technical details is the `pull_request_target` trigger. An unsanitized Pull Request title, combined with this trigger, hands the attacker a write-privileged `GITHUB_TOKEN`. With this privilege, attackers can infiltrate the build process and drop payloads onto your terminal — like the innocuously named `sudo shutdown -h 0` that can brick a system.

Even worse is the **Shai-Hulud worm** that emerged in September 2025. This is the first successfully self-propagating worm attack in the NPM ecosystem. Shai-Hulud isn't just a secret stealer; it's a "package-poisoning machine" that uses captured NPM tokens to automatically publish malicious versions of every package the victim has access to. Imagine waking up one morning to find all your private repos public — that's exactly what Shai-Hulud does.

#### 6. AI: The Attacker's New Right Hand

AI isn't just helping us write code — it's also automating the reconnaissance process for attackers. As seen in the s1ngularity case, attackers are using AI CLI tools installed on developer machines, like Claude, Gemini, and Q, as weapons.

Malware that manipulates AI tools using flags like `--dangerously-skip-permissions` or `--yolo` can scan the file system for sensitive information, SSH keys, and wallets within seconds. In a world where code is increasingly produced by AI rather than humans (and often deployed without review), lowering our skepticism with an "AI handled it anyway" attitude is throwing the gates of hell wide open.

#### 7. Conclusion: Escape Strategy from Hell

To avoid burning in package hell, we must "cut our coat according to our cloth." We need to act with a concrete strategy:

1. **Version Pinning:** `package-lock.json` is not just a file — it's a line of defense.
2. **Audit Your Automation:** Don't blindly merge every PR that Dependabot opens.
3. **Internal Frameworks:** For critical business logic, minimize external dependencies and build your own internal libraries.
4. **Industrial Standards:** Adopt approaches (with tools like Wiz or Socket) that bring the unruly freedom of the open source world under discipline, like ISO standards in automotive.

In a world where a package downloaded 100 million times a week can wake up "poisoned" one morning, and worms like Shai-Hulud automatically invade repositories, what code can we really trust? Perhaps the only safe path is to look at every dependency with suspicion — as if it might sell you out one day.

## Infographic

{{< infografik src="infografik.webp" alt="Dinosaurs on the Package Hunt - Episode 12 Infographic" >}}

## Audio Summaries

### Brief Overview

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-012/audio-brief.m4a" >}}

### Deep Dive

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-012/audio-deepdive.m4a" >}}

## Resources

- You can also explore this episode's content on [NotebookLM](https://notebooklm.google.com/notebook/dcb9a3a5-8d23-43ea-95d7-43e9c94d406d).
