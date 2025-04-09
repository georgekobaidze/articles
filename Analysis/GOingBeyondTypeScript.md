# [Go-ing Beyond TypeScript: Microsoft Picks Go—How Will This Change the Landscape?](https://dev.to/georgekobaidze/go-ing-beyond-typescript-microsoft-picks-go-how-will-this-change-the-landscape-1p4h)

In the middle of March 2025, Microsoft introduced ["Project Corsa"](https://devblogs.microsoft.com/typescript/typescript-native-port/) an initiative that aims to port the TypeScript compiler **(tsc)** and toolset to native code using Google's **Go** programming language. [Anders Hejlsberg](https://github.com/ahejlsberg), the creator and lead architect of TypeScript (who also created C# programming language and several other great technologies), personally presented the project. In his talk, he briefly explained the reasons behind the decision and spoke about the estimated performance gains. Make sure to check out the video. it's valuable for multiple reasons:

* **Insights from the lead architect** – The main person behind the initiative explains the thought process behind this unexpected (but, as it turns out, reasonable) decision.

* **Technical depth** – Most of the content is intended for developers/engineers who want to understand and analyse the ongoing changes.

* **Live demo** – The presentation includes a short but interesting demo for comparing performance between the old and new approaches.

* **A huge step forward** – They expect a **10X** performance improvement, which is genuinely jaw-dropping.

{% embed https://youtu.be/pNlq-EVld70 %}

## The Ongoing Debate

Since the announcement, much has been said, written, and recorded about this topic. The tech community is still divided on this topic, which is understandable since it's just an initiative in progress. There are plenty of different opinions and questions regarding this topic, including but not limited to:

1. Why didn't they go with **Rust**?
2. Why didn't they go with **C#**?
3. Why are they porting it instead of rewriting it from scratch?
4. Is Microsoft investing in Go and killing off C#?
5. How will this impact TypeScript developers?
6. Should C# developers consider investing time in learning the Go programming language?

And many more...

These are all legitimate questions; however, they mostly come from controversial takes rather than pragmatic analysis. While controversy may be attractive to many, it's very rarely accurate. At the end of the day, we all should sit down and try to understand the real reasons behind such a major decision.

I want this article to be more than just plainly throwing out the facts we know so far. I'll share my take on this initiative, talk about decision-making process, and address the concerns surrounding this topic.

## Some Background Info About TypeScript

TypeScript was released to the public in **October 2012**, with version 0.8, after two years of internal development at Microsoft. It's essentially a superset of JavaScript, meaning it adds static types so that types are checked at compile-time. This addition helps catch errors early in the development process. Since its release, TypeScript has gained significant popularity due to its improved tooling support, type-safety, and better-maintainability.

TypeScript continues to be incredibly popular among developers to this day. In fact, it's getting more and more popular. According to Stack Overflow's annual developer surveys, TypeScript has gained a few positions in recent years:

| Year | Position | Source                                                                                            |
| :--: | :------: | :-----------------------------------------------------------------------------------------------: |
| 2020 | 9th      | [2020 Survey Results](https://survey.stackoverflow.co/2020#most-popular-technologies)             |
| 2021 | 7th      | [2021 Survey Results](https://survey.stackoverflow.co/2021#technology-most-popular-technologies)  |
| 2022 | 5th      | [2022 Survey Results](https://survey.stackoverflow.co/2022/#technology-most-popular-technologies) |
| 2023 | 5th      | [2023 Survey Results](https://survey.stackoverflow.co/2023/#technology-most-popular-technologies) |
| 2024 | 5th      | [2024 Survey Results](https://survey.stackoverflow.co/2024/technology/)                          |

TypeScript has consistently held 5th place for the last three years, just behind JavaScript, HTML/CSS, Python, and SQL. There's definitely no shame in being behind these languages.

![Top 20 Overall](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xiejnq87qw45wwfina5t.png)

In terms of the most "Admired and Desired" languages, TypeScript also maintains a solid 5th place.


![Top 20 Most Desired](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u2bfgdow4wmcqwakl40k.png)

## Then Why Change Something That Isn't Broken?

That's a great question that has a very simple and straightforward answer: **performance**.

The TypeScript compiler (tsc) is written in TypeScript itself (which makes it a self-hosting language). A compiler is essentially a software tool that translates code from a high-level programming language into a lower-level language (such as machine code) that a computer can execute. In the case of TypeScript, the compiler (tsc) converts TypeScript code into JavaScript. Unlike traditional compilers that generate machine code, tsc transforms code from one high-level language to another—a process known as **transpiling**.

As counterintuitive as it may seem, **TypeScript isn't the best language for writing a TypeScript compiler** (funny world, right?). But if we take a closer look, TypeScript (and JavaScript in general) is primarily optimized for UI and browsers rather than compute-intensive workloads. No single tool in software engineering can do it all, and TypeScript is no exception. Some languages are simply better suited for tasks like compiler development. JavaScript has reached its limits in this regard, it's a **JIT-compiled** language, meaning it's compiled at runtime rather than **ahead of time (AOT)**. The code must be translated into machine code before it gets executed. This approach introduces a significant startup overhead, as the program spends time compiling code before running, whereas AOT-compiled applications start instantly because they are already compiled into native machine code.

The team recognized a huge opportunity for improvement. In today's world, everything needs to happen as fast as possible because **time is money**. By not addressing this issue, Microsoft was essentially leaving money on the table, which is far from ideal. Anders Hejlsberg and his team began prototyping in several different languages, experimenting with Rust, Go, C#, and others. After thorough testing and number crunching, they concluded that Go was the language that best fit their needs. In the end, they achieved an astounding 10X performance improvement, which is incredibly significant.

## Why Not Other Languages?

Alright, everything so far sounds great, but let's address the elephant in the room—the question that everybody's asking: why not Rust, C#, or any other language? Especially considering that Go is a programming language created and owned by Google, another gigantic company often referred to as an "arch-enemy" of Microsoft. Why would Microsoft choose that language?

Well, first and foremost, we need to understand how decisions like this are made at companies like Microsoft. They can't just pick a tool just because it's hot and trending, especially for gigantic projects like TypeScript, you need to make sure that decisions are carefully analyzed, and only after thorough evaluation choose what works best. It's about finding the right balance among dozens, if not hundreds, of variables that could impact the decision.

These variables include, but aren't limited to, the following:

* What's the expected performance gain?

* Does the language support all the critical features needed for the project?

* What is the allocated budget for the project?

* How much time is available for implementation?

* How well do the team members know the language?

* How much time is required to learn and become proficient in the language?

* What are the other viable alternatives, and how do they compare in terms of benefits and trade-offs?

* Will the language be sustainable and maintainable in the long term?

* How compatible is the language with existing tools and technologies in the project's ecosystem?

* What's the community support and ecosystem around the language?

* What is the scalability potential of the language for future requirements?

* How easy will it be to integrate with other parts of the system or third-party services?

* What are the risks associated with adopting this language (e.g., lack of documentation, fewer libraries, or long-term support)?

* How does the language impact developer productivity and team collaboration?

And many more.

Second, every programming language is designed for a specific purpose, or many different purposes, which is why hundreds (if not thousands) of programming languages have been created throughout history. Even Google, despite having its own technologies, chose TypeScript for developing **Angular** because of its advantages over pure JavaScript. At the end of the day, it's all about using the right tool for the job. If a company insists on using only its in-house technologies, it risks missing out on better solutions and compromising the quality of its products—potentially leading to serious consequences. Microsoft simply chose the best tool available for the task, regardless of who developed it.

Speaking of the best tool, let's break down why they went for Go and not other languages.

To answer this question, we first need to understand that they're not rewriting the entire existing codebase—they're porting it (we'll discuss why they took this approach later in the article). The existing codebase makes several assumptions:

1. Automatic garbage collection:
Since the team is porting rather than rewriting everything from scratch, they couldn't pick a language with completely different memory management semantics. Automatic garbage collection was a critical requirement to ensure a smooth transition.

2. Concurrency support:
By concurrency, I mean shared memory concurrency. JavaScript doesn't have shared memory concurrency, which is one of the reasons it's not as efficient for this type of workload. The new language needed to provide concurrency features to handle parallel processing more efficiently.

And many more. But let's focus on these two for now.

Rust, as we all know, is a low-level programming language. In Rust there's memory management, although it's not automatic. Which basically means that if the team had chosen Rust, they would have had to rewrite a significant portion of the codebase, introducing major structural changes—something that would require much more time and effort than they could afford.

Besides, as we mentioned, Anders Hejlsberg and his team decided to **port** it, which basically means (in the simplest possible terms) keeping as much of the original code as possible while switching to a new language. In cases like this, you want the old and new languages to be semantically as close as possible to each other. Rust, however, is a completely different type of language compared to TypeScript. It's often referred to as a "modernized C++" for good reason—it shares many of C++'s low-level capabilities but with improved safety and modern features.

Now, why not C#?

Yes, C# is Microsoft's primary language. It's the language that I've used throughout my career. I love C#, it's awesome (in my personal opinion). Although I can admit that it's less than perfect for this particular job. Let's break down why:

1. **C# is a bytecode-first language,** meaning it's compiled into an intermediate bytecode (also known as Common Intermediate Language, or **CIL**) before it's executed. While Ahead-of-Time (AOT) compilation exists in C#, it isn't supported on all platforms and is still relatively new. It hasn't been time-tested for a project as large and complex as the TypeScript compiler, making it a risky choice.

2. **Just like Rust, C# is also fundamentally different from TypeScript.** Especially if we consider how TypeScript is written, which is mostly functional way. C# is a fully OOP language, which makes it not suitable for the job. In fact, if the team were to pick a .NET language, they'd likely choose F#, which is a functional language that aligns more closely with TypeScript's style. However, even F# isn't close enough, meaning it would still require a rewrite rather than a port.

Performance-wise, there's even a possibility that C# could outperform Go, but that's not the point. The decision was based on compatibility, ease of transition, and long-term maintainability, not just raw performance.

## So Why Go?
Now that we've covered why languages like Rust, C#, or even F# wouldn't be suitable, let's discuss why the team decided to go with Go.

Go supports shared memory concurrency. Using mechanisms like goroutines, channels, and mutexes. Which was one of the main assumptions that we listed earlier. As mentioned by Anders Hejlsberg himself, one of the main reasons why they reached 10X performance was the ability to use concurrency. The other half came from using native code. However, concurrency alone isn't enough to justify choosing Go—after all, plenty of other languages support it.

Another major reason is Go's functional approach. The current JavaScript codebase is written in a highly functional style. They use very few classes in the source code. In fact, the core compiler doesn't use classes at all. Go fits this description perfectly, because **Go is all about functions and data structures**.

On the other hand, there is one major difference: TypeScript has a much richer type system than Go. This sounds like a limiting factor, but in fact, Go has much better support for primitive data types, especially numeric types. Take a look at how TypeScript and Go compare in terms of numeric types.

### **1. Integer Types (Signed & Unsigned)**

| TypeScript Type        | Bit Size  | Range       |
|------------------------|-----------|-------------|
| `number` (JS `Number`) | 64-bit    | ±(2^53 - 1) |
| `bigint`               | Arbitrary | Unlimited   |

---

| Go Type  | Bit Size   | Range                                                   |
|----------|------------|---------------------------------------------------------|
| `int`    | 32/64-bit* | -2³¹ to 2³¹-1 (32-bit) or -2⁶³ to 2⁶³-1 (64-bit)        |
| `int8`   | 8-bit      | -128 to 127                                             |
| `int16`  | 16-bit     | -32,768 to 32,767                                       |
| `int32`  | 32-bit     | -2,147,483,648 to 2,147,483,647                         |
| `int64`  | 64-bit     | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| `uint8`  | 8-bit      | 0 to 255                                                |
| `uint16` | 16-bit     | 0 to 65,535                                             |
| `uint32` | 32-bit     | 0 to 4,294,967,295                                      |
| `uint64` | 64-bit     | 0 to 18,446,744,073,709,551,615                         |

---

### **2. Floating-Point Types**

| TypeScript Type        | Bit Size | Precision        | Range     |
|------------------------|----------|------------------|-----------|
| `number` (JS `Number`) | 64-bit   | 53-bit precision | ±(2^1023) |

---

| Go Type   | Bit Size | Precision     | Range    |
|-----------|----------|---------------|----------|
| `float32` | 32-bit   | ~6-7 digits   | ±(10³⁸)  |
| `float64` | 64-bit   | ~15-17 digits | ±(10³⁰⁸) |

---

### **3. Special Types & Constants**

| TypeScript Type  | Description                  |
|------------------|------------------------------|
| `Infinity`       | Positive Infinity            |
| `-Infinity`      | Negative Infinity            |
| `NaN`            | Not-a-Number                 |
| `BigInt`         | Arbitrary-precision integers |

---

| Go Type                       | Description                     |
|-------------------------------|---------------------------------|
| `math.MaxFloat64`             | Largest float64 value           |
| `math.SmallestNonzeroFloat64` | Smallest positive float64 value |
| `math.NaN()`                  | Not-a-Number                    |
| `big.Int`                     | Arbitrary-precision integers    |

This has had a significant positive impact on memory consumption. According to the team's estimates, memory usage has already been reduced by half compared to the current version.

## Why Aren't They Rewriting the Existing Codebase from Scratch?

TypeScript was released on **October 1st, 2012.** So by the time of writing this article (03/30/2025), it's been around for almost 13 years. 

Now imagine the scenario: you're working on a massive and extremely complex application that has been evolving for 13 years, used by a lot of important clients. Suddenly, your team is told to completely rewrite it in an entirely new technology that's completely different from what you've been using for years. If there were a horror movie about software engineering, this scenario would definitely make the scariest plot of all time. 

There are so many things that potentially can go wrong. In this particular case we're not talking about just an enterprise application that serves other services, we're talking about a programming language—one that is deeply embedded in the workflows of tens of thousands of companies. Some of these companies are absolute giants, including DoorDash, Canva, Revolut, IBM, Slack, JPMorgan Chase, and many more. Even the slightest incompatibility can cause major chaos in many companies, damaging Microsoft's reputation and eventually revenue.

Yes, rewriting the codebase from scratch can have a few advantages, like using the best tools possible for writing compilers, maximizing potential performance gains, etc. But as we discussed earlier, this decision isn't based on just one or two factors—there are hundreds of considerations. Among the most critical ones are **time and money** (which, in business, are essentially the same thing). It's much more practical to achieve a 10X performance gain in one year than to aim for 15X in ten years. The latter might give you better results in the long run, but the former provides significant improvements within a reasonable timeframe, allowing Microsoft to deliver faster and more immediate benefits.

When it comes to resources (money), I've heard a lot of discussions about how big and resourceful Microsoft is, capable of doing things faster and better than most other companies. Which is true—Microsoft is one of the powerhouses in the tech industry, although it still doesn't have all the resources in the world—it's still limited at some point. Every company, no matter how large, operates within certain constraints. This is especially true for individual teams and projects, which don't get unrestricted access to all of Microsoft's funding or resources. Teams have limited budgets and strict deadlines, so they must prioritize efficiency and make the most of the resources available.

## What's Next for C# and TypeScript Developers? Are We Doomed? Should We Start Learning Go?

NO! Relax. You're in a safe spot whether you're a TypeScript or C# developer. Both are awesome languages. Don't just drop everything and start learning Go as soon as possible. Instead, focus on C#/TypeScript, because those languages are evolving each year, and they're not going anywhere anytime soon. Microsoft wouldn't put all the effort and resources into TypeScript if it didn't have a long-term vision for it. And as for C#, it's still **Microsoft's primary language**, most of its systems are written in C#. I don't see Microsoft replacing it with Go anytime soon—or ever. 

I know, drama, controversy, and memes (especially memes) are way too popular. But if you want to be a professional, step away from the clickbait and focus on legitimate sources of information. Don't let misleading narratives influence your way of thinking, because if you're reading this article, most likely you're a professional software engineer (or at least a technical person), and the first skill you want to have is the ability to think independently and find proper sources of information to form your own, well-reasoned opinions based on them.