---
name: no-comments
description: "Delete unnecessary code comments, fix the code that made them necessary, and offer to encode real constraints as types, tests, or lint rules."
disable-model-invocation: true
---

# No comments

A comment that explains what the code does is a confession that the code does not say it.
Delete the comment and fix the code. Keep only comments about things you cannot change.

## Scope

Use the files the caller names. If the caller names none, use the current diff against the
base branch, default `main`, including uncommitted changes. Never touch code outside that scope.

## What survives

Only these five:

1. Legal or license headers.
2. Non-obvious behavior forced by an external dependency, platform, vendor, or protocol
   you cannot reshape.
3. `// prettier-ignore`, and lint suppressions whose rule is faulty, pedantic, or style-only.
4. Doc comments that define a public API contract.
5. Issue or RFC links that explain a constraint the code cannot express.

Everything else goes: narration, banners, section dividers, commented-out code, changelog
notes, and justifications for workarounds.

When you are unsure whether an exception applies, delete the comment.

## What is not an exception

A surprise in your own code is not an external constraint. Delete the comment and mark the
exact symbol as needing a rename, an extract, a type, or a restructure that makes the
behavior obvious without prose.

`IMPORTANT`, `do not remove`, `too risky`, and `fine for now` are not evidence. Read the
surrounding code first. If the claim is not obvious there, verify it against the real call
sites before you decide. A long justification with no exception behind it is a confession —
delete it. Never rewrite a comment into a shorter version of the same alibi.

`@ts-ignore`, `@ts-expect-error`, `eslint-disable`, and similar suppressions need the same
test. Look up the rule. If it catches real bugs or protects correctness or safety, delete
the suppression and fix the code under it.

## Steps

1. Read every comment in scope. Delete the ones that fail the list above. Record each
   deletion and each symbol that needs reshaping.
2. Fix the trivial cases directly: delete the dead path, drop the unused parameter, use the
   real API, rename the misleading symbol.
3. For the rest, implement the smallest root-cause fix that fits in scope. Remove the
   workaround the comment was defending. Never add a symptom guard in its place. If the root
   cause sits outside the scope, land the smallest in-scope fix and report the rest as open
   work — do not widen the fence.
4. Constraint comments say `do not remove`, `do not change wording`, or `talk to X before
   changing`. If the constraint is real and external, leave the comment. Otherwise offer the
   cheapest way to encode it as a type, a runtime check, a test, or a CI lint rule. Wait for
   approval. If approved, encode it and then delete the comment. If not, delete the comment
   and report the constraint as unenforced.
5. Report the deletion count, the fixes you made, the encodings you offered and landed, the
   constraints left unenforced, and any open work outside the scope.
