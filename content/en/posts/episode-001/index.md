+++
title = "Episode 001 - Cloudflare Went Down and the World Stopped!"
date = "2025-12-26"
description = "Starting from the Cloudflare global outage, we discussed infrastructure dependencies, the unwrap() bug in Rust, the microservices vs monolith debate, and Murphy's Law."
youtube_url = "https://youtu.be/GNZnbC31MX8"
youtube_id = "GNZnbC31MX8"
duration = "34:19"
tags = ["cloudflare", "rust", "microservices", "monolith", "distributed systems", "infrastructure", "Murphy's law", "resilience", "API gateway"]
notebooklm_url = "https://notebooklm.google.com/notebook/1951d774-a8d5-466b-9149-270ea728172f"
draft = false
+++

## Summary

In the first episode of the series, we started with the Cloudflare outage — a real event that shook the internet. A simple `unwrap()` call in Rust brought down infrastructure serving 20% of the internet. From there we explored the risks of single points of failure, the security of undersea cables, the microservices vs monolith debate, and why Netflix and Amazon are pulling back. The verdict: Murphy's Law has been with us since the dinosaur age!

## Video

{{< youtube GNZnbC31MX8 >}}

## Topics

- Why did Cloudflare go down? How did a simple `unwrap()` in Rust turn into a global crisis?
- With 20% of internet traffic behind a single service, how safe are we really?
- Undersea cables, sharks, and NATO missions
- Microservices vs monolith: why are Netflix and Amazon stepping back?
- The real cost of distributed systems and the transaction nightmare
- Murphy's Law has been with us since the dinosaur age!

## Deep Dive

### Cloudflare Went Down: 4 Truths About the Internet's Fragile Foundation

#### Introduction: The Moment the Digital World Froze

We tend to assume the internet just works — until it doesn't. The recent Cloudflare outage was one of the most jarring reminders of how fragile our digital infrastructure really is. With roughly 20% of internet traffic — nearly one in five websites — sitting behind a single service, centralized systems have become textbook single points of failure. The deeper our daily lives and businesses are wired into these massive systems, the more we hang by a thread.

#### Even Rust Can't Stop Human Error: The Unwrap Incident

When we dig into the technical details of the Cloudflare outage, we find Rust — a modern, "safe" language. While Rust is revolutionary in terms of memory safety, it cannot eliminate the weakest link: human error. At the center of the outage was a misuse of Rust's `unwrap()` method.

During development, engineers often use `unwrap()` as a shortcut — essentially saying "I'm certain this will return a valid value." But when that code hits production and encounters an unexpected condition, Rust panics and halts the entire process.

> "Murphy's Law has been with us since the dinosaur age. No matter how resilient we think we've made our systems, the simplest developer mistakes can cause massive failures."

In software architecture, what matters isn't how safe the language is — it's whether the developer handles that 1% edge case.

#### The Physical Fragility of the Internet: Cables, Sharks, and the Deep Ocean

Thinking of the internet as an abstract "cloud" means ignoring real-world infrastructure risks. The digital world depends on thousands of kilometers of physical backbone cables running across ocean floors. NATO has even assigned the Swedish navy to patrol these cables in the North Sea using drones and submarines.

And it's not just sabotage — there are unexpected actors too: sharks. Shark attacks on undersea cables have disrupted intercontinental connectivity. For an architect, this means **High Availability** and **Disaster Recovery** planning must go beyond software — covering physical and geopolitical dimensions as well.

#### API Gateway as a Resilience Shield

When communicating with external systems in complex architectures, using an **API Gateway** instead of direct connections is a lifesaver. The gateway acts as an abstraction layer between systems, and more importantly, serves as a **resilience shield**. When an external system slows to a crawl or times out, the gateway absorbs the impact and prevents your local system from cascading into chaos.

#### Microservices vs Monolith: The Complexity Trap

The rush to split everything into microservices has left many teams drowning in complexity. The moment you go distributed, you face a massive cost: **Transaction Management**. Data consistency that was once handled in a single operation in a monolith becomes a nightmare in a microservices world.

It's no coincidence that giants like Amazon and Netflix are starting to pull back toward **Modular Monolith** architectures in certain critical areas. "Don't go microservices without first building a solid monolith" should be our guiding principle.

#### Conclusion: Are You Ready for the Next Outage?

No matter how modern our languages, no matter which cloud providers we trust with our systems, risk never goes away. Human error, physical sabotage, and architectural complexity are always lurking. Distributing responsibility correctly, choosing the right protocols, and always having a Plan B — these are the only ways to stay standing in the digital world.

## Infographic

<a href="infografik.png" target="_blank" rel="noopener noreferrer">![Lessons from the Cloudflare Outage: System Resilience and Architecture Strategies](infografik.webp)</a>

## Audio Summaries

### Brief Summary
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-001/audio-brief.m4a" >}}

### Deep Dive
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-001/audio-deepdive.m4a" >}}

---

📓 [Explore the NotebookLM workspace for this episode](https://notebooklm.google.com/notebook/1951d774-a8d5-466b-9149-270ea728172f)
