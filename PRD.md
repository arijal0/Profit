# Product Requirements Document (PRD) — Revised V1.1

**Product Name:** Person (TBD)
**Document Version:** 1.1
**Date:** June 2026

## Revision History

| Date | Version | Description | Author |
| --- | --- | --- | --- |
| Jun 21, 2026 | 1.0 | Initial PRD Draft | Ankit Rijal |
| 06/22/2026 | 1.1 | Revised MVP Scope & Technical Specs | Ankit Rijal |

## 1. Executive Summary & Positioning

### 1.1 Product Positioning Statement

> "A daily intelligence briefing for ambitious software engineers who want to improve their technical depth, understand markets, and navigate career uncertainty."

### 1.2 Core Philosophy

- **Progressive Disclosure over Content Walls:** Content must be hyper-dense and authoritative but organized hierarchically so users control their depth of consumption.
- **Demanding, Non-Cringe Persona:** The app acts as an elite technical interviewer and a sharp market macro analyst. It uses a challenging, direct "tough-love" tone rather than cheap insults.
- **Asynchronous Zero-Wait Delivery:** Heavy compute, RAG operations, and multi-agent loops run overnight. The user receives an instantly rendered package at launch.

## 2. Updated MVP Scope Strategy

To ensure technical feasibility, minimize generation costs, and maximize retention, the product architecture is split into a streamlined MVP core and a planned Phase 2 rollout.

| Module | Status (MVP V1.1) | Execution Strategy |
| --- | --- | --- |
| Tech Learning Engine | ✅ KEEP | Combined OS, DBMS, DSA, and System Design tracks. |
| Portfolio Tracker | ✅ KEEP | Plaid connected, tracking macro causality on active user holdings. |
| International Student Module | ✅ KEEP | Focused on immigration, hiring freezes, and OPT/H-1B timelines. |
| Global Geopolitics | ❌ PHASE 2 | Deferred; news must tie to student or market vectors. |
| Alternative Stock Discovery | ❌ PHASE 2 | Algorithmic scanning for unowned trending equities deferred. |

## 3. Revised Functional Requirements (FRs)

### 3.1 User Profile, State & Brokerage Integration

- **FR-1.1 Onboarding:** Users select domain filters (OS, DBMS, DSA, System Design, Big Tech Interviewing) and toggle the `is_international_student` flag.
- **FR-1.2 Plaid Brokerage Sync:** Users link their portfolio via read-only Plaid Investments API tokens. The backend reads active holdings nightly to build the ticker list.
- **FR-1.3 Manual Entry Fallback:** A clean fallback text input for users choosing not to authenticate their brokerages directly.

### 3.2 The Tech Learning Engine & User Memory (Enhanced)

- **FR-2.1 UI Architecture (Progressive Disclosure):** Tech lessons must follow a strict accordion structure:
  - **The Reality Check:** A single high-caliber interview question.
  - **The Key Insight:** A punchy 3-minute read delivering the core architectural concept.
  - **Deep-Dive [Expandable]:** Low-level system pathways, memory buffers, and deep technical context.
  - **Code & Architecture [Expandable]:** Executable pseudo-code, database schemas, or visual layouts.
- **FR-2.2 User Learning Memory:** The database logs concept completions, quiz performance, and weak points. Future nightly generations must dynamically inject scenario variations to reinforce gaps.
- **FR-2.3 Content Metadata Scoring:** Every lesson includes an automated header metadata layer:
  - Difficulty Score (e.g., 8/10).
  - Novelty Level (High/Medium/Low based on user profile history).
  - Interview Frequency (e.g., "Highly Common in FAANG Infrastructure Streams").

### 3.3 Deep-Dive Market & Portfolio Tracker

- **FR-3.1 Macro Causal Analysis:** The application maps economic causality on active holdings, isolating catalysts such as Federal Reserve yields' effect on software equity discounting.
- **FR-3.2 7-Day Historical Time Machine:** Collapsible drawers maintain a cached timeline of daily post-mortems for any asset currently held in the sync.

### 3.4 International Student Matrix

- **FR-4.1 Tactical Intelligence:** If `is_international_student == true`, the system generates tracks for federal policy adjustments, visa processing updates (F-1, OPT, H-1B), and regional tech employment flows.

### 3.5 Core Content Platform Enhancements

- **FR-5.1 Granular Feedback Loop:** Every content block implements a lightweight feedback model: Useful, Not Useful, Too Basic, and Too Advanced.
- **FR-5.2 Explicit Citation Layer:** For market analysis and visa tracking, every factual claim requires a structured metadata citation block anchoring the source back to primary databases (e.g., SEC EDGAR, Fed releases).

## 4. Non-Functional Requirements (NFRs)

### 4.1 Enhanced AI Pipeline & Quality Control

- **NFR-1.1 Segmented Agent Workflow:** The backend utilizes a 6-tier pipeline: Extraction, Clustering, Contextualization, Narrative Synthesis, Citation Mapping, and Quality Validation.
- **NFR-1.2 Quality Validation Layer:** The Validator agent acts as a programmatic gatekeeper, blocking formatting errors, hallucinations, or missing components.

### 4.2 Data Sourcing & Credibility Constraints

- **NFR-2.1 Primary Feed Overrides:** The pipeline prioritizes high-fidelity sources like SEC EDGAR filings, Alpha Vantage news, and official Department of State Visa Bulletins over generic RSS feeds.
- **NFR-2.2 Alternative Data De-Risking:** Narrative engines are legally constrained to treat regulatory disclosures as neutral data vectors rather than definitive price indicators.

### 4.3 Technical Architecture Specifications

- **NFR-3.1 Framework Architecture:** The core application utilizes FastAPI to leverage native asynchronous concurrency for parallel third-party lookups.
- **NFR-3.2 Long-Running Workflow Management (Revised V1.1):** For the V1 MVP, the system uses **Celery** for orchestrating the overnight multi-agent pipeline, with **Redis** acting as both the task broker and the result backend. This replaces the previously specified Temporal engine to keep the MVP infrastructure footprint manageable. (Temporal remains a candidate for a future phase if deterministic workflow guarantees become necessary.)
- **NFR-3.3 Database State Storage:** All text fields, user profiles, and historical caches are managed in a scalable PostgreSQL relational database.
- **NFR-3.4 Caching Layer:** **Redis** additionally serves as the application caching layer (e.g., the pre-rendered daily intelligence package for zero-wait launch delivery, session state, and transient lookups), in addition to its role as the Celery broker/backend.
- **NFR-3.5 Client Framework:** The native iOS client is built with **React Native (Expo)**.
