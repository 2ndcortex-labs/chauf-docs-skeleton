# Organization Chauffeur Playbook

This playbook defines **how this organization expects Chauffeurs to direct work, communicate, report progress to Dispatch, and handle work orders**. It is owned and edited by the organization. Any worker-specific `workers/<slug>/PLAYBOOK_local.md` may extend or override rules below for that project.

---

## 1. Progress Updates to Dispatch (Frequency & Content)

- **Mandatory cadences:**
  1. **On work order claim:** Report that the order was claimed, restate the deliverable in one line, and outline the high-level plan (`phase: planning`).
  2. **At every stage transition:** Post an update when moving between `planning` -> `building` -> `verifying` -> `blocked` -> `done`.
  3. **Time-based heartbeat during long tasks:** If more than **15 minutes** pass without a stage change during active execution, post a concise progress update with current % estimate.
  4. **Mandatory end-of-shift update:** **Always** post a final progress update before ending, pausing, handing off, or compacting a session — even if only partial investigation occurred.
- **Required content in every substantive update:**
  - **What moved forward** (concrete artifacts, commits, verified checks — not vague filler).
  - **Percent estimate** (`0`–`100`) when working an order.
  - **Blockers, risks, or pending Operator questions** (if any).
  - **Immediate next step** so the Operator and the next Chauffeur see continuity at a glance.

---

## 2. Work Order Handling

- **Startup check:** At the beginning of every shift, inspect the worker's active and queued work orders in Dispatch before inventing new work.
  - If an order is already `in_progress`, resume it using `HANDOFF.md` rather than claiming a second order.
  - If no order is active and queued orders exist:
    - **P0 / P1 (Critical / High):** Auto-claim and start immediately unless `BRIEF.md` or `PLAYBOOK_local.md` requires pre-approval.
    - **P2 / P3 (Normal / Background):** Auto-claim if the order payload is unambiguous and within `BRIEF.md` scope; otherwise ask the Operator first.
- **Priority & multi-order discipline:** Work one active order to a clean milestone or completion before claiming the next. If a `P0` arrives while working a `P2`/`P3`, bring the current turn to a safe checkpoint, note the pause in `HANDOFF.md`, and escalate or switch cleanly.
- **Acceptance bar before marking `completed`:**
  - Verify the deliverable against `northstar.md`, `manifesto.md`, `BRIEF.md`, and the order payload.
  - Confirm builds/tests/checks pass and changes are committed/pushed where expected.
  - Include concise result metadata (e.g., PR/commit links, preview URLs, summary of verification) when closing the order.
- **Blocked or failed orders:**
  - If blocked on missing info, credentials, or an external dependency, mark the order `blocked` (or pause for Operator feedback) with the exact question needed to unblock.
  - Only mark an order `failed` after genuine recovery attempts have been exhausted, and record the root cause clearly.

---

## 3. Escalation & Operator Feedback

Pause and ask the Operator (instead of guessing) whenever:
- A decision conflicts with `northstar.md`, `manifesto.md`, or `BRIEF.md`.
- An action is irreversible, public-facing, destructive, or affects billing/production domains.
- Requirements in a work order are ambiguous in a way that changes user-facing architecture or deliverables.
- The worker hits repeated errors (2+ failed attempts on the same root cause) or a persistent permission/auth failure.

When escalating, present:
1. The exact decision needed (1–2 sentences)
2. Your recommended option and why
3. Any concrete tradeoff or risk

---

## 4. Directing Work (Operator Voice & Quality Bar)

- **Clarity over verbosity:** Give direct, well-scoped instructions with clear acceptance criteria. Avoid dumping walls of raw notes into a single turn.
- **One coherent step at a time:** Break large deliverables into verifiable milestones (spec/plan -> implement -> test/verify -> ship).
- **Respect `manifesto.md` and `northstar.md`:** Push back when output is sloppy, over-engineered, or drifts from the stated taste and goals.
- **Verify claims:** Ask for concrete verification output (test results, build output, diffs, live checks) before accepting a task as done.

---

## 5. Shift Handoff Expectations

Because another Chauffeur on a different tool or host may take the next drive:
- Keep `HANDOFF.md` crisp and current (under ~1 page): active order, current state, open questions, and the exact next 1–3 steps.
- Record every settled Operator ruling or project gotcha in `DECISIONS.md` with the date so future Chauffeurs never re-ask settled questions.
- Keep ad-hoc drafts, research, and checklists neatly inside `notes/`.
