# Personal Site Redesign — Design Spec
**Date:** 2026-04-11
**Status:** Approved

---

## Overview

Revamp Jonathan Martin's personal site (`index.html`) from its current generic dark glassmorphism aesthetic into a product-grade editorial design. The site must communicate: *creative, product-focused senior software engineer with strong leadership and deep investment in agentic engineering techniques.*

**Primary audience:** Recruiters and consulting clients.
**Goal:** Make a confident first impression that signals taste, seniority, and product sensibility.

---

## Typography

| Role | Font | Weight/Style |
|------|------|-------------|
| Display / Name | **Fraunces** (variable serif, Google Fonts) | 700–900 |
| Body / UI | **Geist** (Google Fonts) | 300–600 |
| Monospace accents | **Geist Mono** (Google Fonts) | 400 — for handle, tech stack, dates |

**Rationale:** Fraunces is editorial and distinctive — no other engineer portfolio uses it. Geist is clean and slightly technical (Vercel lineage). The combination reads as someone with genuine taste, not a default template.

---

## Colour System

All colours defined as CSS custom properties, switching via `prefers-color-scheme`.

| Token | Light | Dark |
|-------|-------|------|
| `--bg` | `#FAFAF7` (warm off-white) | `#0E0E0C` (near-black, warm) |
| `--text-primary` | `#1A1A1A` | `#F0EFE9` |
| `--text-secondary` | `#4A4A47` | `#A8A89E` |
| `--accent` | `#D4490A` (burnt orange) | `#E85A1A` (slightly brighter) |
| `--border` | `rgba(26,26,26,0.12)` | `rgba(240,239,233,0.12)` |
| `--surface` | `#F2F1EC` | `#181816` |

**One accent colour only** — used for: name highlight on hover, section markers, link underlines, card hover states.

---

## Layout

### Desktop (≥768px)
Two-zone fixed layout filling the full viewport:

- **Left sidebar (40%):** Fixed/sticky. Contains identity — photo, name, handle, tagline, social links, contact info.
- **Right content (60%):** Scrollable. Contains all prose and sections.

A single faint vertical rule separates the zones.

### Mobile (<768px)
- Sidebar collapses to a compact sticky header: small circular photo, name, handle, social icon row.
- All content sections stack below in a single column.

---

## Content Sections

### Sidebar (left)
1. Profile photo — rectangular crop with subtle border, no circle
2. Name: `Jonathan Martin` in Fraunces display
3. Handle: `jono20201` in Geist Mono, muted
4. Tagline: "Father, entrepreneur and software engineering leader." — smaller, secondary colour
5. Social links: GitHub, StackOverflow, X, LinkedIn — icon + label, vertical stack on desktop
6. Contact: email + phone

### Main content (right)
1. **Value proposition** — 1 punchy sentence opener, larger type, Fraunces italic
2. **About** — existing bio paragraphs, lightly edited for flow
3. **What I can help you with** — 3–4 items, each: bold lead phrase (Fraunces) + 1–2 sentence description. Suggested items:
   - Scaling engineering teams & technical leadership
   - Building cloud-native, secure payment/fintech systems
   - Agentic software engineering & AI-accelerated product delivery
   - AWS architecture & infrastructure-as-code (Terraform)
4. **Tech & expertise** — horizontal tag cloud in Geist Mono pill tags
5. **Notable work** — WSD Connector for Confluence + Norfolk Developers Terraform talk
6. **Contact CTA** — brief closing sentence + email link (visible on mobile where sidebar contact is hidden)

---

## Motion & Interactions

All CSS-only, no JavaScript required.

| Element | Animation |
|---------|-----------|
| Page load — main content | Fade-in + translateY(16px → 0), staggered `animation-delay` per section |
| Link hover | Accent underline draws in from left via `transform: scaleX(0→1)` |
| "What I can help with" cards | Left border accent bar appears on hover |
| Nav/social links | Colour shift to accent on hover, `transition: color 0.2s` |
| Profile photo | No hover scale — gentle filter desaturate → full colour on hover |

---

## Background & Texture

- Very subtle grain overlay via inline SVG `feTurbulence` filter on a pseudo-element
- No background image — solid colour with grain creates depth without distraction
- Sidebar and content share the same background; the vertical rule provides zone separation

---

## Technical Constraints

- **Single HTML file** — all CSS inline in `<style>`, no build step
- **No JavaScript** — all interactions via CSS only
- **Google Fonts** — Fraunces, Geist, Geist Mono via `@import`
- **Font Awesome 7** — existing CDN link kept for social icons
- **`prefers-color-scheme`** — full dark/light support via CSS custom properties
- **Responsive** — mobile-first, breakpoints at 768px and 1200px
- Existing assets (`assets/me.jpeg`, favicons) kept in place

---

## Out of Scope

- JavaScript interactions or frameworks
- Multiple pages
- Blog or writing section
- Project portfolio (no featured projects currently)
- Any backend or form handling for contact
