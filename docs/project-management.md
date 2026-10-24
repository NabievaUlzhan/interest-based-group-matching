# Project Management: Risks and Milestones

| Document Attribute | Value |
|---|---|
| Project | Development of a Platform for Interest-Based Group Matching and Offline Social Activities |
| Task | IBS-5 — U5. Identify Project Risks and Define Milestones |
| Team | Fariza — Backend Developer; Syndaly Yerzhan — Frontend Developer; Ulzhan — Full-stack Developer / QA |
| Supervisor | Alshynov Shyngys Kairatuly |
| Status | Proposed plan; milestone dates pending supervisor approval |
| Prepared on | 24 October 2026 |

## 1. Purpose and Status

This document identifies key project risks, mitigation measures, and six milestones for the platform. All ratings and dates are proposals, not confirmed project facts. The team should review them with the supervisor and revise them if the approved scope or academic deadline differs.

**All dates in Section 5 are proposed and pending supervisor approval. They are not an approved schedule baseline.**

## 2. Risk Assessment

Probability and impact use a qualitative Low / Medium / High scale. Low probability means unlikely; Medium means plausible; High means likely or difficult to avoid. Low impact is minor, Medium is noticeable but manageable, and High may significantly affect core functionality, schedule, or user trust. Ratings are initial estimates and should be reviewed during project check-ins.

## 3. Project Risk Register

| ID | Risk | Probability | Impact | Mitigation Measure | One Named Owner |
|---|---|---|---|---|---|
| R1 | **Cold-start recommendations:** new users may have few declared interests, and new groups may have little interaction history, resulting in empty or irrelevant suggestions. | High | Medium | Preserve general group browsing when personalization data is missing. Start with an explainable baseline based on declared interests, define test cases, and evaluate relevance before presenting suggestions as personalized. | Fariza — Backend Developer |
| R2 | **API/frontend mismatch:** frontend and backend may disagree on field names, payloads, validation, or error formats, breaking screens or delaying integration. | Medium | High | Agree on API contracts and example payloads before integration; document success and error responses; review contract changes together; test endpoints and key user journeys early. | Fariza — Backend Developer |
| R3 | **RSVP capacity errors:** concurrent or incorrect registration handling may exceed an event's participant limit or show inaccurate availability. | Medium | High | Confirm whether capacity limits are in scope. If enabled, enforce capacity on the server at registration time and test full events, last-seat contention, duplicate registrations, cancellations, and retries. If limits are outside the MVP, record that decision explicitly. | Fariza — Backend Developer |
| R4 | **Privacy and offline safety:** public listings may expose excessive personal/location information, or users may lack enough information to assess an offline activity safely. | Medium | High | Minimize public personal data; decide which venue details are visible before registration; show clear event time, meeting instructions, and organizer information; review reporting/moderation and safety guidance with the supervisor. Do not claim that the interface guarantees safety. | Ulzhan — Full-stack Developer / QA |
| R5 | **Schedule constraints:** research, implementation, integration, or testing may take longer than expected, leaving insufficient time for fixes and documentation. | High | High | Split work into small tasks, track blockers and dependencies in YouTrack, review progress weekly, prioritize the agreed MVP, reserve time for integration/regression testing, and escalate scope or schedule risks early. | Syndaly Yerzhan — Frontend Developer |
| R6 | **Unclear or changing requirements:** unresolved decisions about permissions, group joining, event publication, or MVP scope may cause rework. | Medium | High | Keep requirements and open questions documented, review changes with the team and supervisor, and record decisions before implementation. | Ulzhan — Full-stack Developer / QA |
| R7 | **Usability problems:** users may not understand group discovery, recommendation explanations, event details, or participation status. | Medium | Medium | Review the prototype against user flows; conduct usability checks when participants are available; record observed difficulties and revise unclear labels, navigation, and feedback. | Syndaly Yerzhan — Frontend Developer |
| R8 | **Insufficient verification:** defects in forms, membership status, event details, or RSVP flows may remain undetected until the final demonstration. | Medium | High | Test normal, empty, invalid, failed, and retry states; test integrated user journeys; record defects and retest fixes before marking a milestone complete. | Ulzhan — Full-stack Developer / QA |

Risk owners are individually accountable for monitoring and reporting their risks. Mitigation may require help from other team members. Ratings are estimates, not measured probabilities.

## 4. Risk Monitoring and Response

Review the risk register during regular progress meetings and whenever a major requirement, dependency, or schedule changes. Each owner should check the risk rating, monitor mitigation actions, report blockers, and record significant changes. Escalate high-impact issues to the supervisor when the team cannot resolve them independently. If a risk occurs, assess its effect, agree on corrective action, and update the schedule where needed.

## 5. Main Project Milestones (M1–M6)

The dates below are **proposed planning dates, pending supervisor approval**. They assume work continues from late October 2026 into early 2027. Confirm the academic deadline and dependencies before treating these dates as a baseline.

| ID | Milestone | Proposed Target Date | Key Deliverables | Completion Criteria |
|---|---|---|---|---|
| M1 | Scope and Requirements Baseline | 6 November 2026 | Problem statement, objectives, MVP scope and exclusions, functional and non-functional requirements, open-decision list. | Team has reviewed the documented scope and requirements; unresolved decisions are recorded for supervisor review. |
| M2 | Research and User Needs Review | 20 November 2026 | Existing-systems comparison, literature review, available user-research notes and summarized needs, design implications. | Sources and findings are documented, and limitations or unvalidated assumptions are identified. |
| M3 | User Flows and UI Requirements | 27 November 2026 | Main user flows, screen list, UI requirements, loading/empty/error/success states, responsive and accessibility considerations. | Flows cover registration/interests, group discovery, event viewing, RSVP, and event creation and have been reviewed by the team. |
| M4 | Clickable UI Prototype Reviewed | 11 December 2026 | Clickable Figma prototype for agreed journeys, reusable interface patterns, review feedback where available. | The team can demonstrate the agreed journeys and record feedback and unresolved design questions. |
| M5 | Core MVP Implementation | 15 January 2027 | Agreed frontend/backend features, required database/API integration, group and event flows in a development environment. | Agreed core flows can be demonstrated; incomplete or blocked features are explicitly documented. |
| M6 | Integration, Testing, and Delivery Readiness | 29 January 2027 | Integration and regression test results, defect list and fixes, updated documentation, demonstration checklist. | Critical agreed journeys pass team tests, remaining known issues are documented, and the team is ready for supervisor review or demonstration. |

**Approval rule:** Dates remain **Pending supervisor approval** until the supervisor confirms or changes them. If the official academic deadline differs from 29 January 2027, revise the proposed dates before approval.

## 6. Dependencies and Tracking

Proposed sequence: **M1 → M2 → M3 → M4 → M5 → M6**. Implementation and testing may overlap where requirements are stable; changes to scope may affect later milestones.

Track each milestone in YouTrack with an owner, proposed target date, status, dependencies, and links to deliverables. Suggested statuses are Not Started, In Progress, Blocked, and Completed. Mark a milestone completed only when its deliverables and completion criteria have been reviewed; record actual completion dates separately from target dates.

Create or update YouTrack records for the risks in Section 3, including risk ID, owner, probability, impact, mitigation, and current status. **This document does not itself update YouTrack; that action remains pending.**

## 7. Assumptions Requiring Confirmation

- Final MVP scope and official project completion deadline.
- Whether event capacity limits and waitlists are part of the MVP.
- Privacy expectations for public profiles, event venues, and organizer information.
- Recommendation baseline and how relevance will be evaluated.
- Final milestone dates and any overlap between activities.
- Whether moderation, reporting, or additional offline-safety features are in scope.

The proposed schedule assumes a late-January 2027 delivery-readiness target. If this conflicts with the academic schedule, the team should revise it before supervisor approval.

## 8. Conclusion

The risk register covers recommendation cold-start, API/frontend integration, RSVP capacity, privacy and offline safety, schedule constraints, requirements, usability, and testing. Each risk has a probability, impact, mitigation measure, and one named owner. Milestones M1–M6 define deliverables from scope and research through design, prototyping, MVP implementation, and integration testing. The team should maintain this plan, reflect the main risks and milestones in YouTrack, and obtain supervisor approval for the proposed dates.

## 9. IBS-5 Acceptance Criteria Check

| Acceptance Criterion | Evidence | Status |
|---|---|---|
| Risks cover cold-start recommendations, API/frontend mismatch, RSVP capacity errors, privacy/offline safety, and schedule constraints. | R1–R5 in Section 3 | Documented |
| Each risk has probability, impact, mitigation, and one named owner. | Section 3 | Documented; team should confirm ownership |
| Milestones M1–M6 have clear deliverables. | Section 5 | Documented |
| Dates are approved or explicitly pending approval. | Section 5 | Proposed dates marked **Pending supervisor approval** |
| `docs/project-management.md` is created. | Save this content at `docs/project-management.md` | Verify in repository |
| Main milestones and risks are reflected in YouTrack. | Section 6 | Pending manual update in YouTrack |
