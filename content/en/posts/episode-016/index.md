+++
title = "Episode 016 - Hit Hard by Quantum"
date = "2026-05-24T14:00:00+03:00"
description = "Two software dinosaurs took on quantum and got hit hard. From superposition to Q-Day, from route optimization to post-quantum cryptography: where does quantum actually help, and where doesn't it?"
youtube_url = "https://youtu.be/f0aCiMvyDMY"
youtube_id = "f0aCiMvyDMY"
duration = "43:58"
tags = ["quantum", "quantum computing", "qubit", "superposition", "schrodinger's cat", "post-quantum cryptography", "q-day", "encryption", "route optimization", "ibm quantum", "quantum security", "software", "technology", "artificial intelligence"]
notebooklm_url = "https://notebooklm.google.com/notebook/5305a0c1-336d-4e27-84be-c5c5930d5870"
draft = false
+++

## Summary

As two "software dinosaurs" who have spent 22 years in IT, in the deterministic world of 1s and 0s, this week we took on quantum and frankly got hit hard. Superposition, Schrödinger's cat, how measurement collapses everything, the factorial explosion of possibilities in route optimization, the Q-Day threat, and post-quantum cryptography... Without drowning in detail, we chased one question: "when do you actually need quantum?" The conclusion is clear: **quantum is not a magic wand that solves every problem; it's the art of matching the right problem with the right tool.**

## Video

{{< youtube f0aCiMvyDMY >}}

## Topics

- Software dinosaurs facing quantum: why do "fireworks go off" in our heads?
- The current state of the quantum world: the excitement and rawness of the punch-card era
- IBM Quantum Composer and cloud-based quantum access
- Running quantum algorithms with Qiskit without knowing the subatomic details
- Superposition: the spinning coin-toss analogy
- The double-slit experiment and Schrödinger's cat
- Measurement and "collapse": how observation changes reality
- Einstein's "God does not play dice" resistance
- Route optimization: 20 stops, ~2.43 quintillion possibilities
- Quantum's real power isn't speed, but handling the entire possibility space at once
- Optimization examples from Ford to a textile workshop
- Q-Day and the "harvest now, decrypt later" threat
- Why migrating to post-quantum cryptography is a matter of survival
- IBM Quantum Readiness Index 2025: 11% R&D share, 53% ROI expectation
- The hardware dead end: noise, physical vs logical qubits
- Quantum ≠ always faster: the right problem, the right scale
- A hybrid future: classical and quantum systems intertwined

## Deep Dive

### 1. Introduction: Going Beyond 1s and 0s

As developers who have clocked 22 years in IT, who wore out our elbows in the corridors of C++ and Assembly, we always saw the world clearly: either 1 or 0. But quantum asks us to set aside the deterministic logic patterns of a quarter-century. As Burak kept repeating throughout the episode, the more you discuss the topic, the more explosions go off in your mind. When you first encounter quantum's "German-sounding" concepts — **entanglement**, for instance — questioning everything you know is almost inevitable.

> "Quantum is genuinely a topic that's hard to grasp and hard to explain... explosions go off in my head."

If you're curious why entanglement isn't a mysterious "remote connection" but the inevitable consequence of a shared quantum state, our guide's [Entanglement chapter](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/07-dolasiklik-entanglement/) covers exactly that.

### 2. The Quantum World Is Still in Its "Infancy"

The current state of quantum technology resembles software's early years crawling along with punch cards: exciting, but just as raw. The good news is that, unlike in the dinosaurs' day, we don't have to reinvent the wheel every time. Today, cloud-based interfaces like `IBM Quantum Composer` bring 2-3 qubit machines right into our homes; thanks to libraries like `Qiskit` on Python, we can run quantum algorithms without knowing every detail of what happens at the subatomic level.

The real issue right now is less the hardware itself than mastering this new language — quantum's probabilistic grammar. Because this technology is no magic wand that solves every problem; it's the art of matching the right problem with the right tool.

> Note: An interesting example Burak came across after we recorded the episode — [SPINQ Triangulum II](https://www.spinquanta.com/products-services/spinq-triangulum), a 3-qubit NMR quantum computer you can set up on your desktop. Turns out "quantum coming into our homes" is more literal than we thought.

### 3. As Long as the Coin Stays in the Air: The Power of Probabilities

At the heart of quantum lies superposition, which rejects the classical world. Toss a classical coin in the air and the result is either heads or tails. But in the subatomic world, until you look at that coin — until you measure — the coin is both heads and tails. Schrödinger's famous cat and the double-slit experiment tell us the same thing: in the microscopic universe, everything is a cloud of probabilities.

There's an important nuance here. "A qubit is both 0 and 1 at the same time" may be memorable, but it's technically incomplete; more accurately, before measurement a qubit sits in a combination of the probability amplitudes for 0 and 1. For those who want to see this distinction in depth, the guide's [Superposition](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/05-superpozisyon/) and [Measurement Problem](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/06-olcum-problemi/) chapters address exactly this.

Two points stood out:

- **Measurement and collapse:** Quantum effects disappear as you scale up to the macro world. The moment a system is observed — measured — that immense possibility space "collapses" into a single deterministic result.
- **Einstein's resistance:** Even Einstein resisted this probabilistic structure for years, saying "God does not play dice"; yet countless experiments showed that quantum works flawlessly at the atomic level.

### 4. The Optimization Monster: From Ford to a Textile Workshop

The real power of quantum computers isn't "fast processing" but the ability to handle the entire possibility space at once. Let's make this concrete with route optimization, where classical computers drown:

| Scenario | Number of Routes (Factorial) | Classical Computer |
|---|---|---|
| 3-stop delivery | 6 possibilities (3!) | Solves in milliseconds |
| 20-stop delivery | ~2.43 quintillion possibilities (20!) | Roughly 77 years, even at billions of routes per second |

The ~2.43 × 10¹⁸ space that 20 stops open up is, in practice, insurmountable for a classical machine. The quantum approach handles this immense space in a fundamentally different way. It's no coincidence that players like Ford in Türkiye are running optimization work in this area. And this isn't unique to giant industries: in a textile workshop, when a truck carrying fabric crashes, the answer to "what's the most profitable thing we can produce today?" waits to be sifted out from among thousands of variables — exactly the kind of problem where quantum shines.

We covered which problem classes are genuinely suited to quantum (and which aren't) in detail in the guide's [Use Cases](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/16-kullanim-alanlari/) chapter.

### 5. The Big Danger: "Harvest Now, Decrypt Later" and Q-Day

Quantum is both a revolution and a doomsday scenario for cybersecurity. **Q-Day** represents the day quantum computers will tear through today's encryption methods (RSA and the like) like paper. Attackers' current strategy is insidious: "harvest now, decrypt later." That is, they store your encrypted data today and will unlock it the day quantum becomes powerful enough.

Let's touch on the up-to-date figures we also corrected in the episode. According to the **IBM Quantum Readiness Index 2025**, the share of R&D that organizations allocate to quantum rose from 7% in 2023 to **11%**. Moreover, organizations preparing for quantum advantage by 2027 expect **53% higher ROI** by 2030. Investment varies markedly by sector, with areas like aerospace-defense and government standing out. Against this backdrop, migrating to post-quantum cryptography is no longer a luxury for companies, but a matter of survival.

Q-Day, the "harvest now, decrypt later" risk, and the migration roadmap toward the post-quantum standards NIST published in 2024 are explored in depth in the guide's [Cryptography and Post-Quantum Cryptography](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/17-kriptografi-ve-post-quantum-cryptography/) chapter.

### 6. The Hardware Dead End: Physical Qubits and Noise

So why don't we have phones with quantum processors in our pockets yet? Because these systems are extremely sensitive: heat, electromagnetic waves, or the slightest vibration (noise) disrupts the quantum state. Today the technology hovers roughly in the 100-qubit band; but the real issue isn't the number of physical qubits, it's logical qubit stability.

> "Quantum doesn't always mean speed... the problem has to be suited to it."

The hardware is so unstable that, to be sure of a computation's correctness, we have to combine multiple physical qubits and run them as a single logical qubit. Until this stability problem is solved, quantum will remain a hybrid force in specific domains where even supercomputers get stuck, rather than replacing the PCs in our homes. You can find why noise and error correction are the lifeblood of the field in the guide's [Noise, Decoherence and the Error Problem](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/13-gurultu-decoherence-ve-hata-problemi/) and [Quantum Error Correction](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/14-kuantum-hata-duzeltme/) chapters.

### 7. Conclusion: Looking at the Future Through a Quantum Window

Quantum computers weren't designed to write Word documents or browse the internet. They're coming to make the "impossible" possible — from molecular simulations in drug design to complex calculations in the defense industry. In the future, classical and quantum systems will work in an intertwined, hybrid structure. As transistors shrink to the atomic scale (the Ångström level), perhaps without even realizing it, we'll all become "quantum users."

**So what about you:** If you knew your data could be cracked 3-5 years from now, how would you architect your digital security today?

> In this episode we took a surface-level run at quantum. If you want to go deeper — from the math of superposition to the hardware race, from PQC migration strategy to the Türkiye perspective — the 25-part **[Quantum Computers: A Clear, In-Depth and Current Guide](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/)** (in Turkish) that we prepared together is waiting for you.

## Infographic

{{< infografik src="infograhic.webp" alt="Hit Hard by Quantum - Infographic" >}}

## Audio Summaries

### Brief Summary

{{< audio src="https://media.dinozorlarlakafautuleme.com/episode-016/audio-brief.m4a" >}}

### Deep Dive

{{< audio src="https://media.dinozorlarlakafautuleme.com/episode-016/audio-deepdive.m4a" >}}

## Resources

- [Quantum Computers: A Clear, In-Depth and Current Guide](https://dinozorlarlakafautuleme.com/blog/kuantum-bilgisayar/) — our 25-part guide (in Turkish) that serves as the in-depth follow-up to this episode
- [Audio/written summary of this episode via NotebookLM](https://notebooklm.google.com/notebook/5305a0c1-336d-4e27-84be-c5c5930d5870)
- [IBM Institute for Business Value — Quantum Readiness Index 2025](https://www.ibm.com/thought-leadership/institute-business-value/en-us/report/2025-quantum-computing-readiness)
- [NIST — First 3 Finalized Post-Quantum Encryption Standards (2024)](https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards)
- [SPINQ Triangulum II — 3-qubit desktop NMR quantum computer](https://www.spinquanta.com/products-services/spinq-triangulum)
