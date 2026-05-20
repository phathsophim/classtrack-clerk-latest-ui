# ClassTrack Design System
**Version:** 1.1 — Based on Clerk's Portal V3.1 Prototype  
**Screens Analyzed:** 12 (Dashboard, Today's Records, Classes, Daily Attendance, Disputes, Future Absences, Group Events, Groups, Pending Parent Replies, Students, Teachers, Index)  
**Compliance Target:** WCAG 2.2 AA  
**Icon Library:** Font Awesome 6.5.0 Solid  
**Status:** Documentation only — do not modify existing screens

---

## Table of Contents

1. [Design Tokens — Colors](#1-design-tokens--colors)
2. [Design Tokens — Typography](#2-design-tokens--typography)
3. [Design Tokens — Spacing, Radius & Shadows](#3-design-tokens--spacing-radius--shadows)
4. [Chips & Badges](#4-chips--badges)
5. [Identity & Avatar System](#5-identity--avatar-system)
6. [Status Colors — Semantic System](#6-status-colors--semantic-system)
7. [Icon System](#7-icon-system)
8. [Parent Reason Chips](#8-parent-reason-chips)
9. [Group Events & School Events](#9-group-events--school-events)
10. [Buttons](#10-buttons)
11. [Navigation — Sidebar](#11-navigation--sidebar)
12. [Topbar](#12-topbar)
13. [Tables](#13-tables)
14. [Detail Drawers](#14-detail-drawers)
15. [Cards & KPI Tiles](#15-cards--kpi-tiles)
16. [Filter Bar](#16-filter-bar)
17. [Forms](#17-forms)
18. [Empty States, Skeletons & Feedback](#18-empty-states-skeletons--feedback)
19. [Inconsistencies Found & Recommendations](#19-inconsistencies-found--recommendations)

---

## 1. Design Tokens — Colors

All colors are defined as CSS custom properties on `:root` and must be referenced by variable name throughout the product. Hardcoded hex values in component code should be replaced in future implementation.

### Background & Surface

| Token | Value | Usage |
|---|---|---|
| `--c-bg` | `#F4F6FA` | Page/app background |
| `--c-surface` | `#FFFFFF` | Cards, drawers, tables, inputs |
| `--c-surface-2` | `#F8FAFC` | Table headers, drawer headers, secondary fill |
| `--c-surface-alt` | `#EEF2F7` | Hover states |

### Borders

| Token | Value | Usage |
|---|---|---|
| `--c-border` | `#D6DBE2` | Primary card/table borders |
| `--c-border-2` | `#E5E8EE` | Subtle dividers, row separators |
| `--c-border-strong` | `#A6ADBB` | Input borders, button borders |

### Ink (Text)

| Token | Value | Usage |
|---|---|---|
| `--c-ink` | `#0F2546` | Primary text, headings |
| `--c-ink-muted` | `#475467` | Secondary text, labels, table headers |
| `--c-ink-subtle` | `#5C6470` | Tertiary/placeholder text, timestamps |

### Brand

| Token | Value | Usage |
|---|---|---|
| `--c-brand` | `#1B5DAF` | Primary action color, links, active states |
| `--c-brand-ink` | `#0E2E55` | Dark brand (hover states, active filter chips) |
| `--c-brand-tint` | `#E8F0FA` | Brand backgrounds (chips, selected rows, grade chips) |

### Semantic — Status & Workflow Colors

| Token | Value | Tint Token | Tint Value | Semantic meaning |
|---|---|---|---|---|
| `--c-success` | `#1F7A3F` | `--c-success-tint` | `#E6F4EC` | Present (status) · Justified (workflow complete) · Submitted on time |
| `--c-warning` | `#9A4708` | `--c-warning-tint` | `#FCF1DD` | Late (status) · Awaiting action |
| `--c-warning-bord` | `#B97F38` | — | — | Warning chip border |
| `--c-danger` | `#B42318` | `--c-danger-tint` | `#FCE9E7` | Absent (status) · Unjustified · Disputed · Missing |
| `--c-info` | `#0E5C8A` | `--c-info-tint` | `#E0EFF7` | Workflow stages: pending approval, parent reply, awaiting |
| `--c-neutral-tint` | `#EEF1F5` | — | — | Neutral chips, count pills, period labels |

### Special

| Token | Value | Usage |
|---|---|---|
| `--c-event-purple` | `#EEEAFE` | Group/school events background |
| `--c-event-purple-ink` | `#3F22A6` | Group/school events text and icons |
| `--c-event-purple-bord` | `#7E68DC` | Group/school events chip border |
| `--c-focus` | `#FFB400` | Focus ring (keyboard navigation) |

### Sidebar

| Token | Value | Usage |
|---|---|---|
| `--c-sidebar` | `#0F2546` | Sidebar top gradient |
| `--c-sidebar-2` | `#0A1B36` | Sidebar bottom gradient |
| `--c-sidebar-hover` | `rgba(255,255,255,0.08)` | Nav item hover |
| `--c-sidebar-active` | `#1B5DAF` | Active nav item, logo mark |

---

## 2. Design Tokens — Typography

### Font Family

```css
--ff: "Segoe UI", system-ui, -apple-system, BlinkMacSystemFont, Roboto, "Helvetica Neue", Arial, sans-serif;
```

No web fonts. System font stack only.

### Font Size Scale

| Token | Value | Usage |
|---|---|---|
| `--fs-xs` | `12px` | Chips, labels, timestamps, metadata |
| `--fs-sm` | `13px` | Table body, nav items, drawer body |
| `--fs-md` | `14px` | Body default, buttons, card body |
| `--fs-lg` | `16px` | Drawer titles, section headings |
| `--fs-xl` | `20px` | Drawer entity name, KPI values |
| `--fs-2xl` | `24px` | Page `<h1>` titles |
| `--fs-3xl` | `30px` | Reserved |

### Font Weight

| Weight | Usage |
|---|---|
| `400` | General body text |
| `500` | Nav items default, drawer detail values |
| `600` | Buttons, card names, crumbs |
| `700` | Headings, chips, table row names, KPI values, avatar initials |
| `800` | Logo mark ("CT"), class icon initials |

### Line Height

- Body: `1.55` — KPI numbers: `1` — Drawer entity name: `1.2`

### Letter Spacing

| Usage | Value |
|---|---|
| Sidebar section labels, drawer `<h3>` | `0.12em` |
| Table `<th>`, chip labels, meta labels | `0.06em` |
| Page `<h1>`, logo | `-0.01em` |

### Numeric Values

All numbers (KPIs, percentages, IDs, counts) use `font-variant-numeric: tabular-nums`.

### Typography Hierarchy

| Element | Size | Weight | Color |
|---|---|---|---|
| Page `<h1>` | 24px | 700 | `--c-ink` |
| Card title | 14px | 700 | `--c-ink` |
| Drawer entity name | 20px | 700 | `--c-ink` |
| Drawer section `<h3>` | 11px | 700 uppercase | `--c-ink-muted` |
| Table `<th>` | 11px | 700 uppercase | `--c-ink-muted` |
| Table row name | 13px | 700 | `--c-ink` |
| Table row metadata | 11px | 400 | `--c-ink-subtle` |
| Sidebar section label | 10px | 700 uppercase | `rgba(255,255,255,0.55)` |
| Nav item | 13px | 500 | `rgba(255,255,255,0.78)` |
| Status chip | 11px | 700 | Semantic ink |
| Button default | 13px | 600 | — |
| Button small | 12px | 600 | — |
| KPI value | 20px | 700 | `--c-ink` |

---

## 3. Design Tokens — Spacing, Radius & Shadows

### Spacing Scale

| Token | Value | Usage |
|---|---|---|
| `--s-1` | `4px` | Inline gaps |
| `--s-2` | `8px` | Compact gaps, chip lists |
| `--s-3` | `12px` | Standard padding, nav items |
| `--s-4` | `16px` | Content padding, drawer body |
| `--s-5` | `24px` | Page content, section gaps |
| `--s-6` | `32px` | Large section spacing |

### Component Padding Reference

| Component | Padding |
|---|---|
| Sidebar logo area | `24px 16px 16px` |
| Sidebar nav item | `10px 12px` |
| Topbar | `12px 24px` |
| Page content area | `24px` |
| Card header | `12px 16px` |
| Card body | `16px` |
| Card footer | `8px 16px` |
| Table `<th>` | `10px 12px` |
| Table `<td>` | `12px` |
| Status chip | `2px 8px` |
| Role/grade/reason chip | `2px 10px` |
| Filter chip button | `6px 12px` |
| Button default | `8px 14px` |
| Button small | `4px 10px` |
| Drawer header | `12px 16px` |
| Drawer body panels | `16px` |
| Drawer action footer | `12px 16px` |
| KPI tile | `12px 16px` |
| Info list `<dl>` | `12px 16px` |
| Modal header / footer | `16px 24px` |

### Border Radius Scale

| Token | Value | Usage |
|---|---|---|
| `--r-sm` | `4px` | Code chips, schedule cells, small details |
| `--r-md` | `6px` | Buttons, inputs, icon buttons, **entity/category tags**, group icons, class icons, period cards, form fields |
| `--r-lg` | `10px` | Cards, table cards, drawers, banners, filter bars |
| `--r-xl` | `14px` | Modals, large cards |
| `--r-pill` | `999px` | **All status chips**, grade chips, role chips, reason chips, filter buttons, nav badges, people avatars, count pills |

### Shadows

| Token | Value | Usage |
|---|---|---|
| `--shadow-md` | `0 4px 12px rgba(15,37,70,0.08)` | Drawers, cards on hover |
| `--shadow-lg` | `0 8px 28px rgba(15,37,70,0.12)` | Toasts, index cards |

---

## 4. Chips & Badges

### Two-tier Chip System

The product uses two distinct chip shapes with a clear semantic purpose:

| Shape | Radius | Purpose |
|---|---|---|
| **Pill** (`--r-pill`) | `999px` | Status chips, workflow chips, informational chips — anything that describes a *state* or *stage* |
| **Rounded square** (`--r-md`) | `6px` | Entity / category labels — anything that describes *what something is* (class group, period slot, source system) |

This distinction is intentional and must be applied **consistently across all screens**. If a label uses a rounded square on one screen, it must use a rounded square everywhere.

### Base Chip Spec — Pill

```css
display: inline-flex; align-items: center; gap: 4px;
padding: 2px 8px;
border-radius: var(--r-pill);
font-size: 11px; font-weight: 700; letter-spacing: 0.02em;
border: 1px solid transparent;
/* Icon inside chip */ font-size: 9px;
```

### Base Chip Spec — Rounded Square (Entity/Category)

```css
display: inline-flex; align-items: center; gap: 4px;
padding: 2px 8px;
border-radius: var(--r-md);    /* 6px */
font-size: 11px; font-weight: 700;
border: 1px solid transparent;
```

---

### Type 1 — Student Status Chips (Attendance State)

These represent the **student's attendance state**. Color is always tied to the status — it must not change based on workflow.

| Variant | Background | Text | Border | Icon |
|---|---|---|---|---|
| Present | `--c-success-tint` | `--c-success` | `#4F9A6C` | `fa-circle-check` |
| Late | `--c-warning-tint` | `--c-warning` | `--c-warning-bord` | `fa-circle-exclamation` |
| Absent | `--c-danger-tint` | `--c-danger` | `#B0625A` | `fa-circle-xmark` |

> **Rule:** Absent stays red and Present stays green always. These are immutable status colors — workflow outcomes do not change them.

---

### Type 2 — Workflow Stage Chips

These represent **where a record is in the workflow**, independent of the student's status.

| Variant | Background | Text | Border | Icon |
|---|---|---|---|---|
| Awaiting check-in | `--c-info-tint` | `--c-info` | `#5B96BC` | `fa-hourglass-half` |
| Awaiting parent reply | `--c-info-tint` | `--c-info` | `#5B96BC` | `fa-hourglass-half` |
| Pending clerk approval | `--c-info-tint` | `--c-info` | `#5B96BC` | `fa-hourglass-half` |
| **Justified** | `--c-success-tint` | `--c-success` | `#4F9A6C` | `fa-circle-check` |
| Unjustified / Past due | `--c-danger-tint` | `--c-danger` | `#B0625A` | `fa-clock` |
| Disputed | `--c-danger-tint` | `--c-danger` | `#B0625A` | `fa-flag` |
| Parent replied | `--c-info-tint` | `--c-info` | `#5B96BC` | `fa-envelope-open-text` |
| Did not reach class | `--c-warning-tint` | `--c-warning` | `--c-warning-bord` | `fa-person-circle-exclamation` |

> **Justified is green** because the workflow is complete — the clerk has resolved the record. This is correct and intentional. Green = done.

> **All "Awaiting / Pending" workflow stages** use `fa-hourglass-half` (sand clock). This distinguishes workflow chips from student status chips, which use circle icons.

---

### Type 3 — Context / Informational Chips

| Variant | Background | Text | Border | Icon |
|---|---|---|---|---|
| Group event | `--c-event-purple` | `--c-event-purple-ink` | `--c-event-purple-bord` | `fa-bus` |
| Future absence | `--c-brand-tint` | `--c-brand-ink` | `#6E94BF` | `fa-calendar-days` |
| Period (neutral) | `--c-neutral-tint` | `--c-ink` | `--c-border-strong` | `fa-clock` |

---

### Type 4 — Informational / Role Chips (Pill)

| Variant | Background | Text | Border |
|---|---|---|---|
| Grade | `--c-brand-tint` | `--c-brand-ink` | `#6E94BF` |
| Homeroom | `--c-info-tint` | `--c-info` | `#5B96BC` |
| Role: Homeroom teacher | `--c-brand-tint` | `--c-brand-ink` | `#6E94BF` |
| Role: Coach | `--c-warning-tint` | `--c-warning` | `--c-warning-bord` |
| Role: Supply | `--c-neutral-tint` | `--c-ink-muted` | `--c-border-strong` |
| Count pill (neutral) | `--c-neutral-tint` | `--c-ink-muted` | none |

---

### Type 5 — Entity / Category Tags (Rounded Square — `--r-md`)

Used when labeling **what an entity or slot is**, not its state. Applied consistently across all screens.

**Period / Class Tags** (used in teacher rows, schedule views):
```css
padding: 2px 8px; border-radius: var(--r-md);
background: var(--c-neutral-tint); color: var(--c-ink);
border: 1px solid var(--c-border-strong);
font-size: 11px; font-weight: 700;
```

**Source Badges** (used in Groups table):

| Variant | Background | Text | Border |
|---|---|---|---|
| Aspen | `--c-info-tint` | `--c-info` | `#5B96BC` |
| CSV | `--c-warning-tint` | `--c-warning` | `--c-warning-bord` |
| Manual | `--c-success-tint` | `--c-success` | `#4F9A6C` |

**Group Type Tags**:

| Variant | Background | Text | Border |
|---|---|---|---|
| Sport | `#FEE4E2` | `#B42318` | `#B0625A` |
| Arts | `--c-event-purple` | `--c-event-purple-ink` | `--c-event-purple-bord` |
| Academic | `--c-info-tint` | `--c-info` | `#5B96BC` |
| Cohort | `#E0F2FE` | `#0369A1` | `#93C5FD` |
| Club | `--c-success-tint` | `--c-success` | `#4F9A6C` |
| Custom | `--c-neutral-tint` | `--c-ink-muted` | `--c-border-strong` |

---

### Type 6 — Filter / Toggle Chips (Interactive)

```css
/* Default */
background: var(--c-surface); border: 1px solid var(--c-border);
color: var(--c-ink-muted); padding: 6px 12px; border-radius: var(--r-pill);
font-size: 12px; font-weight: 600; min-height: 28px;
/* Active/pressed */
background: var(--c-brand-ink); color: #fff; border-color: var(--c-brand-ink);
/* Count inside — inactive */ rgba(0,0,0,0.08)
/* Count inside — active */  rgba(255,255,255,0.2)
```

---

## 5. Identity & Avatar System

### Shape Rule by Entity Type

| Entity type | Shape | Radius | Content |
|---|---|---|---|
| **Person** (student, teacher, parent, clerk) | Circle | `--r-pill` | 2-letter initials, white, weight 700 |
| **Class** (homeroom/class group) | Rounded square | `--r-md` | Grade code (e.g., "9A"), weight 800 |
| **Group / Club / Team** | Rounded square | `--r-md` | FA icon representing category |
| **Event** | Rounded square | `--r-md` | FA icon representing event type |

### Size by Context

| Context | Size |
|---|---|
| Roster mini (compact) | 28px |
| Table standard (students) | 36px |
| Table standard (teachers, classes) | 40px |
| Drawer hero (all entity types) | 56px |
| Sidebar user | 36px |
| Topbar chip | 28px |

### Color — People (proposed token set)

| Token | Value |
|---|---|
| `--c-avatar-1` | `#1B5DAF` |
| `--c-avatar-2` | `#6366F1` |
| `--c-avatar-3` | `#10B981` |
| `--c-avatar-4` | `#F59E0B` |
| `--c-avatar-5` | `#EC4899` |
| `--c-avatar-6` | `#0891B2` |
| `--c-avatar-7` | `#8B5CF6` |
| `--c-avatar-8` | `#EF4444` |

Text: `#ffffff`, weight 700. Assign by entity ID hash — same person = same color everywhere.

### Color — Classes (by grade)

| Grade | Background | Text |
|---|---|---|
| Grade 7 | `#E8F0FA` | `#0E2E55` |
| Grade 8 | `#E0F2FE` | `#0369A1` |
| Grade 9 | `--c-event-purple` | `--c-event-purple-ink` |
| Grade 10 | `--c-success-tint` | `--c-success` |
| Grade 11 | `--c-warning-tint` | `--c-warning` |
| Grade 12 | `--c-danger-tint` | `--c-danger` |

### Color — Groups / Events (by category)

| Category | Background | Text |
|---|---|---|
| Sport | `#FEE4E2` | `#B42318` |
| Arts / Music | `--c-event-purple` | `--c-event-purple-ink` |
| Academic | `--c-info-tint` | `--c-info` |
| Cohort | `#E0F2FE` | `#0369A1` |
| Club | `--c-success-tint` | `--c-success` |
| Custom | `--c-neutral-tint` | `--c-ink-muted` |

---

## 6. Status Colors — Semantic System

### Two-layer Model

The ClassTrack status system has **two independent layers**:

**Layer 1 — Student Status** (what happened to the student)

| Status | Color | Token |
|---|---|---|
| Present | Green | `--c-success` |
| Late | Amber | `--c-warning` |
| Absent | Red | `--c-danger` |

**Layer 2 — Workflow Stage** (what the clerk has done about it)

| Stage | Color | Token |
|---|---|---|
| Awaiting / Pending | Blue | `--c-info` |
| Justified (complete) | Green | `--c-success` |
| Unjustified / Overdue | Red | `--c-danger` |
| Disputed | Red | `--c-danger` |

These two layers are displayed **separately** in the UI — one chip per layer. They do not override each other.

> Example: A row for "Late · Justified" shows two chips — `⚠ Late` (amber) and `✓ Justified` (green). The student is still Late; the workflow is complete.

### KPI Left-Border Accent

| Color | Token | When |
|---|---|---|
| Red | `--c-danger` | Urgent — unjustified, disputed |
| Amber | `--c-warning` | Attention — late, awaiting |
| Blue | `--c-info` | Informational — pending approval |
| Gray | `--c-border-strong` | Neutral count |

---

## 7. Icon System

**Library:** Font Awesome 6.5.0 Solid (`fa-solid`)  
Decorative icons: `aria-hidden="true"` — Interactive icon-only buttons: `aria-label="…"`

### Core Principle — Status vs. Workflow Icons

| Category | Icon style | Examples |
|---|---|---|
| **Student status** | Circle icons (filled) | `fa-circle-check`, `fa-circle-xmark`, `fa-circle-exclamation` |
| **Workflow stages** | Sand clock / time icons | `fa-hourglass-half`, `fa-clock`, `fa-flag` |

This distinction is **intentional and consistent**. A clerk can read the icon shape alone to know whether they are looking at a student's state or a workflow stage.

### Standard Icon Mapping

#### Student Status

| Status | Icon | Rationale |
|---|---|---|
| Present | `fa-circle-check` | Circle family — status |
| Late | `fa-circle-exclamation` | Circle family — status (replaces `fa-door-open`) |
| Absent / No-show | `fa-circle-xmark` | Circle family — status |
| Did not reach class | `fa-person-circle-exclamation` | Circle family — status |

#### Workflow Stages

| Stage | Icon | Rationale |
|---|---|---|
| Awaiting / Pending / Pending approval | `fa-hourglass-half` | Sand clock — workflow |
| Unjustified / Past due | `fa-clock` | Time-based — overdue workflow |
| Disputed | `fa-flag` | Action-needed — workflow |
| Parent replied | `fa-envelope-open-text` | Communication — workflow |
| Justified (complete) | `fa-circle-check` | Complete — workflow done |

#### Navigation

| Section | Icon |
|---|---|
| Dashboard | `fa-gauge-high` |
| Today's records | `fa-clipboard-list` |
| School roster | `fa-table-list` |
| Pending parent replies | `fa-envelope-open-text` |
| Disputes | `fa-triangle-exclamation` |
| Future absences | `fa-calendar-days` |
| Group events | `fa-bus` |
| Classes | `fa-chalkboard` |
| Students | `fa-user-graduate` |
| Teachers | `fa-chalkboard-user` |
| Groups | `fa-people-group` |
| Daily attendance | `fa-chart-column` |
| Audit log | `fa-clock-rotate-left` |

#### Actions

| Action | Icon |
|---|---|
| Search | `fa-magnifying-glass` |
| Notifications | `fa-bell` |
| Help | `fa-circle-question` |
| Refresh / Sync | `fa-rotate` |
| Export | `fa-file-export` |
| Print | `fa-print` |
| Sort | `fa-arrow-down-wide-short` |
| Close panel | `fa-xmark` |
| Send / Remind | `fa-paper-plane` |
| Email | `fa-envelope` |
| Open in Aspen | `fa-arrow-up-right-from-square` |
| Submitted / Done | `fa-check` |
| Parents | `fa-people-roof` |
| Active records | `fa-bell` |

#### Event Types

| Event | Icon |
|---|---|
| Field trip / Bus | `fa-bus` |
| Sports | `fa-futbol` |
| Music / Band | `fa-music` |
| Science | `fa-flask` |
| Arts | `fa-palette` |
| Competition | `fa-trophy` |
| General | `fa-calendar-check` |

### Icon Size Rules

| Context | Size |
|---|---|
| Inside chips | `9px` |
| Card titles | `13px` |
| Nav items | `14px` |
| Event icons | `12–14px` |
| Empty states | `24–28px` |
| Drawer `<h3>` | `11px` |

---

## 8. Parent Reason Chips

Sourced from the Future Absences screen (`reason-tag` classes). These are the canonical reason categories — use them consistently on every screen, every portal.

### Standard Reason Categories

| Reason | Background | Text | Border | Icon |
|---|---|---|---|---|
| Medical (appointment, dental, therapy) | `--c-info-tint` | `--c-info` | `#5B96BC` | `fa-stethoscope` |
| Family (event, commitment, emergency) | `--c-warning-tint` | `--c-warning` | `--c-warning-bord` | `fa-house-heart` |
| Religious (observance, holiday) | `--c-brand-tint` | `--c-brand-ink` | `#6E94BF` | `fa-star-and-crescent` |
| School (field trip, competition, school-sanctioned) | `--c-event-purple` | `--c-event-purple-ink` | `--c-event-purple-bord` | `fa-graduation-cap` |
| Transportation (delay, breakdown, weather) | `--c-neutral-tint` | `--c-ink-muted` | `--c-border-strong` | `fa-bus` |
| Other / Unspecified | `--c-neutral-tint` | `--c-ink-muted` | `--c-border-strong` | `fa-ellipsis` |

### Chip Spec

```css
display: inline-flex; align-items: center; gap: 6px;
padding: 2px 10px; border-radius: var(--r-pill);
font-size: 11px; font-weight: 700;
border: 1px solid;
```

### Rule

The same reason category always uses the same color, icon, and label across all portals. No exceptions. If a clerk sees a blue medical chip in the Clerk portal, a teacher sees the same blue medical chip in the Teacher portal, and a parent sees the same chip in their portal.

---

## 9. Group Events & School Events

### Color (established, do not change)

| Token | Value |
|---|---|
| `--c-event-purple` | `#EEEAFE` — background |
| `--c-event-purple-ink` | `#3F22A6` — text / icons |
| `--c-event-purple-bord` | `#7E68DC` — border |

### Event Avatar

Square rounded (`--r-md`, 6px):

| Size | Context |
|---|---|
| 32px | Standard table/list rows |
| 26px | Compact dashboard rail |
| 56px | Drawer hero |

Default: purple tint bg + purple ink icon  
**Exception — today, student justified:** `--c-success-tint` bg + `--c-success` icon

### Timing Badges

| State | Background | Text | Label |
|---|---|---|---|
| Today | `--c-success-tint` | `--c-success` | "Today" |
| Upcoming | `--c-brand-tint` | `--c-brand-ink` | Date string |

---

## 10. Buttons

### Variants

| Variant | Background | Text | Border | Hover |
|---|---|---|---|---|
| Primary | `--c-brand` | `#fff` | `--c-brand` | `--c-brand-ink` bg |
| Secondary | `--c-surface` | `--c-ink` | `--c-border-strong` | `--c-surface-alt` bg |
| Ghost | `transparent` | `--c-brand` | `transparent` | `--c-brand-tint` bg |
| Danger | `--c-surface` | `--c-danger` | `#E1ABA4` | `--c-danger-tint` bg |

### Sizes

| Size | Padding | Min-height | Font |
|---|---|---|---|
| Default | `8px 14px` | `36px` | `13px / 600` |
| Small | `4px 10px` | `28px` | `12px / 600` |

### Base Spec

```css
display: inline-flex; align-items: center; justify-content: center; gap: 6px;
border-radius: var(--r-md);
font-weight: 600; border: 1px solid transparent;
transition: background 0.12s, border-color 0.12s;
```

### Disabled State

```css
opacity: 0.45;
cursor: not-allowed;
pointer-events: none;
```

Apply to all button variants. Do not change colors — the reduced opacity communicates the disabled state uniformly.

### Icon Buttons (topbar, drawer close)

```css
width: 36px; height: 36px; border-radius: var(--r-md);
background: transparent; border: 1px solid transparent; color: var(--c-ink-muted);
/* hover */ background: var(--c-surface-alt); color: var(--c-ink);
```

Always include `aria-label` on icon-only buttons.

---

## 11. Navigation — Sidebar

### Shell

```css
width: 240px;
background: linear-gradient(180deg, var(--c-sidebar) 0%, var(--c-sidebar-2) 100%);
position: sticky; top: 0; height: 100vh; overflow-y: auto;
```

### Logo Mark

```css
width: 36px; height: 36px; background: var(--c-sidebar-active);
border-radius: var(--r-lg); font-weight: 800; font-size: 16px; color: #fff;
```

### Section Labels

```css
text-transform: uppercase; font-size: 10px; font-weight: 700;
letter-spacing: 0.12em; color: rgba(255,255,255,0.55);
padding: 0 12px; margin-bottom: 4px;
```

### Nav Items

```css
/* Default */ padding: 10px 12px; border-radius: var(--r-md);
color: rgba(255,255,255,0.78); font-size: 13px; font-weight: 500; min-height: 36px;
/* Hover */ background: rgba(255,255,255,0.08); color: #fff;
/* Active */ background: var(--c-sidebar-active); color: #fff; font-weight: 600;
```

### Nav Badges

```css
/* Urgent */ background: var(--c-danger); color: #fff;
/* Neutral count */ background: rgba(255,255,255,0.18); color: #fff;
font-size: 11px; font-weight: 700; padding: 2px 8px; border-radius: var(--r-pill);
```

---

## 12. Topbar

### Shell

```css
background: var(--c-surface); border-bottom: 1px solid var(--c-border);
display: flex; align-items: center; gap: 16px;
padding: 12px 24px; position: sticky; top: 0; z-index: 50; min-height: 64px;
```

### Period Indicator

```css
background: var(--c-brand-tint); color: var(--c-brand-ink);
border: 1px solid #6E94BF; padding: 6px 12px; border-radius: var(--r-md);
font-size: 12px; font-weight: 600;
```

Green 8×8px dot = period currently active.

### User Chip

```css
display: inline-flex; align-items: center; gap: 8px;
padding: 4px 10px 4px 4px;
border: 1px solid var(--c-border); border-radius: var(--r-pill);
background: var(--c-surface); font-size: 12px; min-height: 36px;
/* Avatar */ 28px circle, --c-brand-tint bg, --c-brand-ink text
```

---

## 13. Tables

### Table Card Wrapper

```css
background: var(--c-surface); border: 1px solid var(--c-border);
border-radius: var(--r-lg); overflow: hidden;
```

### Column Headers

```css
background: var(--c-surface-2); border-bottom: 1px solid var(--c-border);
padding: 10px 12px; font-size: 11px; font-weight: 700;
color: var(--c-ink-muted); text-transform: uppercase; letter-spacing: 0.06em;
position: sticky; top: 0; z-index: 1;
```

### Rows

```css
border-bottom: 1px solid var(--c-border-2);
/* hover */ background: var(--c-surface-2); cursor: pointer;
/* selected */ background: var(--c-brand-tint); box-shadow: inset 4px 0 0 var(--c-brand);
/* last row */ border-bottom: 0;
```

### Cells

```css
padding: 12px; vertical-align: middle;
```

### Entity Cell Pattern

```css
display: grid; grid-template-columns: [avatar] 1fr; gap: 12px; align-items: center;
/* name */ font-weight: 700; color: var(--c-ink); font-size: 13px;
/* meta */ font-size: 11px; color: var(--c-ink-subtle); margin-top: 2px;
```

### YTD Bar

```css
height: 6px; border-radius: var(--r-pill);
background: var(--c-neutral-tint);   /* track */
/* fill colors */ ≥90%: --c-success · 75–89%: --c-warning-bord · <75%: --c-danger
```

---

## 14. Detail Drawers

### Layout

```css
/* Panel area with drawer open */
grid-template-columns: 1fr minmax(380px, 520px); gap: 16px;
```

### Shell

```css
background: var(--c-surface); border: 1px solid var(--c-border);
border-radius: var(--r-lg); box-shadow: var(--shadow-md);
display: flex; flex-direction: column; overflow: hidden;
```

### Header

```css
padding: 12px 16px; border-bottom: 1px solid var(--c-border-2);
background: var(--c-surface-2);
/* title */ font-size: 16px; font-weight: 700;
/* close btn */ fa-xmark, 36×36px, aria-label="Close panel"
```

### Hero Area

```css
padding: 16px 16px 12px; border-bottom: 1px solid var(--c-border-2); flex-shrink: 0;
/* avatar */ 56px — circle for people, rounded-square for classes/groups
/* name */ 20px / 700 / --c-ink
/* meta */ chips + text, 12px, gap: 6px, flex-wrap: wrap
```

### Tabs

```css
padding: 10px 14px; font-size: 12px; font-weight: 600; min-height: 40px;
border-bottom: 2px solid transparent; margin-bottom: -1px;
/* active */ color: --c-brand; border-bottom-color: --c-brand;
/* hover */ background: --c-surface-alt;
```

### Section Headers `<h3>`

```css
font-size: 11px; font-weight: 700; color: var(--c-ink-muted);
text-transform: uppercase; letter-spacing: 0.06em; margin-bottom: 8px;
display: flex; align-items: center; gap: 6px;
```

### Info List (Key-Value)

```css
display: grid; grid-template-columns: max-content 1fr; gap: 8px 16px;
padding: 12px 16px; background: var(--c-surface-2);
border: 1px solid var(--c-border-2); border-radius: var(--r-md);
/* dt */ 11px / 700 uppercase / --c-ink-subtle / 0.06em tracking
/* dd */ 13px / 500 / --c-ink
```

### Action Footer

```css
padding: 12px 16px; border-top: 1px solid var(--c-border-2);
background: var(--c-surface-2); display: flex; gap: 8px; flex-wrap: wrap; flex-shrink: 0;
```

Primary action: `btn--primary`. Secondary: `btn--secondary`. No ghost buttons in footer.

---

## 15. Cards & KPI Tiles

### Generic Card

```css
background: var(--c-surface); border: 1px solid var(--c-border);
border-radius: var(--r-lg); overflow: hidden;
/* header */ 12px 16px padding, 14px/700 title, 12px/--c-ink-subtle subtitle
/* count badge */ pill, --c-neutral-tint bg, 12px/700, padding: 2px 8px
/* footer */ 8px 16px, --c-surface-2 bg, border-top --c-border-2
```

### KPI Tiles

```css
background: var(--c-surface); border: 1px solid var(--c-border);
border-radius: var(--r-lg); padding: 12px 16px;
display: grid; grid-template-columns: auto 1fr; gap: 12px; align-items: center;
/* left accent */ border-left: 3px solid [urgency color]
/* icon */ 30×30px, --r-md, semantic tint bg
/* value */ 20px/700/--c-ink/tabular-nums
/* label */ 12px/600/--c-ink-muted
/* meta */ 11px/400/--c-ink-subtle
/* hover */ border-color: --c-border-strong; box-shadow: --shadow-md
```

---

## 16. Filter Bar

```css
background: var(--c-surface); border: 1px solid var(--c-border);
border-radius: var(--r-lg); padding: 12px 16px;
display: flex; align-items: center; gap: 12px; flex-wrap: wrap;
/* search input */ border: 1px solid --c-border-strong; --r-md; padding: 6px 10px
/* select */ same border/radius as search input
/* separator */ 1px × 24px, --c-border-2
/* group label */ 11px/700/uppercase/0.06em/--c-ink-subtle
```

---

## 17. Forms

Used in the Future Absences declaration modal and other data-entry flows.

### Form Field

```css
/* Label */ display: block; font-size: 12px; font-weight: 700; color: var(--c-ink); margin-bottom: 8px;
/* Required mark */ color: var(--c-danger); margin-left: 2px;
/* Hint */ font-size: 11px; color: var(--c-ink-subtle); margin-top: 4px;
```

### Input / Select / Textarea

```css
width: 100%; padding: 8px 12px;
border: 1px solid var(--c-border-strong); border-radius: var(--r-md);
background: var(--c-surface); font-family: inherit; font-size: 13px; color: var(--c-ink);
min-height: 36px;
/* focus */ outline: 3px solid var(--c-focus); outline-offset: 0;
/* error state */ border-color: var(--c-danger);
```

### Radio Card

```css
display: flex; align-items: flex-start; gap: 8px;
padding: 8px 12px; border: 1px solid var(--c-border); border-radius: var(--r-md);
background: var(--c-surface); cursor: pointer;
/* checked */ border-color: var(--c-brand); background: var(--c-brand-tint);
```

### Period Pill Checkbox

```css
display: inline-flex; align-items: center; gap: 6px;
padding: 6px 12px; border: 1px solid var(--c-border); border-radius: var(--r-pill);
font-size: 12px; font-weight: 600; color: var(--c-ink-muted); cursor: pointer;
/* checked */ background: var(--c-brand-ink); color: #fff; border-color: var(--c-brand-ink);
```

### Modal

```css
width: 560px; max-width: 92vw; border: 1px solid var(--c-border);
border-radius: var(--r-xl); background: var(--c-surface);
box-shadow: 0 24px 64px rgba(15,37,70,0.25);
/* header */ padding: 16px 24px; --c-surface-2 bg; 16px/700 title
/* body */ padding: 16px 24px; max-height: 70vh; overflow-y: auto
/* footer */ padding: 12px 24px; --c-surface-2 bg; flex, space-between
/* backdrop */ rgba(15,37,70,0.45); backdrop-filter: blur(2px)
```

---

## 18. Empty States, Skeletons & Feedback

### Empty State

```css
padding: 24px 16px; text-align: center; color: var(--c-ink-subtle); font-size: 13px;
/* Icon */ font-size: 24–28px; color: var(--c-border-strong); display: block; margin-bottom: 8px;
```

### Skeleton Screen (Loading State)

Use skeleton rows when table data is loading. Replace content with animated shimmer placeholders.

**Skeleton line:**

```css
.skeleton-line {
  height: 12px;
  background: linear-gradient(90deg, var(--c-border-2) 25%, var(--c-surface-alt) 50%, var(--c-border-2) 75%);
  background-size: 400% 100%;
  animation: shimmer 1.4s ease infinite;
  border-radius: var(--r-sm);
}

@keyframes shimmer {
  0%   { background-position: 100% 0; }
  100% { background-position: -100% 0; }
}
```

**Skeleton avatar:**

```css
.skeleton-avatar {
  border-radius: var(--r-pill);   /* circle for people */
  background: var(--c-border-2);
  /* same size as real avatar */
}
```

**Skeleton table row** — structure mirrors the real table but all cells contain skeleton lines:

```
[skeleton-avatar 36px] [skeleton-line 60%]  [skeleton-line 40%]  [skeleton-line 30%]
```

Show 5–8 skeleton rows while data loads. Fade in real rows once data arrives.

**Skeleton card** — use for KPI tiles and summary cards:

```css
.skeleton-card {
  background: var(--c-surface); border: 1px solid var(--c-border);
  border-radius: var(--r-lg); padding: 12px 16px;
  display: flex; flex-direction: column; gap: 8px;
}
/* Contains 2–3 skeleton lines of varying widths */
```

### Toast Notifications

```css
background: var(--c-surface); border: 1px solid var(--c-border);
border-left: 4px solid [semantic color]; box-shadow: var(--shadow-lg);
padding: 12px 16px; border-radius: var(--r-md); font-size: 13px; max-width: 360px;
/* Position */ fixed; bottom: 24px; right: 24px; z-index: 90
```

Auto-dismiss: 5 seconds. `--c-success` for confirmations, `--c-info` for informational.

### Concurrency Indicator

```css
background: #FFF5E6; color: #804500;
border: 1px dashed #B97F38;
padding: 2px 8px; border-radius: var(--r-pill);
font-size: 11px; font-weight: 600;
```

Used when another clerk is handling a record simultaneously. Unique pattern — preserve.

### Info / Warning Banner

```css
background: [semantic-tint]; border: 1px solid [semantic-border]; color: [semantic-ink];
border-radius: var(--r-lg); padding: 12px 16px;
display: flex; align-items: flex-start; gap: 12px; font-size: 13px;
```

---

## 19. Inconsistencies Found & Recommendations

### Priority 1 — Icon Standardization

| # | Issue | Screens | Fix |
|---|---|---|---|
| 1 | Late status uses `fa-door-open` in Dashboard and Today's Records | Dashboard, Today's Records | Replace with `fa-circle-exclamation` everywhere. Late is a student status → circle icon family. |
| 2 | "Reminded" submit chip in Teachers uses `fa-bell` but other awaiting states use `fa-hourglass-half` | Teachers | Standardize all workflow-waiting states to `fa-hourglass-half`. Use `fa-bell` only for the Remind action button. |
| 3 | `fa-clock` used for both "Period (upcoming)" and "Unjustified/Past due" | Dashboard, Teachers | "Period upcoming" → `fa-clock` (OK). "Unjustified past due" → `fa-clock` with red chip is acceptable, but consider `fa-circle-exclamation` for more urgency. |

### Priority 2 — Visual Consistency

| # | Issue | Screens | Fix |
|---|---|---|---|
| 4 | Teacher/Student avatar colors are hardcoded hex values | Teachers, Students | Define `--c-avatar-1` through `--c-avatar-8`. Assign by entity ID hash. |
| 5 | Groups drawer hero is 48px; others are 56px | Groups drawer | Standardize all drawer hero avatars to 56px. |
| 6 | "Reminded" chip uses red (`--c-danger-tint`) | Teachers | Use amber (`--c-warning-tint`). Reminded = action taken but pending response. Red = no action taken. |
| 7 | Terminology: "Awaiting" vs "Pending" mixed | Multiple | Standard: "Awaiting" = waiting on external party. "Pending" = waiting on the clerk. |

### Priority 3 — Documentation Applied

| # | Decision | Rule |
|---|---|---|
| 8 | Period/class tags are square on some screens | Defined as Type 5 Entity Tags (`--r-md`). Must be square on all screens consistently. |
| 9 | Justified status is green | Correct and intentional. Justified = workflow complete. Green = done. Not an inconsistency. |
| 10 | Source badges are square | Defined as Type 5 Entity Tags. Acceptable and intentional. |

### Priority 4 — New Standards Added

| # | Addition |
|---|---|
| 11 | Parent reason chips standardized from Future Absences screen (Section 8) |
| 12 | Disabled button state defined: `opacity: 0.45; cursor: not-allowed; pointer-events: none` |
| 13 | Skeleton screen pattern defined (Section 18) |
| 14 | Form component patterns documented from Future Absences modal (Section 17) |

---

*ClassTrack Design System v1.1 — Updated May 2026*  
*Documentation only — no prototype screens modified*
