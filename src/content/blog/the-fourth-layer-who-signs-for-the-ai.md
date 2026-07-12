---
title: "The Fourth Layer: Who Signs for the AI in Your Plant?"
description: "The three EmberOT articles map where AI belongs on the plant floor. NIS2 decides who signs for it."
pubDate: "Jul 12 2026"
tags: ["OTsecurity", "ICScybersecurity", "NIS2", "AIgovernance", "IEC62443"]
---

"AI-powered" has become the most expensive two words in an OT procurement document. They describe a feeling — that something modern and capable is now watching the process — while saying nothing about what the thing actually does, or who answers for it when it is wrong. Three articles from EmberOT have built the clearest framework I have seen for cutting through that fog. They stop, though, one layer short of where the real decision now sits. This is an attempt to add that layer.

## What the EmberOT articles envision

Read together, the three pieces describe a single, disciplined picture of where AI belongs in an industrial environment.

The first, Rishabh Das's "transparency curve," supplies the mechanism. Split the word "AI" into what it actually contains — statistics, machine learning, large language models — and one pattern appears: the more capable a technique becomes, the less it can explain itself. Statistics can show you exactly why it raised a flag. A machine-learning model can point at the measurements behind an alert, but its reasoning drifts every time it is retrained. A large language model just predicts the most probable next sentence — fluent, and unable to tell you why. On a plant floor that ordering is not academic. Anything protecting a physical process has to be explainable enough that a safety engineer can sign off, because standards like IEC 61508 demand a documented chain from input to output. Capability does not buy you out of that requirement. Transparency decides placement.

The second piece narrows what the most capable tool is actually for. An LLM in OT is a translation layer, not a detection layer. Detection — anomaly models, physics-based monitoring — has existed for a decade and was always "AI." What the language model adds is legibility: it turns a detector's output into something the engineer closest to the process can read. It has no privileged access to ground truth. In OT, physics is the ground truth, and the model cannot see it. So it explains; it does not decide. And because it usually wants to reach up into the cloud to do that, it becomes a new conduit across zones that IEC 62443 was written to keep separate — a modernization that can undo an air gap if nobody is watching.

The third piece, from EmberOT's Jori VanAntwerp, names what the newest arrivals actually are. Autonomous agents are not features; they are identities. Every helpful one is a credential nobody badged and an actor nobody is watching. In some environments they already outnumber humans many times over, each carrying standing access that nobody inventoried, scoped, or retired. The fix is not exotic. It is asset management applied to non-human identities: inventory them the way you inventory PLCs, give them least privilege, watch their behavior. This is IEC 62443 thinking, extended to software that acts on its own.

Put the three together and the vision is coherent and, in the best sense, conservative: AI belongs in OT as a transparent, translated, governed, advisory layer. Where a technique sits is decided by how much it can explain itself. Identity is governed like any other asset. The decisions themselves stay with deterministic systems and the humans who answer for them.

## The question all three share

Notice what every one of those articles turns on. The transparency curve asks whether a safety engineer can sign off. The translation argument asks that engineer to read and judge. The identity argument asks who is accountable for an actor on the network. All three converge on one question: can someone put their name to this? And that is where the framework stops — at the operator, the asset owner, the engineer on the floor. Which is exactly one layer too low.

## The fourth layer — up to the board

Because the person who now legally has to sign is not on the floor. Under NIS2, the directive reshaping cybersecurity accountability across the EU, management bodies are personally accountable for how their organization manages cyber risk. The obligation does not stop at the CISO. It reaches the board. And that changes what "AI-powered" means. On the floor it was a placement question. In the boardroom it is a liability question.

Translate that upward and it gets uncomfortable. When a vendor says "our solution is AI-powered," the board-level version of that sentence is: "we have introduced a system whose reasoning may not be explainable into an environment where the liability lands on us." Put that way, "we deployed an AI-powered solution" is not a reassurance. It is the exact point at which the questions should start.

This is where the transparency curve stops being an engineering diagram and becomes a governance instrument. A director does not need to know what an autoencoder is. They need one axis — how well can this explain itself? — to ask the only questions that matter. Where in the process does this system sit? If it protects something physical, can we produce the documented reasoning a regulator, or a court, will ask for? If it is advisory, are we certain it only advises — that it cannot quietly act? Who owns the agents we have let onto the network, and can we name them? The curve gives a non-technical board a way to interrogate a technical claim without being bluffed by it.

It also bridges two worlds that regulation keeps apart and that boards keep confusing. Functional safety (IEC 61508) and industrial security (IEC 62443) are different standards families with different auditors. The transparency curve sits across both, because "can you explain why it acted" is at once a safety question and a security one. A board that learns to ask it is governing both at the same time.

None of this is a case against AI in OT. The EmberOT articles are right: used as a transparent, translated, governed layer, these tools are a real force multiplier for the people closest to the process. The point is narrower and harder. The engineering community has worked out where AI belongs on the floor. The governance community has not yet worked out who signs for it. NIS2 has already decided that the signer is the board — whether or not the board realizes it yet.

"AI-powered" is a marketing claim. Accountability is a governance one. The three EmberOT articles map the first three layers of the gap between them — technique, translation, identity. The fourth layer, the one that decides who is liable when the fluent system is confidently wrong, is being drawn right now in boardrooms that mostly do not know they are holding the pen.
