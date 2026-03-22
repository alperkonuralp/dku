+++
title = "Episode 010 - Are We Fitting Problems to Solutions? Déjà Vu in Tech!"
date = "2026-03-22"
description = "We talked about the cyclical nature of time in technology. The same problems keep appearing under different names. Even Spotify went back from microservices to modular monolith!"
youtube_url = "https://youtu.be/NVrLpP61lqA"
youtube_id = "NVrLpP61lqA"
duration = "31:17"
tags = ["hype cycle", "microservices", "monolith", "design patterns", "transaction", "vendor lock-in", "POC", "MVP", "loose coupling", "artificial intelligence"]
notebooklm_url = ""
draft = false
+++

## Summary

We talked about the cyclical nature of time in technology. The same problems keep reappearing under different names — we call this "Déjà Vu in Tech." Even Spotify went back from microservices to modular monolith! The headache we solved 10 years ago with a simple `begin transaction` came back to haunt us with microservices in the form of saga pattern and outbox pattern. Design patterns are timeless, but hypes are temporary. Don't let AI catch the fish for you — learn to catch it yourself.

## Video

{{< youtube NVrLpP61lqA >}}

## Topics

- Déjà Vu in Tech: Why are we always in the same cycle?
- Are we fitting problems to solutions, or seeking solutions to problems?
- Microservices → Monolith → Modular Monolith: Even Spotify went back!
- Library dependencies and the importance of loose coupling
- The transaction concept: the headache we solved 10 years ago is back
- Why are design patterns timeless?
- POC and MVP: Test before falling for the hype!
- Let AI teach you to fish — you do the fishing!
- The vendor lock-in danger and security vulnerabilities

## Deep Dive

### Déjà Vu in the Tech World: Are We Fitting Problems to Solutions?

#### Introduction: The Repeating History of Technology

Looking back as an architect with over 20 years in the software world, I see how dynamic yet deeply cyclical time is. Many approaches presented as "revolutions" today are simply topics we debated, solved, and sometimes shelved under different names fifteen to twenty years ago.

Focusing only on the new without adding past experiences to our toolkit pushes us to make the same mistakes with more modern and more expensive tools.

#### Boarding the Hype Train: Are We Fitting Problems to Solutions?

The biggest danger in today's software ecosystem is selecting a technology based on its hype level rather than its engineering merit. Architectural practices that giants like Netflix, Spotify, or Amazon developed for their own massive scale are often stripped of context and marketed as "the one truth" for companies of every size.

Instead of looking for a tool to solve an existing problem, we start inventing a problem to fit the popular tool at hand.

> "We have a solution; let's go and find the problem we can apply this solution to."

#### The Microservices Paradox: The Return of Problems Solved 10 Years Ago

Microservices promised us scalability but brought an operational nightmare along with them. Data consistency that we handled in monolithic systems with a single `begin transaction` and `commit` command 10 years ago has become the biggest pain point of distributed systems today.

**The Distributed Transaction Dead End:** Structures once managed with tools like MSDTC became history with the transition to the Linux and Container world. This forced us into much harder and more costly constructs like Saga Pattern or Outbox Pattern.

**Operational Anxiety:** Questions like "Did the data go through? Is it synchronized?" are no longer just technical details — they are the main source of phones ringing in the middle of the night and never-ending synchronization errors.

#### The Dependency Trap: Vendor Lock-in

Placing a library at the center of a project without an abstraction layer in between is "marrying" that vendor. And in this marriage, the cost of divorce is sometimes rewriting the entire project from scratch.

The risk isn't limited to performance — security and licensing costs are also part of this dependency trap. The solution is always the same: **Loose Coupling** and proper **Abstraction**.

#### The Return of the Giants: Why Did Spotify Switch to Modular Monolith?

The fact that Spotify — the "poster child" of microservices — is now moving toward Modular Monolith structures is a lesson for the entire industry. This isn't a step backward; it's a sign of maturity. The operational cost of managing millions of pods, the headaches caused by network traffic, and data consistency issues pushed even the giants to consolidate SOA principles under a monolithic roof.

A well-designed modular monolith is always more efficient and sustainable than a poorly designed pile of microservices.

#### Engineering in the AI Age: Learning to Fish

AI has brought a new breath to the industry, but it hasn't reduced the need for fundamental engineering discipline — if anything, it has increased it. AI can write code fast, but detecting whether that code "left a bomb in memory" still requires human intelligence and discipline.

- **AI as a POC Tool:** Use AI to see the impact of a new technology. Have it quickly prepare a Proof of Concept and test it.
- **Disciplined Engineering:** Having AI write code without knowing design patterns and SOLID principles is an uncontrolled force.
- **Learning Approach:** Let AI teach you to fish — you do the fishing.

#### Conclusion: Set Aside the Excitement, Use a Checklist

Before making an architectural decision, ask yourself these questions:

- Will I be able to test this structure easily?
- How much more complex will the deployment process become?
- How does the system respond under load?
- How deeply am I tied to this tool?
- Does the external instrument I'm using harbor a security vulnerability?

Is that modern solution you're applying with excitement today a new problem you'll have to solve tomorrow, or is it genuinely the key you need?

## Infographic

{{< infografik src="infografik.webp" alt="Déjà Vu in Tech: Are We Fitting Problems to Solutions?" >}}

## Audio Summaries

### Brief Summary
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-010/audio-brief.m4a" >}}

### Deep Dive
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-010/audio-deepdive.m4a" >}}

---

📓 The NotebookLM workspace for this episode will be added soon.
