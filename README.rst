Epistemically Safe Instruction Architecture
============================================

:Author: Maxim Dementyev
:email: dememax@hotmail.com
:Copyright: 2026
:Naming: AI Instructions -> aii -> a2i

.. contents:: Contents
   :depth: 3
   :local:

Overview
--------

This repository contains a structured set of AI instructions designed for
**analysis of complex, human-driven conversations and ideas**, where
*truth, meaning, and uncertainty* must all be preserved.

The goal is not conversational smoothness, persuasion, or agreement,
but **epistemic discipline**: avoiding hallucinations, false generalizations,
and misleading explanations while still providing useful interpretation.

This includes maintaining strict boundaries between presentation
preferences, informational completeness, and cross-context behavioral
policy assumptions.

This instruction set is intended for advanced analytical use cases:
dialogue analysis, linguistic discussion, social dynamics, reasoning audits,
and reflective or adversarial conversations.

Design Principles
-----------------

The architecture is intentionally layered. Each layer protects against
a different class of failure and has a clearly defined responsibility.

These layers are orthogonal. They do not duplicate each other and must not
be collapsed into a single rule set.

Pipeline Constraints (Data Integrity & Reasoning Discipline) layer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Prevent factual hallucinations, invented sources, unjustified
generalization, and invalid inference steps.
This layer answers the question:
*“Is this claim allowed to exist as a fact or inference at all?”*

Epistemic Control (Right-to-Generate Constraints) layer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Enforces explicit stopping conditions. If the origin, mechanism,
justification, or internal rationale of a claim cannot be traced to
user input or verifiable pre-trained knowledge, generation must stop.
Silence or explicit declaration of “Unknown” is preferred over
plausible fabrication.

This layer also enforces a strict distinction between **consumption
preferences** and **epistemic access**.

Preferences about avoiding disturbing, explicit, or unwanted material
apply only to presentation style, recommendation strategy, or descriptive
vividness. They must not be promoted into restrictions on factual
completeness, classification-relevant attributes, or analytically
necessary context.

If ambiguity exists between exposure avoidance and informational
restriction, informational completeness takes priority by default.

Output Interface Contract layer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Governs *how* responses are expressed: language, tone, terminology,
and structural clarity. This layer ensures that even correct content
is not presented in a misleading or manipulative way.

Feedback & Prompt Analysis layer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Provides meta-level diagnostics on the quality of user inputs and
reasoning. Does not alter epistemic constraints but identifies
linguistic ambiguity, logical gaps, and prompt patterns that weaken
analytical precision.

Context & Transparency layer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Provides user-specific background, operational context, and attribution
signals that inform interpretation without overriding epistemic
constraints.

Localized preference statements are not treated as standing behavioral
policies unless explicitly confirmed. Preferences expressed within a
specific conversational scope must not be projected across sessions,
domains, or analytical tasks without scope confirmation.

Interpretation & Framing Constraints layer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Govern *how* valid information is interpreted and explained:
preserving stress cases, attribution (who said what to whom),
user-significant exceptions, and the distinction between local behavior
and stable traits.

Generalizations must explicitly indicate their mode (typical case,
illustrative example, or stress case), and diagnostically important
counterexamples must remain visible when they materially affect
interpretation.

Interaction Style Preferences (Optional) layer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Control interaction style (directness, disagreement, uncertainty
listing) without affecting epistemic correctness.

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

Numeric prefixes encode both **grouping** and **injection order**:
lower-numbered blocks must be applied before higher-numbered ones.

File Naming Scheme
------------------

Design goals for filenames
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- sortable
- stable over time
- insertable without renaming
- readable in diffs
- boring (this is a virtue)

Scheme
~~~~~~~~

Two-digit numeric prefixes inspired by BASIC / early toolchains.

Canonical ranges
~~~~~~~~~~~~~~~~~

00–09
    **Reserved / bootstrap** (empty)

10–19
    **Core Pipeline**

    Data integrity, verification anchoring, and reasoning discipline.
    Defines what claims may exist.

20–29
    **Epistemic Control**

    Generation permission and informational completeness guarantees.

30–39
    **Output Interface Contract**

    Language discipline, structure, and formulation honesty.

40–49
    **Feedback & Prompt Analysis**

    Linguistic clarity diagnostics and reasoning-quality feedback.

50–59
    **Context & Transparency**

    User profile data, preference persistence boundaries,
    jurisdictional context, collaboration environment,
    source attribution, and meta-feedback signals.

60–69
    **Framing (general interpretation)**

    Perspective alignment, generalization mode declaration,
    and stress/exception preservation.

70–79
    **Framing (domain-specific)**

    Domain baselines and paradigm-aware explanation strategy.

80–89
    **Interaction Style Preferences**

    Correction style, uncertainty disclosure, and exploration strategy.

Numbering ranges reflect primary architectural responsibility rather than
exclusive layer membership. Some ranges intentionally contain multiple
closely related control layers (e.g. context and transparency).

Versioning
----------

The repository maintains explicit versions of the instruction set.
Changes should be additive where possible.
Breaking conceptual changes require a new major version.

Customization and Scope
-----------------------

This instruction set includes optional, user-specific context blocks
reflecting individual analytical preferences or operational background.

At present, optional blocks are provided for **Maxim Dementyev**, including:

- personal analytical preferences,
- business and operational context for B2B, legal, and financial discussions.

These blocks are strictly optional. The core architecture remains valid
and useful without them.

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

Instruction Block Constraints
-----------------------------

All instruction blocks in this repository are intentionally constrained
to maximize portability, predictability, and compatibility across
different AI platforms.

The following constraints are **design requirements**, not incidental
limitations.

Block Size Limits
~~~~~~~~~~~~~~~~~

- Individual instruction blocks are generally kept **at or below
  approximately 1500 characters**.
- This reflects known platform limits:
  - Gemini instruction block size constraints.
  - ChatGPT personal instruction and session-injection limits.
- Architectural assumptions must not rely on longer blocks or implicit
  cross-block memory.

Formatting Discipline
~~~~~~~~~~~~~~~~~~~~~

- Instruction blocks avoid advanced or fragile formatting.
- Only minimal, robust constructs are used:
  - plain text
  - simple lists
  - section headers
  - capitalization for emphasis
  - quotation marks where necessary

This is intentional. Many platforms normalize, flatten, or partially
strip formatting during storage or execution. Instruction semantics
must survive such normalization without loss of meaning.

Language and Style Normalization
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Instruction blocks are written in **neutral, technical English**.
- The style is optimized for **machine interpretation**, not rhetorical
  effect or human persuasion.
- Language choices favor:
  - clarity over expressiveness,
  - explicit constraints over implied intent,
  - descriptive precision over idiomatic richness.

Where relevant, an STE-like (Simplified Technical English–style) approach
is used: short sentences, active voice, and limited syntactic complexity.
This is a stylistic discipline, not strict adherence to a controlled
vocabulary standard.

AI-Agnostic Intent
~~~~~~~~~~~~~~~~~~

These constraints ensure that instruction blocks:

- do not depend on hidden formatting channels,
- do not assume platform-specific parsing behavior,
- remain semantically stable under normalization or rephrasing,
- can be reused, reordered, or injected independently.

Together, these properties are essential for treating instructions as
**portable architectural components**, rather than fragile prompts.

Model-Specific Constraints and Normalization
--------------------------------------------

The instruction blocks are designed to respect known platform constraints,
most notably:

- Gemini instruction limits (approximately 1500 characters per block,
  no advanced formatting).
- ChatGPT personal instruction limits and session-level injection patterns.

Blocks may be internally normalized or rephrased by platforms during
storage. Such normalized versions are execution artifacts and must not
be treated as canonical specifications.

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
