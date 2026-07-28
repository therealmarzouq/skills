---
name: simplified-technical-english
description: Write and rewrite technical documentation, plans, READMEs, and specs using ASD-STE100 Simplified Technical English (STE) principles — short sentences, one approved meaning per word, active voice, no filler. Use this whenever the user asks to write or rewrite docs, plans, technical specs, READMEs, or PR descriptions, or explicitly mentions STE, ASD-STE100, or "simplified technical English."
---

# Simplified Technical English (STE)

This skill applies the core writing discipline of **ASD-STE100**, the aerospace/defense
industry standard for unambiguous technical writing, to everyday docs: plans, specs,
READMEs, PR descriptions, runbooks. It is a style discipline, not the official ASD
specification — for the authoritative standard and full approved-word dictionary, see
https://www.asd-ste100.org/. The full dictionary is copyrighted by ASD and is not
reproduced here; this skill applies the general *principles* in plain language.

Goal: eliminate hedging, filler, and ambiguity that make AI-written docs feel bloated
("AI slop"). Every sentence should say one true thing, plainly.

## Step 1 — classify the text

- **Procedure** (tells someone what to do): max 20 words per sentence, imperative
  mood ("Run the migration," not "The migration should be run").
- **Description** (explains how something works or what happened): max 25 words per
  sentence, active voice preferred.

Never blend the two in one paragraph — decide which mode a section is in first.

## Step 2 — apply the core rules

**One word, one job.** Pick one term per concept and reuse it everywhere. Don't
alternate between "delete / remove / eliminate" for the same action — pick one and
stick with it for the whole document.

**Cut hedging and inflated verbs.** Replace vague or padded phrasing with the
plainest verb that says exactly what happens:
- "leverage," "utilize" → "use"
- "in order to" → "to"
- "is responsible for handling" → "handles"
- "may potentially cause" → "can cause" (or state the actual condition)

**No modal soup.** Avoid stacking "should," "might," "could," "may" when you actually
know the answer. If a step is required, say "do X." If it's conditional, say
"if Y, do X" — condition first, action second.

**Active voice, simple tense.** "The server rejects the request" beats "The request
will have been rejected by the server." Avoid present-perfect and progressive
constructions in instructions.

**One instruction per sentence.** Don't chain steps with "and then." Break combined
instructions into a numbered list.

**Cap sentence length.** 20 words for instructions, 25 for explanations. If a sentence
runs longer, split it — usually at the "and," "which," or "because."

**Keep multi-word technical terms short.** If a term needs more than three words
strung together, rephrase with a short prepositional phrase instead of stacking
nouns.

## Step 3 — transform, don't just trim

When rewriting a draft:
1. Classify each section as procedure or description.
2. Break any sentence over the word limit.
3. Convert passive/modal/hedged phrasing into direct active statements.
4. Merge synonyms for the same concept into one consistent term.
5. Move conditions to the front of the sentence.
6. Re-check that nothing essential (subject, actor, condition) got dropped in the
   simplification — STE removes padding, not information.

## Example

| Before (typical AI output) | After (STE-style) |
|---|---|
| "This function is responsible for potentially handling the validation of user input in cases where it may be malformed." | "This function validates user input. It rejects malformed input." |
| "You should probably consider running the tests before merging, in order to make sure nothing breaks." | "Run the tests before you merge." |

## Notes

- This is a style filter, not a grammar checker — it won't catch every real STE
  rule (the full standard has 53 rules and a ~900-word controlled dictionary).
  It's tuned to catch the specific failure mode of over-hedged, padded technical
  writing.
- Apply this to prose sections of docs/plans/READMEs. Don't force it onto code
  comments, commit messages, or conversational replies unless asked.
