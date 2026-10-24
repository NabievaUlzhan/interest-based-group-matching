# Functional and Non-Functional Requirements

| Document attribute | Value |
|---|---|
| Project | Development of a Platform for Interest-Based Group Matching and Offline Social Activities |
| Task | U3 — Define Functional and Non-Functional Requirements |
| Team | Fariza — Backend Developer; Syndaly Yerzhan — Frontend Developer; Ulzhan — Full-stack Developer / QA |
| Status | Preliminary requirements baseline; team and supervisor review pending |
| Prepared on | 24 October 2026 |

## 1. Purpose and Scope

This document defines the functional and non-functional requirements for the proposed web platform for discovering interest-based groups and offline activities. It uses the supplied README, user flows, existing-systems comparison, and completed interview summaries as project inputs.

The README explicitly describes the feature scope and technology choices as preliminary. Therefore, the requirements below are proposals for review, not a claim that the scope has been approved, the platform has been implemented, or the proposed features have been validated.

The initial scope covers account access, profiles and interests, group discovery and recommendations, offline event discovery, event creation, and event participation. A native mobile application, payments, private messaging, attendance verification, and automatic location detection are not established as requirements by the supplied documents.

## 2. Priority Definitions

- **Must** — required for the agreed MVP; completion depends on satisfying it.
- **Should** — important, but may be deferred only with a documented reason and agreement.
- **Could** — useful if time and scope permit.

Priorities are proposed and must be confirmed by the team and supervisor. They are not yet an approved project baseline.

## 3. Functional Requirements

| ID | Priority | Requirement | Verifiable acceptance criterion |
|---|---|---|---|
| FR-01 | Must | The system shall allow a visitor to create an account using the registration fields approved for the MVP. | Submit valid required fields and verify that account creation is confirmed. Submit missing or invalid fields and verify that field-specific errors appear and success is not reported. |
| FR-02 | Must | The system shall allow registered users to log in and log out. | Valid credentials provide authenticated access; invalid credentials show a non-sensitive error. After logout, authenticated actions require logging in again. |
| FR-03 | Must | The system shall allow a registered user to view and update their profile using the fields approved for the MVP. | Save a profile change, reload or reopen the profile, and verify the saved value. A failed save must not display a success state. |
| FR-04 | Must | The system shall allow a registered user to select, save, and edit interests. | Save a set of interests, revisit the profile, and verify the same selections are shown. If saving fails, retain the edits and show that they were not saved. |
| FR-05 | Must | The system shall let visitors browse available interest groups and view each group's available summary information. | With seeded group data, verify that each group listing shows its name and summary. When no groups are available, show an explicit empty state rather than an error or blank page. |
| FR-06 | Should | The system should provide group suggestions based on a registered user's saved interests. | Given a defined test profile and a fixed set of sample groups, verify that suggestions follow the recommendation rule selected for the MVP. If no suggestions can be produced, general group browsing remains available. The recommendation method is not finalized by this requirement. |
| FR-07 | Must | The system shall display details for a selected offline event. | Open an available event and verify that its available title, description, date, time/time zone, location or meeting instructions, organizer, and participation status are displayed. An unavailable event must show a clear status. |
| FR-08 | Must | The system shall allow an authorized user to create and update an offline event using the fields required for publication. | Verify that required fields and a valid future date/time are checked before publication; a successful save or publication shows the confirmed state. An unauthorized user cannot publish. Draft behavior is included only if approved for the MVP. |
| FR-09 | Must | The system shall allow a registered user to register for an available event and cancel that registration when permitted. | A successful registration is shown as confirmed in event details. Duplicate submissions are prevented or handled safely. A permitted cancellation updates the status only after confirmation; on failure, the last confirmed status is retained or refreshed. |
| FR-10 | Must | The system shall let a registered user view their event registrations. | After registering for an event, verify that it appears in the user's activity/registration list. After a confirmed cancellation, verify that the list and event details show consistent status. |
| FR-11 | Must | The system shall let users search and filter group listings using supported text and interest categories. | With a known test dataset, verify that a text query and selected interest filters return the expected groups. Clearing filters restores the unfiltered listing. The precise combination rule for multiple interests must be agreed and documented. |
| FR-12 | Should | The system should let a registered user join an eligible group and display the resulting membership status. | After a successful join, show confirmed membership; a guest is asked to log in. A failed join must not show membership as confirmed. Group approval, private groups, and leaving a group require a scope decision before implementation. |

### 3.1. Functional Scope Notes

- **Group membership and event registration are separate.** Joining a group must not automatically register a user for an event.
- FR-06 is a proposed capability, not a commitment to a particular algorithm or proof that recommendations will be effective. The algorithm and evaluation method belong in the evaluation plan and require team agreement.
- Capacity limits, waitlists, event approval/moderation, group join approval, and cancellation deadlines are not settled in the supplied documents. If event capacity is included, the system must enforce it consistently on the server and test simultaneous registration attempts.
- The user-flow document proposes immediate group membership in one section but uses “Submit join request” in its diagram. This is an unresolved interaction/policy choice; the interface must not show “Member” until membership is actually confirmed.
- Exact registration/profile fields, password policy, account recovery, organizer eligibility, public visibility of location and profile information, and event cancellation rules must be agreed before implementation.
- The technology stack in the README (React, TypeScript, Python, FastAPI, PostgreSQL) is preliminary; this requirements document does not make it an approved architectural decision.

## 4. Non-Functional Requirements

The targets below are **proposed test targets**, not measured results or formal compliance claims. The team and supervisor should confirm that they are feasible and appropriate before the evaluation baseline is approved.

| ID | Priority | Requirement | Measurement and acceptance criterion |
|---|---|---|---|
| NFR-01 | Must | **Usability:** users should be able to complete the core journeys with limited assistance. | Conduct a documented usability test covering account access, interest selection, group discovery, event details, and event registration. Record completion, errors, assistance, and feedback. Proposed target: at least 80% of observed task attempts completed without moderator intervention. Approve the sample and target before testing. |
| NFR-02 | Must | **Performance:** common group/event list and detail requests should respond within an agreed time under a defined test load. | Test a documented build and environment with a stated dataset and concurrency. Proposed target: p95 response time ≤ 2 seconds for group/event list and detail requests at up to 20 simulated concurrent users. Record actual measurements; do not report the target as achieved before testing. |
| NFR-03 | Must | **Security:** authenticated and permission-restricted actions must reject unauthorized access. | Test protected actions as a guest, a regular user, and a user without organizer permission. Unauthorized actions must be rejected and must not expose protected data. Review password handling and input validation. |
| NFR-04 | Must | **Privacy:** public views and responses should expose only fields approved for public discovery and event participation. | Compare public profile, group, and event outputs against an approved field/visibility checklist. Verify that private account fields are not exposed and that venue/address visibility follows the agreed policy. |
| NFR-05 | Must | **State consistency and reliability:** confirmed group membership and event-registration states should agree across relevant screens. | Test success, failure, duplicate submission, retry, and concurrent registration/join scenarios. Compare stored state with event/group details and the user's activity/profile view. After the final result is known, no contradictory confirmed status should remain. |
| NFR-06 | Should | **Responsive interface:** core screens should remain usable on mobile, tablet, and desktop viewport sizes. | Test proposed widths of 360 px, 768 px, and 1366 px in documented browsers. Essential content and actions must remain available without page-level horizontal scrolling or clipped controls. |
| NFR-07 | Must | **Basic accessibility:** core journeys should support keyboard operation and understandable labels and feedback. | Manually test navigation, forms, interest selection, dialogs, and RSVP using a keyboard. Verify visible focus, meaningful labels, associated error messages, and status that is not conveyed by color alone. Agree a contrast target and measure it; do not claim formal accessibility compliance without appropriate testing. |

### 4.1. Measurement Rules

For each NFR test, record the date and build, environment/browser/device, dataset, sample size or concurrency, test steps and tools, observed measurements, pass/fail outcome, and defects or limitations. Until tested, mark the result **Pending** or **Not tested**. Targets can be revised before the baseline is approved, with the reason recorded.

## 5. Interview Evidence, Assumptions, and Design Decisions

The supplied `interviews.md` records the completed interviews with four anonymized participants (P1–P4). The small exploratory sample informs requirements but should not be generalized to all students.

| Interview finding | Requirements potentially related | Evidence status and next action |
|---|---|---|
| Finding groups/people with shared interests (summaries P1, P2, P4) | FR-04, FR-05, FR-06, FR-11 | Reported across the interview summaries for P1, P2, and P4. This supports investigating interest-based discovery; it does not by itself prove that a separate platform is preferred. |
| Activity information encountered through different channels (summaries P1, P2, P4) | FR-05, FR-07, FR-11 | Reported across the interview summaries for P1, P2, and P4. Centralized listings are a candidate response, not a proven solution. |
| Coordinating schedules and availability (summaries P2, P4) | FR-07, FR-08, FR-09 | Reported in the summaries for P2 and P4. Clear scheduling information is a relevant requirement candidate. |
| Uncertainty about joining unfamiliar people (summary P3) | FR-07; potentially event-description and privacy requirements | An individual experience reported by P3. It should inform consideration of clear group/event information without being generalized to all students. |
| Finding enough people to participate (summaries P2, P4) | FR-05, FR-06, FR-08, FR-09 | Reported in the summaries for P2 and P4. Group discovery and event creation are candidate responses; their usefulness should be evaluated during prototype testing. |

The following are **design assumptions or decisions requiring review**, not established interview findings:

- Users may prefer one place to discover relevant groups and offline activities.
- Shared interests may be useful for group suggestions.
- Clear event details may help users decide whether to attend.
- A transparent explanation of why a group is suggested may be useful.
- Immediate group joining and direct event registration may be suitable default flows.
- A responsive web platform may suit the intended users and organizers.

Treat the interview summaries as the finalized research input, while distinguishing recurring observations from individual experiences. Four participants provide exploratory evidence and do not represent all students. Requirements are informed by interview findings but still need clear acceptance criteria and implementation/testing.

## 6. Open Decisions Before Implementation

The following decisions affect requirements, interface behavior, and testing:

1. Confirm the MVP and exclusions against the supervisor-approved proposal, when available.
2. Confirm the registration/profile fields, password policy, and account recovery behavior.
3. Decide whether group joining is immediate or request/approval-based.
4. Decide whether event capacity, waitlists, event moderation, drafts, and cancellation deadlines are in scope.
5. Define organizer permissions and whether an organizer may edit or cancel a published event.
6. Define public visibility of user interests, organizer details, and precise event locations.
7. Select and document the initial recommendation baseline and the data it may use.
8. Approve the measurable NFR targets and the evaluation conditions.
9. Preserve the completed interview findings in `interviews.md` and use participant labels when linking requirements to reported themes.

## 7. Requirement Review and Change Control

For each change, record the requirement ID, change rationale, evidence or decision source, impact on related requirements and milestones, and review/approval status. Update linked user flows and evaluation tests when a requirement changes.

Before implementation, confirm that:
- all Must requirements are within the agreed MVP;
- priorities have been reviewed by the team and supervisor;
- unresolved permissions, privacy, capacity, and cancellation rules are documented;
- NFR targets and test conditions are approved;
- interview-informed needs are linked to the relevant participant labels, while assumptions and proposed solutions remain clearly labeled.

## 8. Conclusion

This document proposes twelve functional requirements and seven non-functional requirements with acceptance criteria or measurable test methods. It aligns the core requirement IDs FR-05–FR-10 with the needs-to-requirements mapping already used in `interviews.md`: group browsing, recommendations, event information, event creation/update, event registration/cancellation, and viewing registrations.

The README is treated as a preliminary project description, and the user-flow document is treated as a proposal rather than an approved specification. The completed interview summaries are treated as finalized research input; recurring observations and individual experiences are distinguished, and the small sample is not generalized to all students. No implementation, test success, recommendation accuracy, or formal compliance is claimed.

## 9. U3 Acceptance Criteria Check

| Acceptance criterion | Evidence in this document | Status |
|---|---|---|
| Functional requirements FR-01–FR-12 are reviewed. | Section 3 defines FR-01–FR-12. | Drafted; team/supervisor review pending |
| Non-functional requirements NFR-01–NFR-07 are reviewed. | Section 4 defines NFR-01–NFR-07. | Drafted; target approval and testing pending |
| Every Must requirement has a verifiable acceptance criterion. | Section 3. | Criteria included; confirm scope and test data during review |
| NFRs are measurable/testable. | Section 4 and Section 4.1. | Proposed measurement methods and targets; approval/testing pending |
| Must/Should/Could are used consistently. | Sections 2–4. | Applied; priority approval pending |
| Interview-supported requirements are distinguished from assumptions. | Section 5. | Completed interview summaries used; recurring themes and individual experiences are distinguished from assumptions |
| `docs/requirements.md` is created and committed. | Save this file at `docs/requirements.md`. | File prepared; commit pending |
