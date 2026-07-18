---
title: "From Policy to Proof: What 62443-2-1's Rewrite Means Under NIS2"
description: "The 2024 edition deleted the idea at the center of the standard and scored every requirement on a maturity model. That is the exact question NIS2 will put to the board."
pubDate: "Jul 18 2026"
heroImage: "../../assets/policy-to-proof-hero.jpg"
tags: ["OTsecurity", "ICScybersecurity", "NIS2", "IEC62443", "compliance"]
---

The 2024 edition of IEC 62443-2-1 did something standards almost never do. It deleted the idea at its own center.

The 2010 edition was built around the CSMS — the Cyber Security Management System, the framework an asset owner stood up to run industrial cybersecurity. Fourteen years of programs, audits, and consultancy decks were organized around that one concept. The latest edition, published in August 2024, does not revise it. It removes it. The word "CSMS" is gone. In its place is a Security Program; the nineteen management elements become eighty-seven requirements across eight program areas; and the whole thing is told to coordinate with the corporate ISO 27001 system rather than duplicate it.

That is a large structural change, and most of the commentary has stopped there — at the reorganization. But the reorganization is not where the weight sits. Folded into the new structure is a single addition that changes what the word "compliant" is allowed to mean. The 2024 edition scores every requirement on a four-level maturity model.

## The difference between having and doing

Under the old edition, a requirement was close to a yes or no. Do you have a policy for network segmentation? Do you have an incident response plan? A binder on a shelf could answer yes. The standard said little about how well the thing was actually done — it "left the measurement open," in its own words.

The maturity model closes that gap. Each requirement is now rated from ML1 to ML4, on a scale borrowed from the CMMI model the rest of the 62443 series already uses. ML1, Initial, means someone performs the task because they happen to know how — ad hoc, undocumented, resident in one person's head. ML2, Managed, means it is written down. ML3, Defined, means it is written down, tailored to the plant, and demonstrably practiced across the whole organization rather than in one good team. ML4, Improving, means you measure it and can show it getting better over time.

Read those levels again and notice what they rate. They do not rate whether a control exists. They rate how deeply it is lived. You cannot reach ML3 with a document, because ML3 asks for evidence that people actually do the thing, everywhere, under normal and adverse conditions. The bar moved from existence to evidence.

## Why this lands now

A maturity model is a useful engineering idea on its own. What makes this one matter is timing, and a piece of European law.

62443-2-1 is the part of the series that speaks to the asset owner — the operator running the plant. It is the natural technical answer to NIS2, the EU directive now reshaping cybersecurity obligations for essential and important entities, manufacturing among them. I have argued before that NIS2 pushes accountability up to the board: management bodies are personally liable for how their organization manages cyber risk. That is the layer where the signature now lands.

Put the two side by side. NIS2 does not ask whether you own a policy. It asks whether you manage risk — and, after an incident, whether you can demonstrate that you did. That is a maturity question in everything but name. A regulator standing in a plant after a breach will not be satisfied by a segmentation policy on file. They will ask whether it was practiced, whether it was tailored to this environment, whether anyone measured it. The 2024 edition arrives built to answer in exactly that language.

## The uncomfortable translation

Here is what changes for anyone who has said the words "we are 62443-compliant."

Under the old edition, that sentence was a shield. You had the elements; you were conformant. Under the new one, the honest version of the sentence is a coordinate: "we are at ML2 on most requirements, and ML1 on a few that matter." The maturity model turns a binary claim into a graded self-assessment — and a graded self-assessment cuts both ways. Overclaim it, and you have handed a regulator, or a court, a documented gap. Evidence it, and you hold the strongest demonstration available that you managed risk on purpose.

That is not a weakness in the standard. It is the design. The 2010 edition let an organization confuse having a program with running one. The 2024 edition makes that confusion visible, and it does so on the same axis — how mature, how practiced, how measured — that NIS2 will use to judge the organization.

So the move from the previous edition to the current one is not the paperwork exercise it looks like from the outside. The old elements do re-map onto the new program areas, and most of the content survives the journey. But the real work is not re-filing documents under new headings. It is the maturity climb — proving, requirement by requirement, that the program is lived and not merely owned.

Having a policy was the old bar. Being able to prove the policy is practiced, tailored, and measured is the new one. It is also, and not by accident, the bar the board is now signing against.
