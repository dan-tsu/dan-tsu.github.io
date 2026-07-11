---
title: "Wiki or RAG: two ways to put an offline LLM on industrial documentation"
description: "Two ways to put a local, offline LLM on industrial plant documentation — a compiled wiki versus retrieval — and how to choose for an OT environment."
pubDate: "Jul 11 2026"
heroImage: "../../assets/wiki-vs-rag-hero.jpg"
---

You have a room full of plant documentation. P&IDs, standard operating procedures, incident reports, and the IEC 62443 and NIST 800-82 texts themselves. Somewhere in there is the answer to the question in front of you, and you need it now — from those documents, not from a model's training data, and without any of it leaving the building.

There are two ways to put a local LLM on your plant documentation, and in an industrial environment they are not interchangeable. One retrieves. One compiles. That difference decides which you should run.

## Retrieval, on demand

The first approach is retrieval-augmented generation — RAG. I built a local one on a Mac mini: Bun, LanceDB, Ollama, the whole stack running offline under a dedicated, non-privileged user. The code is public ([dantsu-ai/rag1](https://github.com/dantsu-ai/rag1)). You drop your documents in, the system splits them into chunks and stores a mathematical fingerprint of each one — an embedding. When you ask a question, it finds the chunks closest to the question, hands them to a local model, and the model writes an answer with citations back to the source.

Nothing is decided ahead of time. Every query searches the raw documents fresh and generates a new answer. Add a document and it is live the moment it is indexed. The system is always current, and it never touches the cloud — I watched the network to confirm it: zero connections leaving the box during a query.

## Compilation, ahead of time

The second approach inverts that. Instead of searching raw documents at question time, an LLM reads the whole corpus and compiles it into a structured wiki — plain markdown pages, one per concept, cross-linked, each summary citing its sources. Andrej Karpathy described this pattern in April 2026 ([the LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)): the model incrementally builds and maintains the wiki, updating pages and flagging contradictions as new material arrives. His line for it is *"Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase."*

Adapt that to an air-gapped plant, and one property stands out: the knowledge is compiled once, into an artifact a person can read without any model running at all. You browse it like a wiki. The LLM's work is finished before anyone asks a question.

## What the offline constraint does to each

Both can run entirely local — that part is solved. Local models are now good enough that keeping everything on your own hardware is a real choice, not a downgrade.

But the constraint exposes where each one puts its risk.

RAG needs the model up every time someone asks a question. The answer is generated on the spot, which means it can vary between runs, and you cannot review "all the answers" in advance — there is no fixed output, only the corpus and the machinery that reads it.

The compiled wiki moves all of the model's work to the front. Once it is built, reading it needs no inference at all — it is just markdown. You can diff it, version it, and sign it off. But it goes stale the moment the underlying documents change, and any mistake the model made during compilation now sits in a page that looks authoritative.

## The trade-off that actually matters

The instinct is to frame this as smart versus simple, or new versus old. That is the wrong axis. In a plant, four questions decide fit:

- Who owns the artifact, and who maintains it?
- Can it be audited — reviewed, diffed, signed off?
- How current does it have to be, and how often do the sources change?
- Where is the trust boundary, and what has to be running for an answer to appear?

Answer those and the choice makes itself.

## Where each one wins

For reference knowledge that is reviewed and change-controlled — the standards, validated procedures, anything where an answer must be traceable and stable — the compiled wiki fits the way a plant already works. It produces an artifact you can put under document control, the same as any other controlled document. No model at read time means one less live system in a place that distrusts live systems.

For exploration — "has anything like this happened before," reading across years of incident reports, questions nobody wrote a procedure for — RAG earns its place. It stays current without a rebuild and it reaches as wide as the corpus.

| | Compiled wiki | RAG |
|---|---|---|
| Answer at read time | Pre-written markdown | Generated live |
| Needs a model running to read? | No | Yes |
| Auditable / sign-off | Yes — a fixed artifact | Hard — no fixed output |
| Stays current | Needs a rebuild | Automatically |
| Best for | Controlled reference | Exploration |

## How to decide for your environment

Start from the constraint that binds hardest. If it is auditability and change control — most regulated plants — compile the wiki and put it under document control. If it is breadth and currency across material nobody has curated, run RAG. Some environments want both: a controlled wiki for what has been validated, RAG over the long tail of everything else.

The mistake is choosing by which one feels more advanced. In an operational environment, the more advanced system is the one that fits the constraints you already have to live with — not the one with the most capability on paper.
