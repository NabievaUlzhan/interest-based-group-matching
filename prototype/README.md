# IBS-11 — Clickable Figma UX Prototype

## Purpose and status

- **Project:** Development of a Platform for Interest-Based Group Matching and Offline Social Activities.
- **Prototype name:** Interest-Based Social Platform — UX Prototype.
- **Working product name:** CommonGround.
- **Task:** [IBS-11 — Design and Build a Clickable UX Prototype in Figma](https://interest-based-group-matching.youtrack.cloud/issue/IBS-11/S2.-Design-and-Build-a-Clickable-UX-Prototype-in-Figma).
- **Documentation and exports reviewed:** 24 October 2026.

The prototype demonstrates how university students, people who recently moved to a new city, and activity organizers could discover communities and make offline plans. It supports review of navigation, information hierarchy, feedback, and the main participant and organizer journeys before application implementation.

This is a preliminary design proposal. People, groups, events, venues, addresses, and recommendation reasons are fictional examples. No interview findings, usability-study results, matching effectiveness, or real social outcomes are claimed. The project owner reports having manually tested the main clickable journeys; this is a functional walkthrough, not a user-research study.

The primary design reference is [Preliminary User Flows and UI Requirements](../docs/user-flows.md), authored on `IBS-13-user-flows` at commit `0e2a38a`. The current prototype covers its main paths and selected recovery scenarios; it does not implement every proposed state or policy in that specification.

## Open the existing prototype

- [Figma Design — editable source file](https://www.figma.com/design/rZJZOEB9oiLOJdmFGq1ZS6/Interest-Based-Social-Platform-%E2%80%94-UX-Prototype)
- [Figma Prototype — start at Welcome](https://www.figma.com/proto/rZJZOEB9oiLOJdmFGq1ZS6/Interest-Based-Social-Platform-%E2%80%94-UX-Prototype?node-id=3-186&starting-point-node-id=3%3A186&scaling=scale-down&content-scaling=fixed)
- [Reviewer launchpad — recovery scenarios](https://www.figma.com/proto/rZJZOEB9oiLOJdmFGq1ZS6/Interest-Based-Social-Platform-%E2%80%94-UX-Prototype?node-id=17-1197&scaling=scale-down&content-scaling=fixed)
- [Mobile example — group discovery](https://www.figma.com/proto/rZJZOEB9oiLOJdmFGq1ZS6/Interest-Based-Social-Platform-%E2%80%94-UX-Prototype?node-id=17-733&scaling=scale-down&content-scaling=fixed)

These links refer to the existing file `rZJZOEB9oiLOJdmFGq1ZS6`. Access follows its current Figma sharing permissions; anonymous/public access has not been verified. Reviewers may need to sign in or request access from the file owner. No sharing permissions were changed for this deliverable.

Open the Prototype link, use **Get Started**, and follow the named actions below. The forms use preset examples: click a field to open its filled variant, then submit. Submitting the empty example opens validation feedback. Restart the prototype to return to the entry point. Scroll longer organizer and mobile screens when necessary.

## Screen inventory

The `01 · Desktop journeys` page contains the eleven core screens, 39 additional desktop state frames, 13 mobile examples, and a reviewer launchpad. The `Components & guidance` page contains reusable UI elements and design foundations. The Figma source uses native editable frames, text, and component instances; the PNGs below are static review exports.

| ID | Core Figma screen | Purpose | Desktop export |
| --- | --- | --- | --- |
| S01 | Welcome | Explain the platform and open account creation, login, groups, or events. | [Welcome](screenshots/s01-welcome.png) |
| S02 | Sign Up | Show name, email, password, confirmation, validation, and account-creation flow. | [Sign Up](screenshots/s02-sign-up.png) |
| S03 | Login | Enter the preset credentials and continue to interests or an intended event. | [Login](screenshots/s03-login.png) |
| S04 | Profile & Interest Selection | Show the fictional profile, choose interests, save, or browse groups. | [Profile and interests](screenshots/s04-profile-and-interests.png) |
| S05 | Group Discovery & Recommendations | Browse/search/filter groups and show explained suggestions after saving interests. | [Group discovery](screenshots/s05-group-discovery.png) |
| S06 | Group Details | Inspect a community, join it, and open an associated activity. | [Group details](screenshots/s06-group-details.png) |
| S07 | Event Discovery | Browse offline event cards and open event details. | [Event discovery](screenshots/s07-event-discovery.png) |
| S08 | Event Details & RSVP | Review time, timezone, venue, meeting instructions, organizer, and participation. | [Event details and RSVP](screenshots/s08-event-details-and-rsvp.png) |
| S09 | My Activities | Separate participant registrations from organizer drafts and published activities. | [My Activities — empty example](screenshots/s09-my-activities.png) |
| S10 | Create Event | Prepare or edit an event, validate it, save a draft, or review it. | [Create Event](screenshots/s10-create-event.png) |
| S11 | Review & Publish Event | Review public details, return to editing, or publish the example. | [Review and publish](screenshots/s11-review-and-publish-event.png) |

Additional exported evidence:

- [S05 — saved interests and explained recommendations](screenshots/s05-recommendations-saved.png)
- [S08 — registration confirmed](screenshots/s08-registration-confirmed.png)
- [S08 — cancellation confirmation](screenshots/s08-cancel-participation-confirmation.png)
- [S08 — participation cancelled](screenshots/s08-participation-cancelled.png)
- [S09 — registered activities](screenshots/s09-registered-activities.png)
- [S08 — event published](screenshots/s08-event-published.png)

Other saved variants include filled/invalid forms, failed login, selected/unsaved interests, filtered/no matching groups, joined groups, walking/book-club details and participation states, interrupted/unknown RSVP, an unavailable event, a private saved draft, and publication failure. The reviewer launchpad provides direct entry to the principal recovery examples.

## Clickable user journeys

| Journey | Walkthrough and expected feedback |
| --- | --- |
| 1. Registration and login | **Welcome → Get Started → Sign Up → filled example → Create Account → account-created Login → filled example → Log in → Profile & Interest Selection.** Empty submission demonstrates validation instead of success. |
| 2. Preferences and discovery | **Select interests → Save preferences → Group Discovery / saved.** The example selects Board games and Outdoors, shows a saved confirmation, and explains suggestions. **Browse all groups** provides a general browsing route. |
| 3. Join a group | **Group Discovery → group card → Group Details → Join group → joined state.** The confirmation explains that membership does not register the user for an event. **Explore group events** continues to Event Discovery. |
| 4. Register for an event | **Event Discovery → event card → Event Details → Register for event → Registered.** Event date, time, timezone, physical venue, and organizer remain visible. A separate login example returns to event details for an explicit RSVP action. |
| 5. Cancel participation | **Registered event → Cancel participation → confirmation.** **Keep registration** returns to the registered state; confirming **Cancel participation** opens the cancelled state with **Not registered**. Registration can be demonstrated again. |
| 6. Inspect registered activities | **Registered event → View my activities → registered event card → registered Event Details.** Use this path to inspect the registered example; the default S09 export intentionally shows an empty state. |
| 7. Create and publish an event | **Create event → click a field for the filled example → Review event → Review & Publish → Publish event → Published → View organizer activities.** **Edit event** returns to the filled form. **Save draft** opens the private-draft activities state. Empty/incomplete submission and publication-failure recovery have dedicated variants. |

The same participant loop is demonstrated in the mobile board-game examples: discovery, no-matches recovery, group joining, event registration, registered activities, and cancellation. Walking and book-club variants have their own desktop details and RSVP states.

## Design decisions

- **Visual hierarchy:** Inter typography, prominent page headings, readable content sections, and restrained decoration emphasize the next action. A forest-green primary color (`#205C4B`), warm neutral background (`#F6F7F2`), dark text (`#19332D`), and muted supporting text (`#52635C`) provide a consistent community-oriented appearance.
- **Reusable patterns:** Buttons, form fields, interest chips, group/event cards, navigation, and feedback banners use shared components, text styles, and spacing/color variables. Repeated spacing follows an 8-pixel-based scale.
- **Separate commitments:** Group membership and event RSVP are distinct actions. Registered status expresses intention to attend; it does not verify physical attendance. Cancellation removes event participation, not group membership.
- **Explainable examples:** Saved-interest suggestions give an illustrative reason rather than claiming that a working recommendation algorithm has selected an optimal group.
- **Local offline context:** Fictional Astana activities use explicit dates, UTC+5, physical venues, and meeting information. Examples include Astana Board Game Circle, Weekend City Walkers, and Pages & Conversations.
- **Reversible decisions:** Validation retains a preset example, cancellation has a keep/confirm choice, drafts remain private in the scenario, and review precedes publication.
- **Responsive exploration:** Desktop frames are 1440 pixels wide; the main form is taller than the other core screens. Mobile examples use 390 × 844 viewports with vertical scrolling. These demonstrate layout direction rather than a complete responsive implementation.
- **Accessibility intent:** Persistent labels, descriptive actions, status text alongside color, and error guidance are included. Keyboard, assistive-technology, zoom, focus-order, and formal contrast compliance still require dedicated evaluation.

## Export provenance and review

The 17 PNG files in [screenshots/](screenshots/) were copied directly from the selected existing Figma frames using **Edit → Copy as → Copy as PNG** on 24 October 2026. No screenshots were synthesized, redrawn, replaced with placeholders, or retouched. Figma's native output is 2×: 2880 × 2200 for the 1440 × 1100 frames, and 2880 × 2840 for S10's 1440 × 1420 frame. Exports exclude editor chrome and retain the actual frame content, including existing layout imperfections.

Each PNG was opened for visual inspection and checked for a valid image, expected dimensions, descriptive filename, and distinct content. All eleven core desktop screens are represented. The six state exports provide additional recommendation, participation, and publication evidence. Static images do not demonstrate clickability; use the live prototype for interactions. Future Figma edits will not automatically update these files.

The project owner reports that the main journeys have been manually tested. The preceding browser verification also exercised the seven desktop paths, mobile board-game loop, and publication-failure retry. This deliverable preparation verified the live screen inventory, native exports, links, documentation coverage, and repository scope; it did not rerun every alternate branch or conduct a usability study.

## Known limitations

1. **Simulation:** Forms switch between preset frames. There is no live text input, authentication, server-side validation, database, recommendation engine, real membership, RSVP, draft persistence, or event publication. Interest chips demonstrate a preset Board games/Outdoors pair rather than arbitrary combinations. State is not globally synchronized across every navigation branch.
2. **Selective recovery coverage:** The saved variants illustrate important errors, confirmations, and recovery paths. They do not cover the complete loading/error/empty-state matrix, all permissions, duplicate submissions, or every network outcome proposed in `docs/user-flows.md`.
3. **Layout polish:** Mobile wordmark wrapping, some card text widths, and the activities-tab row need refinement. Some desktop form widths and date/time alignment also need polish. The exports intentionally show the current design unchanged.
4. **Incomplete mobile coverage:** Some mobile walking/book-club cards, authentication routes, and organizer actions open existing desktop variants. Separate tablet layouts and every mobile equivalent have not been completed.
5. **Unresolved product policies:** Organizer eligibility, moderation, privacy, profile visibility, password/verification rules, private-group approval, capacity/waitlists, and editing/cancelling published events remain preliminary. Group leaving is not demonstrated; the task's event “Leave” behavior is represented by **Cancel participation**.
6. **Validation and access:** Not every alternate interaction has been executed individually in presentation mode. Formal accessibility and representative-user testing remain outstanding. Figma access depends on the file owner's existing permissions.

## IBS-11 acceptance-criteria check

The following criteria were read from the linked YouTrack issue on 24 October 2026. This table records prototype/deliverable evidence and does not change YouTrack checkboxes or issue status.

| IBS-11 criterion | Evidence and review status |
| --- | --- |
| Sign-up and login screens are created. | Covered by S02 and S03, their live form variants, and the corresponding PNGs. |
| Profile and interest selection screens are created. | Covered by S04, selected/unsaved examples, and the profile/interests export. |
| Group discovery and recommendation screens are created. | Covered by S05, the saved-interest recommendation variant, group cards/details, and both S05 exports. Recommendations are illustrative. |
| Event listing and event details with Join/Leave actions are created. | Covered by S07 and S08. **Register for event** is the event join action; **Cancel participation** is the leave action. Registered, confirmation, and cancelled-state exports provide evidence. |
| The main user journey is connected through clickable navigation. | Covered by the seven walkthroughs above and the live prototype. Main-path manual testing is reported; exhaustive alternate-branch testing is not claimed. |
| A shareable Figma link and screen exports are available. | Existing Design and Prototype URLs are provided above, with 17 native PNGs. Reviewers must have the required Figma access; anonymous access is unverified. |
| The link is added to the README and UX documentation. | Links are included in the [repository README](../README.md) and this prototype README, which serves as the UX prototype documentation and links to the preliminary user-flow specification. |

The documentation and exports are prepared for review on `IBS-11-figma-prototype`. No commit, push, pull request, branch merge, issue update, or Figma design edit is part of this deliverable preparation.
