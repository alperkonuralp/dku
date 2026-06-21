+++
title = "Episode 018 - Which Programming Language Is the Best?"
date = "2026-06-21T10:00:00+03:00"
description = "Is there really a 'best' programming language? From a language's philosophy and DNA to the birth of threads and new-generation languages, we explore why asking the right question beats crowning a winner."
youtube_url = "https://youtu.be/XZRB4LqJouU"
youtube_id = "XZRB4LqJouU"
duration = "34:51"
tags = ["programming languages", "software", "software engineering", "c#", "python", "rust", "zig", "gleam", "thread", "parallel programming", "object-oriented programming", "dotnet", "dku", "best programming language"]
notebooklm_url = "https://notebooklm.google.com/notebook/0cec889d-7664-4e34-9a1f-adef22314973"
draft = false
+++

## Summary

In this episode we stepped away from AI for a while and went back to the roots of software, putting the question that has fueled forum wars and office debates for years on the table: "Which programming language is the best?" Before answering, we questioned the question itself — because there is no single champion that rules over every domain. Languages aren't piles of syntax; they are living ecosystems with their own histories, philosophies, and "DNA." Where we landed: **the real issue isn't the "best language" but being able to choose the language whose philosophy fits the problem you're trying to solve.**

## Video

{{< youtube XZRB4LqJouU >}}

## Topics

- Why isn't there a single "best programming language"?
- The right question: "which language is right for this project?"
- Stepping away from AI, back to the roots of software
- Every language has a philosophy and a "DNA"
- The origin of object-oriented programming: the 1960s, the University of Oslo, and `Simula`
- Simula's philosophy + C's compiler = the birth of `C++`
- The method overloading example: not a technical limit, but a philosophical stance
- The "fanboy" trap and professional pragmatism
- The Python paradox: undeniable in the AI ecosystem even if you dislike its syntax
- Right tool, right job: AI/data, parallel processing, system level
- Hardware evolution: from single-core to multi-core
- From "time slicing" to real parallelism: the birth of the `thread`
- Not the language but the ecosystem: why standard libraries matter
- How knowing one language deeply speeds up learning new ones
- How 20+ years with `C#`/`.NET` builds pattern recognition
- Comparing the memory types of agentic systems with human memory
- New languages will keep coming: `Rust`, `Zig`, `Gleam` and Stack Overflow surveys
- Even AI ultimately has to work through a language
- Respect for the low level: trying to draw a window in `C` or Assembly

## Deep Dive

### The End of the Search for the "Perfect Language"

We opened the episode with the question every developer asks early on: "Which language should I learn?" — or its slightly bolder cousin, "Which programming language is the best?" As two "dinosaurs" who have been in this business for over two decades, we can comfortably say that the rush to crown a "winner" is usually a sign that we're asking the wrong question.

There are hundreds of languages out there, and popularity lists show every month how their rankings shuffle. But the point isn't to declare a champion; it's to understand why these languages exist, which need gave birth to them, and how they shape the very nature of software. Seeing a language not just as a tool but as a solution architecture and a way of thinking is the first step to finding your way through the crowd.

### 1. It's the DNA and Philosophy, Not the Name

Focusing only on syntax when learning a language is like judging a book by its typeface and missing the story. Behind every language lies a deep "DNA" and a particular philosophy. Why a language does or doesn't support `method overloading`, for instance, isn't just a technical detail; it reflects how its designers see the world. Some languages insist, "the signature has to differ too" — that's not a limitation, it's a deliberate stance.

Trace this genetic heritage and you end up in the 1960s, at the `Simula` seeds planted at the University of Oslo. That's where the first spark of object-oriented philosophy ignites. Years later, the architects of `C++` took that philosophy and fused it with the raw power of C's compiler, producing a hybrid that stays close to the machine while still taming complexity. As Alper puts it, languages always have this quality of drawing inspiration from somewhere, taking another language's idea and reinterpreting it for a new problem.

> It is often more meaningful to have an idea about the philosophy and DNA of a language before you even learn its name.

Once you understand the philosophy, you stop fighting the compiler; you start seeing why it pushes back where it does.

### 2. The "Fanboy" Trap and the Python Paradox

One of the biggest mistakes in software is clinging to a single language with near-religious devotion, regardless of what the project needs. We call this the "fanboy trap." In professional life, pragmatism beats preference; every language has a domain where it shines and a boundary where it struggles.

A nice paradox shows up here. Alper openly admits he isn't a fan of `Python`'s syntax — yet he also acknowledges that Python is the undisputed king of the AI and large language model world. If you're building something on the AI side, ignoring Python over aesthetic gripes would be a professional failure. The libraries, the community, the ready-made models — that ecosystem is simply too powerful to dismiss. We pick a tool because it does the job best, not because we "love" it.

The reverse holds too: especially in heavily `thread`ed, parallel workloads, forcing everything through Python instead of reaching for other languages is a mistake. Right tool for the right job:

| Domain | Preferred languages | Key strength |
| --- | --- | --- |
| AI / data | `Python` | Ecosystem and library richness |
| High concurrency / parallelism | Languages designed to manage multiple cores | True parallel processing |
| System level / performance | `C++`, `Rust` | Closeness to hardware, control |

### 3. Hardware, the Invisible Architect

We often treat programming as an abstract logic puzzle, when in fact the "metal" our languages run on drives their evolution. We used to work with a single processor, a single core. We "simulated" multitasking: slicing the processor's time into tiny pieces and giving each app a turn, so the computer appeared to do many things at once.

Then core counts grew, and a single processor block came to hold multiple processors. Languages had to evolve from managing "perceived" multitasking to managing real parallelism across cores. As Burak reminds us, there was a time when the concept of a `thread` didn't even exist; later it settled in and moved to the center of our languages.

Sometimes adding features to an old language isn't enough; you need a clean break. Part of the rise of languages like `Rust` is exactly this: an approach that puts memory safety at the heart of the design from the very start. On hardware with no operating system — "bare metal" — you often have to set the standard library aside and talk directly to the architecture, a shift in mindset that high-level frameworks usually hide from us.

### 4. Deep Roots, Fast Branches

There's a persistent myth: "Specialize in one language too long and you'll become obsolete." Our experience says the opposite. Spending twenty years with a language like `C#` doesn't just make you a C# expert; it builds a deep capacity for pattern recognition.

When a "dinosaur" looks at a new language, they don't see alien syntax; they see how that language solves universal problems. "How does this handle dependencies — like `Maven` in Java, or a `.NET` solution template?" In Alper's words, when he looks at a language he doesn't know, he maps it — "in `.NET` it was like this, in Java like that, in `PHP` it was this" — and grasps it far faster. Push your experience to its peak in one place while keeping an eye on "what else is out there," and you've got a powerful accelerator.

To appreciate how far we've come, it's worth treating Assembly as a kind of "sport" now and then. Today we draw an interface in seconds; but anyone who has tried to hand-write a window, a button on it, and a pop-up that opens on click in `C` or Assembly understands the value of modern tools on a whole different level.

### 5. Even AI Needs a Syntax

In this new era, some claim the age of the programmer is ending. We disagree. Even as agentic systems — autonomous AI tools that can carry out a task on their own — grow more independent, they still depend on an "execution layer." When an AI agent does a job, it doesn't wish it into existence; it writes and runs Shell scripts, `Python`, or `JavaScript` to talk to the hardware and the operating system. If Python is available in the environment, it reaches for it immediately.

If AI learns these languages to get its work done, then we are the ones who must stay masters of that execution layer: the side that verifies, controls, and architects what the AI generates.

From here we took a pleasant detour: the philosophical resemblance between the memory types of agentic systems and human memory. The experience we accumulate over years sits in our "long-term memory," while our speed at learning new things depends on the "short-term memory" that shifts past a certain age. Short-term memory, long-term memory, experiential memory — they line up surprisingly well with the memory layers of AI.

### 6. Conclusion: Don't Be Afraid to Seek a Challenge

Locking yourself inside one language is like watching the world through a single window. Producing solutions under the constraints of different languages stretches the mind and enriches your perspective. New languages will keep coming; someone will dislike a language's philosophy, sit down, write their own compiler or interpreter, and release it as open source. And when it catches on, names like `Gleam`, `Rust`, and `Zig` suddenly climb the Stack Overflow surveys. Hardware is changing too; in a world where quantum brings probability into the picture and we step beyond the binary of one and zero, entirely different languages may speed things up.

We closed with Burak's lovely line: if even AI is learning a programming language, then we absolutely must learn one too. The point isn't to memorize the syntax of the trendiest language; it's to stay curious and seek out challenges. The real question is this: are you choosing your next language by looking at a popularity contest, or by the philosophy of the problem you're trying to solve?

## Infographic

{{< infografik src="infographic.webp" alt="Which Programming Language Is the Best? - Infographic" >}}

## Audio Summaries

### Brief Summary

{{< audio src="https://media.dinozorlarlakafautuleme.com/episode-018/audio-brief.m4a" >}}

### Deep Dive

{{< audio src="https://media.dinozorlarlakafautuleme.com/episode-018/audio-deepdive.m4a" >}}

## Resources

- [NotebookLM notebook](https://notebooklm.google.com/notebook/0cec889d-7664-4e34-9a1f-adef22314973)
- [Simula (Wikipedia)](https://en.wikipedia.org/wiki/Simula)
- [Stack Overflow Developer Survey](https://survey.stackoverflow.co/)
