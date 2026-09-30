Project: ARCHIE
Work Date: 2026-09-29
Session Title: VERONICA V2/V2.1 Hands-Off Acquisition Workflow Redesign
Source Type: Chronicle Handoff
Prepared By: ARCHIE
Public Disclosure Check: Cleared for public repository

# Summary

ARCHIE substantially redesigned VERONICA's Sean/Yosh headgear acquisition workflow after continued Batch 001 processing exposed excessive human adjudication, Work-token consumption, and repeated evidence handoffs between Chat, Work, and AJ.

The previous process emphasized proving duplicate, variant, and package-quality relationships before acquisition. The revised architecture instead treats Sean/Yosh as a Preferred Canonical Source and prioritizes reversible forward progress, staging, and post-download reconciliation.

# Development Trigger

The existing VERONICA workflow repeatedly escalated ambiguous candidates to REVIEW and asked AJ to provide manual screenshots or relay evidence between ARCHIE, VERONICA Chat, and VERONICA Work.

This contradicted the intended operating model: automated collection comparison and acquisition with minimal operator involvement.

Because candidate downloads are reversible and actual staged packages provide better evidence than repository metadata alone, exhaustive pre-acquisition certainty was determined to be unnecessary.

# Preferred Canonical Source Policy

Sean/Yosh is now a Preferred Canonical Source.

When a Sean/Yosh candidate represents the same collectible already held in Actus, VERONICA no longer needs to prove that Sean's package is technically superior before proposing it as the preferred replacement.

Existing local material remains protected when it may contain unique or useful content.

Supported disposition concepts now include:

- REPLACE
- REPLACE + PRESERVE
- ADD
- ACQUIRE
- STAGE
- SKIP
- REVIEW only when uncertainty has meaningful consequences

Automatic deletion remains prohibited.

# Phase 1 Validation

VERONICA applied the Preferred Canonical Source policy to the 48-candidate REVIEW population.

Initial Phase 1 results:

- REPLACE: 3
- REPLACE + PRESERVE: 11
- ADD: 4
- ACQUIRE: 2
- REVIEW: 28

Twenty candidates were resolved automatically in the first policy pass.

HC-6 Yellow Ranger was carried forward separately as REPLACE + PRESERVE.

No files were acquired or modified.

# Shared-Exception Processing

The remaining exception queue showed that multiple candidates shared common blockers rather than requiring independent adjudication.

Eight Gundam candidates were blocked because an existing Actus holding was named only `Gundam Helmet`.

AJ supplied the holding's existing render. The holding was identified as:

RX-78-2 Gundam Helmet

This resolved the shared blocker for:

- HC-14 — Gundam Deathscythe
- HC-30 — Gundam Mighty Strike Freedom
- HC-42 — Gundam Heavyarms EW
- HC-59 — Gundam Barbatos
- HC-75 — Gundam Bael
- HC-90 — Gundam Epyon
- HC-98 — Wing Gundam Zero EW
- HC-114 — RX-93 Nu Gundam

Under the completed Actus inspection, these candidates had no other plausible corresponding holdings and therefore resolved as NO-MATCH → ACQUIRE.

The full V2 Human Exception Queue fell from 28 to 20.

This established a new operating principle: process exceptions by shared evidence requirement and automation opportunity rather than sequential candidate order.

The earlier HC-8-first manual adjudication sequence was discontinued.

# V2.1 Hands-Off Acquisition Policy

Further review established that pre-download certainty itself was creating unnecessary work.

The governing V2.1 principle is:

Reversible forward progress over pre-acquisition certainty.

Pre-download uncertainty should normally produce ACQUIRE/STAGE rather than REVIEW.

Decision pattern:

- Clearly or probably missing → ACQUIRE
- Clearly or probably same as existing → ACQUIRE → REPLACE_CANDIDATE
- Same with potentially useful local material → ACQUIRE → REPLACE_PRESERVE
- Meaningful variant → ACQUIRE → ADD
- SAME-AS versus VARIANT uncertain → ACQUIRE → STAGE
- Poorly documented but in scope → ACQUIRE → STAGE
- Out of scope → SKIP

Confidence remains recordable as HIGH, MEDIUM, or LOW but no longer automatically blocks acquisition.

# Revised VERONICA Lifecycle

Inventory Source
→ Normalize Candidate Identity
→ Compare Against Actus/Catalog Metadata
→ Best-Guess Classification
→ Build Acquisition Manifest
→ Acquire to Staging
→ Inspect Actual Package
→ Reconcile Against Actus
→ Promote / Add / Replace / Preserve
→ Escalate Consequential Exceptions Only

Detailed package reconciliation therefore moves after acquisition to staging, where VERONICA can inspect actual files instead of attempting to infer every relationship from repository metadata and previews.

# Preservation Boundary

No automatic deletion is authorized.

When Sean replaces an existing canonical package, the displaced local package must initially be preserved or staged rather than destroyed.

Unique or potentially useful existing material may be retained through REPLACE + PRESERVE.

Cleanup and retention automation is deferred until the workflow demonstrates sufficient reliability.

# Human Intervention Threshold

AJ should no longer serve as the routine evidence-transfer layer.

VERONICA should make reasonable best-guess decisions using machine-accessible evidence.

Human intervention is reserved primarily for cases where unique material could be lost, a subjective collection decision is unavoidable, conflicting identities cannot safely coexist, collection scope itself is uncertain, or another consequential decision cannot safely be deferred until staging.

An unresolved staged package is acceptable system state.

# Work Model Escalation

A model-selection strategy was established to reduce unnecessary Work consumption.

Routine operations should use the least expensive reasoning level appropriate to the task.

Current operating pattern:

- GPT-6 Luna / Low — filesystem inventory, extraction, hashes, deterministic matching, rule application, manifests, routine acquisition/staging.
- GPT-6 Sol / Medium — ambiguous identity or package relationships requiring substantive reasoning.
- GPT-6 Sol / High — difficult visual/geometry adjudication and genuinely complex exceptions.
- GPT-6 Astra / Medium — broader exploratory Work where the problem is not sufficiently constrained.

The strongest reasoning configuration should not process an entire collection merely because a minority of records are difficult.

ARCHIE will provide an explicit model and reasoning recommendation whenever transitioning work into Work.

# ARCHIE / VERONICA Operating Relationship

ARCHIE assumes the coordination layer for this workflow.

AJ should not routinely relay individual adjudication messages among ARCHIE, VERONICA Chat, and VERONICA Work.

Preferred pattern:

AJ → ARCHIE → bounded VERONICA Work operation → ARCHIE review

VERONICA Work is used when local filesystem access or substantial batch execution is actually required.

ARCHIE performs policy, workflow design, result interpretation, exception clustering, and determination of the next bounded operation.

# Current State

At session close:

- Sean/Yosh remains Preferred Canonical Source.
- V2.1 Hands-Off Acquisition Policy is established.
- Shared Gundam blocker resolved.
- Existing unnamed Gundam holding normalized to RX-78-2 Gundam Helmet.
- Manual HC-8 sequence discontinued.
- Pre-download exhaustive duplicate interrogation discontinued.
- No Sean/Yosh packages were acquired during this development session.
- /Volumes/Actus remains unchanged.
- Automatic deletion remains unauthorized.

# Exact Resume Point

Next operation:

VERONICA V2.1 — Batch 001 Acquisition Manifest

Recommended Work configuration:

Model: GPT-6 Luna
Reasoning: Low

The next run is manifest-only.

It should apply V2.1 policy across the complete Batch 001 candidate population and produce:

- complete acquisition manifest
- acquisition-action counts
- download queue
- expected post-download disposition
- preservation requirements
- retained source-location information
- continuation record

It must not download packages or modify Actus.

ARCHIE reviews the resulting manifest before authorizing the first acquisition/staging operation.
