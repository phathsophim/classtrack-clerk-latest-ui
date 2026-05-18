# ClassTrack — Attendance Clerk Portal walkthrough
**Audience:** EC Catholic stakeholders
**Demo school:** École Sainte-Croix · Clerk: Marguerite T.
**Total time:** ~15 minutes + Q&A

---

## Opening (1 min)

> "What you're going to see is the V3 wireframe for the **Attendance Clerk** portal — the screen the school's clerk lives in every day. We rebuilt it from the previous Principal portal to match the v2 functional requirements and meet WCAG 2.2 AA from day one.
>
> The design has two anchors. First, every screen is **action-first** — a clerk should be able to land on a page and immediately see what's waiting for them. Second, the **master-detail pattern** is consistent everywhere: a list on the left, a detail drawer that opens on the right so the clerk never loses their place. Let's walk through it."

---

## 1. Dashboard

> "This is what Marguerite sees when she logs in at 7:55 AM. The greeting is intentionally short — no fluff."

**Show:**
- The **Action needed** list on the left — nine items today, ordered by urgency.
- The four **KPI tiles** at the top: late at sign-in, replies pending, past 24h, signed-in-not-in-class.
- **Today's status** in the right rail with per-class **Send reminder** buttons for teachers who haven't submitted attendance yet.
- **Weekly attendance chart** and **by-grade** breakdown.

> "Everything here is a jump-off point. Click any row and you go straight to the screen that resolves it."

---

## 2. School roster

> "When the clerk needs to look at the whole school for one period, this is the screen. We redesigned it heavily this week."

**Show:**
- Date sits in the topbar next to the period — **Period 2 · 10:35–11:50 · Thu, May 7**.
- **Period dropdown** in the filter bar (blue to match the topbar chip) — current period is the default.
- Status filter chips: **Late · Absent · Awaiting parent** — no "Present" and no "No mark yet" because **this screen is for active records only**.
- Click **Liam Tremblay** — the drawer opens beside the table, not on top of it. Audit trail shows the clerk's sign-in action explicitly: *"Marguerite T. signed Liam in at 10:24 AM · status changed to Late."*

> "We removed the 'Locate' button and the 'My queue' toggle — we only have one clerk in this model, and locating a student isn't something the system can actually do."

---

## 3. Pending parent replies

> "Two tabs: *Awaiting your approval* and *Awaiting parent reply*. This is the conversation queue."

**Show:**
- Click **Olivia Bernard** — the drawer renders the conversation as message bubbles: the system notification we sent, and the parent's reply with the doctor's-note attachment.
- **Case Context** block surfaces the record type, period, and category before the clerk has to scroll.
- Primary action: **Approve justification**.

> "The reason this lives outside School roster is the presentation. A conversation is easier to scan as bubbles than as a row."

---

## 4. Disputes

> "When a parent contests a final mark, it lands here."

**Show:**
- Three open disputes — Sofia, Liam, Jaylen.
- Drawer has a **Case Context** block (including 'Final state' showing what Aspen recorded), a **Dispute Claim** bubble with evidence pills, and a collapsible **Audit trail** that's open by default.
- Resolution actions: **Change to..., Uphold original, Request more evidence**.

> "One open question for Mourad: when a dispute is filed, should we pause the Aspen-out push? We've documented this as Q7 — we need the policy from your side before build."

---

## 5. Future absences

> "Parent-declared, clerk-declared, and group-event-derived future absences all live here."

**Show:**
- Six demo records including Sophie's band-trip absence — it's linked to a Group Event so the clerk knows it's not an individual case.
- **Add future absence** modal — sources are **Parent or guardian** and **Authorized adult on file** (foster parents, social workers).
- A banner redirects multi-student cases to Group events.

> "We researched Canadian practice for foster-care scenarios — the 'Authorized adult on file' wording matches how school boards already handle this."

---

## 6. Group events

> "Field trips, sports trips, band tours — anything that pulls a group of students out of class."

**Show:**
- Four demo events.
- Click **Band weekend showcase** — drawer shows the affected periods per day, a student roster mini-table linking back to School roster, and an **Excluded from §2.1** pill (the school-sanctioned-event exemption from the new attendance law).
- **New group event** modal: clerk picks students one by one *or* selects an existing group (Senior football, Band program, Grade 9 — all).

---

## 7. Groups

> "This is the foundation for everything in scope creep — future messaging, ad-hoc audiences, the soccer-team parents, the bus 12 riders."

**Show:**
- Six demo groups across **three source modes**: Aspen-synced (read-only, nightly), CSV-imported (snapshot), Manual (fully editable).
- Each drawer shows a source-specific banner so the clerk immediately knows what they can and can't edit.
- **Used by** section lists referencing group events.

> "Q12 — and there are several sub-questions — covers how groups behave when Aspen rosters change overnight. We need Soufiane's input on conflict resolution before we build the sync logic."

---

## 8. Students *(Directory)*

> "The school directory starts here. Aspen-sourced, read-only."

**Show:**
- Filterable table — grade, class, search by name or student ID.
- Click **Liam Khoury** — drawer opens with five tabs.
- **Active records** tab is first by default — shows what's open *today* plus recent absences and late marks.
- **Attendance** tab — YTD stat strip, then a **Month dropdown** that lists the late and absence records for the selected month.
- **Student info, Parents, Groups** round out the profile.

> "Every Aspen-sourced field has the same blue read-only banner. The clerk learns the pattern once."

---

## 9. Classes *(Directory)*

> "One row per class — homeroom, enrolment, today's submission status, YTD rate."

**Show:**
- 9A is overdue submitting Period 2 — chip says **Awaiting · due 10:50 AM**.
- 9B is overdue with no reminder yet — chip is red.
- Drawer shows a **per-period strip** of today's submissions plus the class roster mini-table.
- Primary action: **Send submission reminder**.

> "This screen makes it obvious which teachers need a nudge before the period closes."

---

## 10. Teachers *(Directory)*

> "The staff side of the same data."

**Show:**
- Columns: Teacher, Role, Homeroom, Today's classes (P1–P4 chips), Today · P2 submission status, **On-time rate · 30 days**.
- Click **Marie Dubois** — drawer shows her Mon–Fri × P1–P4 schedule grid, today's submission strip, a 30-day on-time submission card (with average submission time vs. school average), and recent submission history.

> "Ninety-seven percent on-time over thirty days isn't just a vanity stat — it tells the clerk which teachers she can trust to self-manage and which ones need outreach."

---

## Closing (1 min)

> "Three things to take away:
>
> 1. **It's all one workflow.** Directory → Workflows → Justifications → Today — every screen links into the next.
> 2. **Aspen is the source of truth.** Demographics, rosters, schedules — read-only here, no double-entry.
> 3. **It's accessible.** WCAG 2.2 AA, two-stop focus halos, semantic tables, live regions for status changes — this passes audit on day one.
>
> What we need from you before September 1: **answers to Q7 (Aspen during disputes), Q11 (the reason-category enum), and Q12 (groups + Aspen sync rules)**. Once those are settled, the build is unblocked."

---

## Open questions to flag if asked

- **Q7** — Should the Aspen-out push pause while a dispute is active?
- **Q8** — Two distinct populations: staff who lead group events vs. authorized adults on file. We split them in the UI; need confirmation.
- **Q10** — Grade-impact exclusion for school-sanctioned events under the new law.
- **Q11** — Final list of reason categories (medical, transportation, religious, school-sanctioned event, family commitment, illness, weather, other).
- **Q12** — Groups + Aspen sync: data contract, identity, conflict resolution, snapshot vs. live-binding.

All open questions are tracked in **attendance-states-and-transitions.md**.
