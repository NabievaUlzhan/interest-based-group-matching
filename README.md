# Interest-Based Group Matching and Offline Social Activities

## Project Overview

This project focuses on the development of a web platform that helps people discover communities based on shared interests and find offline social activities to participate in.

The project is motivated by the challenges people may face when entering university, moving to a new city, or trying to build new social connections.

## Problem Statement

Finding people with compatible interests and coordinating face-to-face activities can involve fragmented channels and manual communication. The proposed platform would bring interest profiles, group discovery, explainable suggestions, and event participation into one place. The extent of these difficulties and the usefulness of the proposed solution require user research and evaluation; they are not established findings in this README.

## Project Aim

To design and develop a web platform that supports interest-based group discovery and participation in offline social activities.

## Project Objectives

- Investigate the needs and challenges of potential users.
- Review existing platforms and related research.
- Define the initial functional and non-functional requirements.
- Design the platform architecture and user interface.
- Develop and test the platform based on the finalized requirements.
- Evaluate the platform using appropriate testing and user feedback.
- Develop and evaluate an interest-based group ranking mechanism.
- Integrate the frontend, API, database, and event module, including authentication and authorization controls.

## Target Users

- University students
- People who have recently moved to a new city
- People looking for communities with shared interests
- Organizers of offline social activities

## Expected Outcomes

The intended outcome is an integrated working web prototype with interest-aware group discovery, event creation and editing, and event registration (RSVP). Supporting deliverables should include requirements, architecture and UI documentation, documented tests and evaluation results, and reproducible setup instructions. These are project goals, not a claim that the application or its evaluation is complete.

## Preliminary MVP Scope

The scope below follows `docs/proposal.md` in [IBS-6 / PR #4](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/4). The proposal is **unmerged**, and its scope is **pending supervisor review**. The final scope will be determined after further research and consultation with the project supervisor.

| Proposed MVP | Excluded from the first prototype |
| --- | --- |
| Web registration, login, and profile management | Native iOS/Android applications |
| Selection and modification of personal interests | Paid ticketing and online payments |
| Group discovery and explainable interest-based ranking | Large-scale machine learning personalization |
| Offline event listing, creation, editing, and RSVP | Real-time chat and video meetings |
| Security controls and test coverage | Third-party identity verification |

The [initial architecture](docs/architecture.md) also describes group joining and event registration/cancellation as separate actions: joining a group does not register the user for an event. Organizer eligibility, private-group approval, leaving groups, waitlists, and cancellation rules still require scope decisions. Prototype examples do not establish final product policies.

## Proposed Technologies

| Component | Proposed Technology / Current Use |
|---|---|
| Frontend | React, TypeScript; Vite proposed as the build tool |
| Backend | Python, FastAPI, Pydantic |
| Database | PostgreSQL |
| Data access and migrations | SQLAlchemy, Alembic |
| Authentication | JWT and Argon2 password hashing |
| Group ranking | TF-IDF with cosine similarity; Jaccard as a baseline |
| UI/UX Design | Figma (existing design and clickable prototype linked below) |
| Testing | Pytest, Postman (proposed; no executable test suite on `main`) |
| Version Control | Git and GitHub (in use) |

The application stack is **preliminary**, documented in the [initial architecture](docs/architecture.md) and the unmerged [technology comparison / PR #5](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/5). It may be revised during requirements analysis and system design. Application dependencies and versions are not yet pinned in runnable project configuration.

## Team Members

| Team Member | Preliminary Responsibility |
|---|---|
| Arstanbek Fariza — Backend Developer | Database design, REST API, authentication, and group ranking |
| Yerzhan Syndaly (Syndaly Yerzhan) — Frontend Developer | React/TypeScript user flows, responsive views, UI/UX design, interest selection, group/event screens, and API integration |
| Nabieva Ulzhan — Full-stack Developer / QA | Event CRUD and RSVP workflow, integration, test planning, automation, and execution |

Interviews, literature analysis, diagrams, documentation, reviews, and supervisor meetings are shared responsibilities. Individual responsibilities follow the preliminary proposal and may be adjusted as the scope and requirements become clearer.

## Current Project Stage

**Stage:** Research, planning, and preliminary system/UI design; application implementation pending.

**Repository snapshot:** 24 October 2026, `origin/main` at `c2e0927` (merged [architecture PR #7](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/7)). PR status is separate from supervisor approval or implementation status.

| Status | Evidence and meaning |
| --- | --- |
| Completed and merged documentation | Existing project README, initial architecture description, and four Mermaid diagrams with SVG/PNG exports are on `main`. The design remains preliminary. |
| Existing UI design | The Figma Design and Prototype links below open the existing UX file. It demonstrates preset fictional flows, not live authentication, persistent data, a working recommendation engine, or real event registration. |
| Reviewed, open, and unmerged | Existing-systems comparison (#1), user flows (#2), proposal (#4), technology comparison (#5), prototype documentation/exports (#8), and interview documentation (#9) have approving GitHub reviews but are not on this `main` snapshot. See the documentation index. |
| In review and unmerged | Risks and milestones are in PR #6, with review comments to resolve. Proposed dates still require supervisor approval. The evaluation plan is in open PR #10, with test execution pending implementation. |
| Branch draft, unmerged | Requirements exist on `IBS-3-requirements`, with no PR found at this review. The exact path is indexed below. |
| Proposed / not implemented | Frontend, backend, database migrations, recommendation implementation, executable tests, deployment, and measured evaluation results are not present on `main`. |

Interview documentation remains a review artifact; this README does not independently verify interview records or claim validated research findings, usability results, or improved social outcomes.

## Project Documentation

### Directory Overview

| Location | Purpose and availability in this `main` snapshot |
| --- | --- |
| [docs/](docs/) | Exists; currently contains [architecture.md](docs/architecture.md). Other documents are listed separately as unmerged work below. |
| [diagrams/](diagrams/) | Exists; editable Mermaid sources and [SVG/PNG exports](diagrams/exports/) for system context, use cases, components, and the initial ER model. |
| `prototype/` | Not on `main`; UX documentation and 17 screen exports are submitted in [PR #8](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/8). |
| `tests/` | Not on `main`; intended location for future executable tests. No test results are available here. |

### Available on Main

- [System architecture and initial data model](docs/architecture.md)

| Diagram | Editable source | Readable exports |
| --- | --- | --- |
| System context | [Mermaid](diagrams/system-context.mmd) | [SVG](diagrams/exports/system-context.svg), [PNG](diagrams/exports/system-context.png) |
| Use cases | [Mermaid](diagrams/use-case.mmd) | [SVG](diagrams/exports/use-case.svg), [PNG](diagrams/exports/use-case.png) |
| Components | [Mermaid](diagrams/component.mmd) | [SVG](diagrams/exports/component.svg), [PNG](diagrams/exports/component.png) |
| Entity relationships | [Mermaid](diagrams/er-diagram.mmd) | [SVG](diagrams/exports/er-diagram.svg), [PNG](diagrams/exports/er-diagram.png) |

### Unmerged Documentation Index

These links open actual branch files or PRs. They do not imply that the files exist on `main`, that the scope is approved, or that planned work has been implemented.

| Document | Location outside `main` | Review status at this snapshot |
| --- | --- | --- |
| Project proposal and MVP scope | [docs/proposal.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-6-project-proposal/docs/proposal.md) | [PR #4](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/4): approved GitHub review, unmerged; supervisor scope review pending |
| Existing-systems comparison | [docs/existing-systems.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-10-existing-systems/docs/existing-systems.md) | [PR #1](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/1): approved GitHub review, unmerged |
| User flows and UI requirements | [docs/user-flows.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-13-user-flows/docs/user-flows.md) | [PR #2](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/2): approved GitHub reviews, unmerged; preliminary flows |
| Technology comparison | [docs/technology-comparison.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-7-technology-comparison/docs/technology-comparison.md) | [PR #5](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/5): approved GitHub review, unmerged |
| Risks and milestones | [docs/project-management.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-5-project-risks/docs/project-management.md) | [PR #6](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/6): review comments outstanding, unmerged |
| User interviews | [docs/interviews.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-1-user-interviews/docs/interviews.md) | [PR #9](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/9): approved GitHub review, unmerged; original interview records require verification |
| Functional and non-functional requirements | [docs/requieremenrs.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-3-requirements/docs/requieremenrs.md) | Branch draft on `IBS-3-requirements`; filename spelling is as stored; no PR found |
| Verification and evaluation plan | [docs/evaluation-plan.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-4-evaluation-plan/docs/evaluation-plan.md) | [PR #10](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/10): open, unmerged; test execution pending implementation |
| UX prototype documentation and screen exports | [prototype/README.md](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-11-figma-prototype/prototype/README.md) | [PR #8](https://github.com/NabievaUlzhan/interest-based-group-matching/pull/8): approved GitHub review, unmerged |

The architecture refers to `docs/requirements.md` and `docs/technology-comparison.md`; neither path exists on this `main` snapshot. Use the branch links above for the current drafts. No literature-review file is present on `main`.

## Figma Design and Prototype

- [Figma Design — existing editable source](https://www.figma.com/design/rZJZOEB9oiLOJdmFGq1ZS6/Interest-Based-Social-Platform-%E2%80%94-UX-Prototype)
- [Figma Prototype — start at Welcome](https://www.figma.com/proto/rZJZOEB9oiLOJdmFGq1ZS6/Interest-Based-Social-Platform-%E2%80%94-UX-Prototype?node-id=3-186&starting-point-node-id=3%3A186&scaling=scale-down&content-scaling=fixed)
- [UX documentation and walkthroughs — unmerged IBS-11 branch](https://github.com/NabievaUlzhan/interest-based-group-matching/blob/IBS-11-figma-prototype/prototype/README.md)

The file is titled **Interest-Based Social Platform — UX Prototype**, with **CommonGround** used as a working product name. Both Figma links were opened during README preparation on 24 October 2026. Access remains subject to the file owner's sharing permissions. The prototype uses fictional examples and preset screen transitions; it is a design demonstration, not a runnable application.

## Setup, Run, and Tests

There is no runnable application code, dependency manifest, or executable test suite on this `main` snapshot. **Setup, execution, and testing instructions will be added after implementation**, when the actual prerequisites, configuration, commands, and test environment can be verified. Use the documentation and Figma links above to review the current project artifacts.

## Project Management

GitHub is used for source code management, documentation, and team collaboration. YouTrack is used to manage tasks and monitor project progress.

- [GitHub repository](https://github.com/NabievaUlzhan/interest-based-group-matching)
- [GitHub pull requests](https://github.com/NabievaUlzhan/interest-based-group-matching/pulls)
- [YouTrack — Interest-Based Social Platform project issues](https://interest-based-group-matching.youtrack.cloud/issues/IBS)
- [IBS-12 — S3. Write Project README and Project Documentation Overview](https://interest-based-group-matching.youtrack.cloud/issue/IBS-12)

Task or review status does not by itself establish that a deliverable has been merged, implemented, or evaluated. Update this overview and its links when the relevant work reaches `main`.

## Academic Information

- **University:** Astana IT University
- **Program:** Software Engineering
- **Group:** SE-2424
- **Supervisor:** Alshynov Shyngys Kairatuly
