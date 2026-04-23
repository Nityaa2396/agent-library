# PRD: Plainly — AI Literacy for Non-Technical Professionals

**Status:** Draft v0.1
**Author:** Product
**Last updated:** 2026-04-22

---

## 1. Problem

Non-technical professionals (marketers, HR, operations, finance, legal, executives) are being asked to make decisions about AI — vendor selection, policy, workflow integration, hiring — without understanding how the underlying technology works. Existing options force a bad tradeoff:

- **Free/cheap consumer apps** (Coursiv, Elements of AI) either stay at the surface ("how to write a prompt") or teach static academic theory that doesn't connect to daily work.
- **Enterprise platforms** (SmarterX) charge $999/user/year and require organizational buy-in.
- **Generic LLM chatbots** can explain concepts but don't structure learning, retention, or role-relevance.

The result: business users either fake fluency, defer to engineers, or make poorly informed decisions about tools they don't understand.

## 2. Goal

Build a product that gives non-technical professionals **genuine conceptual literacy** in AI — enough to ask the right questions, evaluate vendors, and make informed decisions — delivered in plain English, contextualized to their role, at a price individuals will pay.

### Success Metrics (first 6 months post-launch)
- 10,000 paid individual subscribers
- 60% 30-day retention; 35% 90-day retention
- 70%+ of users can correctly answer a "concept transfer" quiz 30 days after lesson completion (vs. recall-style quiz)
- NPS ≥ 40 among paid users
- 25 enterprise pilots signed by month 6

## 3. Target Users

**Primary:** Mid-career non-technical professionals at companies adopting AI — marketers, product managers, HR leaders, operations managers, finance analysts. Age 28–50. Already use ChatGPT/Claude casually but cannot explain what a token, embedding, or context window is.

**Secondary:** Executives needing decision-grade understanding without time for a course.

**Out of scope:** Engineers, data scientists, students seeking academic credit.

## 4. Core Product

### 4.1 The "Concept Card" model
Every technical concept (e.g., *embeddings*, *fine-tuning*, *RAG*, *hallucination*) is taught through a 5-minute **Concept Card** with three layers:
1. **Plain-English explainer** (90 seconds, text + audio) — uses analogy from everyday life.
2. **Why it matters for your role** — contextualized snippet for the user's selected job function.
3. **Decision framework** — a 3-question checklist the user can apply at work tomorrow.

### 4.2 Role-based learning paths
At onboarding, user picks a role (Marketing, HR, Ops, Finance, Legal, Exec). The same concept library is sequenced and contextualized differently per role.

### 4.3 Spaced repetition + transfer quizzes
Concepts resurface on a spaced schedule. Quizzes test **application** ("Your vendor says their model is 'fine-tuned on your data.' What's the first question you should ask?") not recall.

### 4.4 Weekly "In the Wild" brief
Each week, one real news item (vendor launch, regulation, incident) is decoded using concepts the user has already learned, reinforcing transfer.

### 4.5 Ask-a-Concept chat
Users can ask follow-up questions on any concept. Answers are constrained to the concept library and cite the relevant Concept Card.

## 5. Pricing

- **Free tier:** 10 foundational Concept Cards, no role personalization, no spaced repetition.
- **Individual:** $12/month or $99/year.
- **Team (5–50 seats):** $8/seat/month, includes admin dashboard and progress tracking.
- **Enterprise (50+):** Custom, includes SSO, custom learning paths, compliance reporting.

Positioning: deliberately undercuts SmarterX ($999/yr) while charging more than Coursiv ($29/mo) to signal depth over volume.

## 6. Differentiation

| | Coursiv | Elements of AI | SmarterX | **Plainly** |
|---|---|---|---|---|
| Conceptual depth | Low | High | Medium | **High** |
| Role-contextualized | No | No | Partial | **Yes** |
| Updated continuously | Partial | No | Yes | **Yes** |
| Individual price | $29/mo | Free | $999/yr | **$12/mo** |
| Application focus | Prompts | Theory | Mixed | **Decision frameworks** |

## 7. MVP Scope (first release)

**In:**
- 40 Concept Cards covering foundational LLM/AI concepts
- 3 role paths (Marketing, Ops, Exec)
- Spaced repetition engine
- Transfer-style quizzes
- Web app (responsive); no native mobile at MVP
- Stripe billing for Individual tier
- Email-based weekly brief

**Out (v1):**
- Native mobile apps
- Team/Enterprise tier
- Ask-a-Concept chat (post-MVP)
- Certifications
- SSO

## 8. Acceptance Criteria

- A user can sign up, pick a role, and complete their first Concept Card in under 4 minutes.
- 90% of Concept Cards include both text and audio.
- Spaced repetition surfaces a concept within 24h, 3d, 7d, and 21d of first completion.
- Quiz questions are reviewed by a subject-matter expert and a non-technical reviewer before publishing.
- Weekly brief sends every Monday 9am in the user's local timezone.

## 9. Risks (initial)

- **Content quality risk:** Wrong analogies create worse misconceptions than no learning. Mitigation: dual review (SME + non-technical).
- **Retention risk:** Bite-sized learning has notoriously poor 90-day retention. Mitigation: weekly brief + spaced repetition.
- **Positioning risk:** May be perceived as "yet another AI course." Mitigation: lead with decision-framework angle, not lessons.

## 10. Open Questions

- Do we build for individuals first and grow into teams, or seed with a few enterprise design partners?
- Should the weekly brief be free (lead-gen) or paid-only (retention)?
- How do we keep concept content current as the field changes monthly?
