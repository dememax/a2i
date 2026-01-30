Epistemically Safe Instruction Architecture
============================================

:Author: Maxim Dementyev
:email: dememax@hotmail.com
:Copyright: 2026
:Naming: AI Instructions -> aii -> a2i

.. contents:: Contents
   :depth: 3
   :local:

This repository contains a structured set of AI instructions designed for
**analysis of complex, human-driven conversations and ideas**, where
*truth, meaning, and uncertainty* must all be preserved.

The goal is not conversational smoothness, persuasion, or agreement,
but **epistemic discipline**: avoiding hallucinations, false generalizations,
and misleading explanations while still providing useful interpretation.

This instruction set is intended for advanced analytical use cases:
dialogue analysis, linguistic discussion, social dynamics, reasoning audits,
and reflective or adversarial conversations.

Design Principles
-----------------

The architecture is intentionally layered. Each layer protects against
a different class of failure.

1. **Data Integrity (Pipeline Constraints)**  
   Prevents factual hallucinations, invented sources, and unjustified
   generalization. This layer answers the question: *“Is this claim allowed
   to exist at all?”*

2. **Epistemic Control (Right-to-Generate Constraints)**  
   Enforces explicit stopping conditions. If the origin, mechanism, or
   justification of a claim cannot be traced to user input or verifiable
   pre-trained knowledge, the model must stop and say so.
   Silence or refusal is preferred over plausible fabrication.

3. **Interpretation & Framing Constraints**  
   Governs *how* valid information is explained: preserving stress cases,
   attribution (who said what to whom), user-significant exceptions,
   and the difference between local behavior and stable traits.

These layers are orthogonal. They do not duplicate each other and should
not be collapsed into a single rule set.

What This Is Not
----------------

This project is **not**:

- a prompt optimization trick
- a tone or politeness filter
- a conversational alignment framework
- a replacement for fact-checking tools
- an attempt to model internal AI mechanisms

It deliberately avoids post-hoc rationalizations such as references to
“internal weights”, “conflict resolution modules”, or hidden system prompts.
If something cannot be grounded, it must not be explained.

Intended Use Cases
------------------

- Analysis of real chat logs or conversations
- Linguistic and pragmatic discussions
- Reasoning and argument audits
- Social or group dynamics analysis
- Expert-level exploratory dialogue
- Situations where “true but misleading” is considered a failure

This instruction set is especially useful when:

- over-generalization is dangerous,
- rare or stressful counterexamples matter,
- attribution and perspective are critical,
- or the cost of a confident hallucination is high.

Structure
---------

Instructions are split into independent blocks, each stored as a separate file.
Blocks are indexed to allow insertion of new constraints without renaming
existing files, preserving history and diffs.

See individual files for details.

File naming scheme
---------------------

Design goals for filenames:

- sortable
- stable over time
- insertable without renaming
- readable in diffs
- boring (this is a virtue)

Scheme: two-digit numeric prefixes, inspired by BASIC / old toolchains.

Versioning
----------

The repository maintains explicit versions of the instruction set.
Changes should be additive where possible, and breaking conceptual changes
should result in a new major version.

Rationale
---------

Most AI failures in analytical conversations are not caused by lack of
knowledge, but by *unauthorized explanation*.

This architecture treats explanation as a privilege, not a default.

Customization and Scope
-----------------------

This instruction set includes optional, user-specific blocks reflecting
individual analytical preferences and working style.

At present, one such optional block is tailored for **Maxim Dementyev** and
encodes preferences observed in long-form analytical dialogue
(e.g. emphasis on epistemic rigor, explicit attribution, stress cases,
and resistance to smoothing or premature abstraction).

These user-specific blocks are strictly optional. The core architecture
remains valid and useful without them.

AI-Agnostic Design
------------------

All instruction blocks are intentionally written to be **AI-agnostic**.

They do not rely on:

- model-specific internal mechanisms,
- references to hidden prompts or training details,
- assumptions about tool availability or memory models.

This allows the same instruction set to be applied, with minimal adaptation,
to different systems (e.g. ChatGPT, Gemini, or other LLMs), while preserving
the same epistemic guarantees.

Model-Specific Constraints and Normalization
--------------------------------------------

The instruction blocks are designed to respect known platform constraints,
most notably:

- Gemini instruction limits (approximately 1500 characters per block,
  no advanced formatting).
- ChatGPT personal instruction limits and session-level injection patterns.

As a result:

- Each block is self-contained and length-bounded.
- Blocks can be saved, injected, or reordered without semantic dependency
  on formatting or markup.

Usage with ChatGPT and Gemini
-----------------------------

The architecture supports different deployment strategies depending on
the platform.

**For ChatGPT:**

- A compact conjunction of the fundamental blocks (under 1500 characters)
  can be stored in "Personal Instructions" to provide a stable baseline.
- Additional blocks (e.g. framing, stress cases, domain-specific guidance)
  are intended to be injected explicitly at session start when needed.

**For Gemini:**

- Blocks are stored individually, respecting per-block length limits.
- During the save process, Gemini may internally normalize or rephrase
  blocks. Such normalized versions are considered implementation artifacts,
  not authoritative definitions.

The canonical source of truth remains the versions in this repository.

Canonical vs Normalized Blocks
------------------------------

Some platforms may transform, normalize, or rephrase instruction blocks
when saving them internally.

These normalized versions:

- are acceptable as execution artifacts,
- must preserve semantic intent,
- must not be treated as canonical specifications.

Canonical versions of all instruction blocks are maintained in this
repository and should be used as the reference for comparison,
revision, and future development.
