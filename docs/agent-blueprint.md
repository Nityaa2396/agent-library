# Agent Team Blueprint: Plainly Concept Card Pipeline

**Status:** Draft v0.1
**Last updated:** 2026-04-22
**Source PRD:** [docs/prd.md](./prd.md)

---

## 1. Coordination task

Producing a single **Concept Card** end-to-end. It requires accurate research → plain-English explainer with analogy → per-role "why it matters" snippets and decision frameworks → application-style quiz questions. Each step depends on the prior step's output, and the analogy/role snippets must stay technically faithful to the researcher's source — that's a real handoff, not a single-agent prompt.

This addresses PRD §9 risk #1 (wrong analogies create worse misconceptions than no learning) by enforcing dual-track validation across specialist agents.

## 2. Specialists

### Concept Researcher
Gathers and validates the technical truth for a concept: definition, mechanism, common misconceptions, citations. Outputs the canonical source-of-truth document that all downstream agents must conform to.

### Plain-English Writer
Turns the researcher's source into the 90-second explainer + everyday analogy. Owns voice, the 12-word-style brevity rules, and the audio script.

### Role Contextualizer
Produces per-role "why it matters" snippets and 3-question decision frameworks for each enabled role (Marketing, Ops, Exec at MVP per PRD §7). Operates from a tight template.

## 3. Model selection

| Specialist | Model | Why |
|---|---|---|
| Concept Researcher | **Opus** | Source synthesis, accuracy under ambiguity, judgment about what to omit. Content errors compound downstream (PRD §9 risk #1). |
| Plain-English Writer | **Sonnet** | Strong prose at lower cost; analogy generation is craft, not depth. Iterates well against the Researcher's notes. |
| Role Contextualizer | **Haiku** | Short, structured outputs repeated across N roles per concept. Cheapest model that follows a tight template, since the Researcher already did the hard thinking. |

## 4. File ownership

| Agent | Owns (exclusive write) |
|---|---|
| Concept Researcher | `content/concepts/{slug}/source.md` (definition, mechanism, citations) |
| Plain-English Writer | `content/concepts/{slug}/explainer.md`, `content/concepts/{slug}/explainer.audio.txt` |
| Role Contextualizer | `content/concepts/{slug}/roles/*.md` (one file per role) |

**Shared, read-only for all three:** `content/concepts/{slug}/meta.yml` (slug, status, reviewer sign-offs)

## 5. TaskCompleted hook

A `validate_concept.py` script wired to TaskCompleted. It fails the task unless **all** of the following are true:

- All required files exist for the concept (`source.md`, `explainer.md`, every role file declared in `meta.yml`, `quiz.json`).
- `explainer.md` is ≤ 250 words and contains an `## Analogy` section.
- Every claim in `explainer.md` has a matching citation in `source.md` — verified by an LLM-as-judge call comparing the two documents.
- `quiz.json` questions are application-style — checked by a small classifier prompt that rejects recall phrasing (e.g., "What is X?").
- `meta.yml` shows both reviewer sign-offs from PRD §8 (SME + non-technical reviewer).
- No role file is empty or duplicates another role's text verbatim.

The hook runs structural checks first (fast, local), LLM-judge checks second. It blocks acceptance until all checks pass, directly mitigating the §9 content-quality risk before it reaches production.
