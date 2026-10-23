# Project Risks and Milestones

| Document Attribute | Value |
|---|---|
| Project | Development of a Platform for Interest-Based Group Matching and Offline Social Activities |
| Task | IBS-5 — U5. Identify Project Risks and Define Milestones |
| Team | Fariza — Backend Developer; Syndaly Yerzhan — Frontend Developer; Ulzhan — Full-stack Developer / QA |
| Supervisor | Alshynov Shyngys Kairatuly |
| Status | Preliminary proposal for team review |
| Date | 24 October 2026 |

## 1. Introduction

This document identifies potential risks that could affect the development of the Interest-Based Group Matching and Offline Social Activities platform and defines the main project milestones.

The platform aims to help users discover groups based on shared interests, explore offline activities, create events, and participate in social activities. Successful development requires coordination between frontend and backend development, clear requirements, appropriate testing, and timely completion of project deliverables.

The risks and milestones described below are preliminary proposals. Their probability, impact, priorities, owners, and target dates should be reviewed and agreed upon by the project team and supervisor.

## 2. Project Risk Management Approach

Project risks will be identified, assessed, monitored, and addressed throughout the development process.

Each risk is evaluated using two criteria:

- **Probability:** the likelihood that the risk will occur.
- **Impact:** the potential effect on the project scope, schedule, quality, or functionality.

The following qualitative scale is proposed:

| Rating | Probability | Impact |
|---|---|---|
| Low | Unlikely to occur | Minor effect on the project |
| Medium | Could occur during development | Noticeable delays or additional work |
| High | Likely to occur or difficult to prevent | Significant delays, scope changes, or loss of essential functionality |

Risk priority is determined by considering both probability and impact. High-priority risks should receive earlier attention and be reviewed regularly.

## 3. Project Risk Register

| ID | Risk Description | Probability | Impact | Mitigation Strategy | Proposed Owner |
|---|---|---|---|---|---|
| R1 | Unclear or changing requirements may lead to rework and delays. | Medium | High | Document functional and non-functional requirements, review them with the team and supervisor, and record changes before implementation. | Full-stack Developer / QA |
| R2 | Frontend and backend integration problems may prevent features from working together correctly. | Medium | High | Agree on API contracts, request and response formats, and error handling before integration. Test endpoints and integration scenarios early. | Frontend and Backend Developers |
| R3 | Delays in individual tasks may affect the overall project schedule. | Medium | High | Break work into smaller tasks, define dependencies, track progress, and communicate blockers as early as possible. | All team members |
| R4 | Bugs and insufficient testing may reduce the reliability and usability of the platform. | Medium | High | Prepare test scenarios, perform functional and integration testing, document defects, and retest fixes before delivery. | Full-stack Developer / QA |
| R5 | The group-matching or recommendation approach may not produce relevant suggestions. | Medium | Medium | Begin with a simple baseline approach, define how relevance will be evaluated, and compare results against expected use cases before selecting a final approach. | Backend Developer and Full-stack Developer / QA |
| R6 | Users may have difficulty understanding the interface or completing important user flows. | Medium | Medium | Review user flows, validate the proposed interface with potential users, and improve navigation, feedback, and error messages based on findings. | Frontend Developer |
| R7 | Poor coordination, conflicting changes, or merge conflicts may disrupt team development. | Medium | Medium | Use separate task branches, descriptive commits, pull requests, code reviews, and regular communication about shared files and interfaces. | All team members |
| R8 | Database or application errors may cause incorrect or unavailable group, event, or participation information. | Medium | High | Validate input, handle failed requests, test important database operations, and verify that event registration and membership statuses remain consistent. | Backend Developer and Full-stack Developer / QA |
| R9 | Insufficient time for final integration and documentation may result in incomplete deliverables. | Medium | High | Reserve time for integration, regression testing, documentation review, and preparation of the final demonstration. | All team members |

These ratings are initial estimates rather than measured probabilities. The team should update them when new information becomes available.

## 4. Risk Monitoring and Response

Risk monitoring will be incorporated into regular project reviews.

The team should:

1. Review open risks when discussing task progress and blockers.
2. Update the probability and impact ratings when circumstances change.
3. Record newly identified risks and assign a responsible team member.
4. Check whether mitigation actions are completed and effective.
5. Escalate risks that threaten important milestones to the supervisor.
6. Document significant scope or schedule changes and their consequences.

If a risk occurs, the team should assess its effect on the project and agree on a corrective action. Depending on the situation, this may involve fixing a defect, changing the implementation approach, adjusting the task sequence, or revising the planned scope with supervisor approval.

## 5. Project Milestones

The following milestones represent the proposed sequence of major project activities. Exact dates and dependencies should be confirmed against the team's approved schedule.

| ID | Milestone | Main Activities | Completion Criteria |
|---|---|---|---|
| M1 | Project Scope and Requirements Defined | Define the problem, target users, project objectives, scope, and functional and non-functional requirements. | Requirements and project boundaries are documented and reviewed by the team. |
| M2 | Existing Systems and User Needs Researched | Compare existing platforms, review relevant literature, and gather feedback from potential users. | Research findings, sources, and user research documentation are available for review. |
| M3 | User Flows and UI Requirements Defined | Describe registration, interest selection, group discovery, event viewing, RSVP, and event creation flows. | User flows, interface requirements, and relevant interface states are documented. |
| M4 | UI Prototype Prepared | Develop a clickable prototype based on the documented user flows and interface requirements. | Main user journeys can be demonstrated in the prototype and reviewed by the team. |
| M5 | Core Application Features Implemented | Develop the agreed frontend, backend, database integration, group discovery, and event functionality. | The agreed core features are implemented and can be demonstrated in a development environment. |
| M6 | Integration and Testing Completed | Integrate application components, test main user journeys, identify defects, and verify fixes. | Critical user journeys pass the agreed tests, and remaining known issues are documented. |
| M7 | Final Documentation and Demonstration Prepared | Review project documentation, summarize results, prepare the demonstration, and address final feedback. | Required deliverables are reviewed, and the team is ready to demonstrate the project. |

Milestone completion should be based on the stated criteria rather than the passage of time alone.

## 6. Dependencies Between Milestones

The proposed milestone sequence is:

1. **M1 — Project Scope and Requirements Defined:** establishes the project boundaries and expected functionality.
2. **M2 — Existing Systems and User Needs Researched:** provides evidence to inform requirements and design decisions.
3. **M3 — User Flows and UI Requirements Defined:** translates the research and scope into user journeys and interface behavior.
4. **M4 — UI Prototype Prepared:** makes the proposed interaction flows available for review.
5. **M5 — Core Application Features Implemented:** develops the agreed functionality using the reviewed requirements.
6. **M6 — Integration and Testing Completed:** verifies that the application components and important user journeys work together.
7. **M7 — Final Documentation and Demonstration Prepared:** consolidates deliverables and prepares the project for final review.

Some activities may overlap. For example, testing can begin during implementation, and documentation can be updated throughout the project. Changes to requirements may affect several later milestones.

## 7. Milestone Tracking

Milestone progress should be tracked using the team's project management tool.

The following status values are proposed:

- **Not Started:** work has not begun.
- **In Progress:** activities required for the milestone are underway.
- **Blocked:** progress depends on resolving an issue or dependency.
- **Completed:** all completion criteria have been met and reviewed.

For each milestone, the team should record the planned date, actual completion date, current status, responsible person, and any blockers. Delays should be assessed for their impact on subsequent milestones.

No milestone should be marked completed solely because its tasks have been started or because a target date has passed.

## 8. Assumptions and Limitations

This document is based on the current understanding of the proposed platform and its development activities.

The following points remain subject to confirmation:

- The final project scope and approved minimum viable product (MVP).
- The exact project schedule and milestone dates.
- The final technology stack and recommendation approach.
- The availability of potential users for research and usability evaluation.
- The final testing requirements and acceptance criteria.
- The allocation of individual risk and milestone ownership.

The risk register and milestones should be revised when the approved project proposal, implementation plan, or supervisor feedback provides more precise information.

## 9. Conclusion

This document establishes a preliminary framework for identifying and managing project risks and tracking major milestones. The risk register highlights potential issues related to requirements, integration, scheduling, testing, recommendation quality, usability, collaboration, data consistency, and final delivery.

The proposed milestones provide a structured path from requirements and research to prototyping, implementation, testing, and final demonstration. Their completion criteria help the team evaluate progress using concrete deliverables.

The project team should review this document regularly, confirm milestone dates and responsibilities, and update the risk register as development progresses. This approach can help the team identify problems early, coordinate work more effectively, and improve the likelihood of delivering the agreed project scope.

## 10. IBS-5 Acceptance Criteria Verification

The following checklist is proposed for reviewing this documentation task. It should be checked against the actual IBS-5 requirements in YouTrack before the task is considered complete.

| Criterion | Evidence in This Document | Status |
|---|---|---|
| Project risks are identified and documented. | Section 3 — Project Risk Register | Documented |
| Risk probability and impact are assessed. | Sections 2–3 | Documented; ratings require team review |
| Risk mitigation strategies are defined. | Section 3 | Documented |
| Main project milestones are identified. | Section 5 — Project Milestones | Documented |
| Milestone completion criteria are defined. | Section 5 | Documented |
| Risk monitoring and milestone tracking are described. | Sections 4 and 7 | Documented |
| The documentation is committed to the project repository. | To be verified after committing the file | Pending |

