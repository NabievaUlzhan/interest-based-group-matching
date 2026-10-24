# Design Verification and Evaluation Plan

| Document attribute | Value |
|---|---|
| Project | Development of a Platform for Interest-Based Group Matching and Offline Social Activities |
| Task | U4 — Design Verification and Evaluation Plan |
| Team | Fariza — Backend Developer; Syndaly Yerzhan — Frontend Developer; Ulzhan — Full-stack Developer / QA |
| Status | Proposed plan; execution pending implementation |
| Prepared on | 24 October 2026 |

## 1. Purpose

This plan defines how the platform will be verified after implementation. It covers functional behavior, API authorization and input validation, frontend/backend integration, responsive UI behavior, and the quality of interest-based group recommendations. It aligns with the requirement IDs in `docs/requirements.md` and the proposed journeys in `docs/user-flows.md`.

## 2. Scope

Verification covers:

- Account registration, login, and logout (FR-01–FR-02).
- Profile and interest selection, saving, and editing (FR-03–FR-04).
- Group browsing, search/filtering, and recommendations (FR-05–FR-06, FR-11).
- Event details, event creation/update, registration/cancellation, and registration history (FR-07–FR-10).
- Group membership, if included in the approved MVP (FR-12).
- API authentication, authorization, validation, privacy, error handling, and state consistency.
- Integration between the frontend, API, database, and recommendation component.
- Responsive layouts and basic keyboard/accessibility behavior (NFR-06–NFR-07).
- Recommendation quality against a simple baseline.

Features not approved for the MVP — such as waitlists, private messaging, payments, attendance verification, or event moderation — must not be treated as required functionality unless the scope is updated.

## 3. Verification Approach and Test Environment

### 3.1 Test levels

1. **Unit tests:** validate isolated functions, input validation, recommendation scoring, and metric calculations.
2. **API/integration tests:** exercise HTTP endpoints against a test database, including authentication, permissions, persistence, and error responses.
3. **End-to-end tests:** complete user journeys through the browser UI and verify visible status and persisted state.
4. **Responsive and accessibility checks:** inspect core screens at defined viewport widths and test keyboard interaction.
5. **Recommendation evaluation:** compare the candidate ranking with the baseline using a fixed dataset and relevance labels collected for evaluation.
6. **Usability evaluation:** after core flows work, observe participants completing agreed tasks and record completion, errors, assistance, and feedback.

### 3.2 Environment and test data

For each run, record the application build/commit, test date, browser and version, operating system, viewport, API configuration, database version, test dataset, and tools used. Use a dedicated test environment and synthetic accounts/data; do not use real passwords or unnecessary personal information.

Seed a reproducible dataset containing:

- Valid and invalid account inputs and accounts with different roles/permissions.
- Groups with known names, descriptions, and interest tags, including groups with no matching interests.
- Events with future and past dates, complete and incomplete details, open and closed registration, and capacity cases if capacity is in scope.
- Users with no interests, one interest, several interests, and interests with no matching groups.
- Recommendation test profiles and groups with human-assigned relevance labels.

Test data must be reset or versioned between runs so results can be reproduced. Record any test excluded from a run and why.

## 4. Functional Test Cases

All cases below have status **Not run** until execution evidence is recorded. “Expected result” describes the intended behavior, not an observed result.

| Test ID | Requirement | Steps | Expected result | Status |
|---|---|---|---|---|
| TC-F01 | FR-01 Registration — valid input | 1. Open registration. 2. Enter valid values for all required fields. 3. Submit. 4. Check the account in the UI or test database. | Account creation is confirmed only after success; the account is persisted and can proceed to login according to the approved flow. | Not run |
| TC-F02 | FR-01 Registration — invalid input | 1. Submit with a required field missing. 2. Submit malformed email or mismatched passwords where applicable. | Field-specific validation is shown; invalid input is rejected and no successful account creation is reported. | Not run |
| TC-F03 | FR-02 Authentication | 1. Log in with valid credentials. 2. Access a protected page. 3. Log out. 4. Try the protected action again. 5. Repeat login with invalid credentials. | Valid login grants access; logout invalidates the authenticated session/token as designed; protected actions then require login. Invalid credentials produce a non-sensitive error. | Not run |
| TC-F04 | FR-03 Profile persistence | 1. Log in. 2. Change an editable profile field. 3. Save. 4. Reload/reopen the profile. 5. Simulate a save failure. | Successful changes persist after reload. On failure, the UI does not claim success and preserves or clearly identifies unsaved changes. | Not run |
| TC-F05 | FR-04 Interests | 1. Select multiple interests. 2. Save. 3. Reopen the profile. 4. Edit the selection and save again. 5. Simulate a failed save. | Saved interests persist and can be edited. Failed saves are not shown as successful; edits remain available for retry where possible. | Not run |
| TC-F06 | FR-05 Group browsing | 1. Seed several groups. 2. Open group discovery as a guest. 3. Open a group's details. 4. Repeat with an empty group dataset. | Available groups and summary details are displayed. Empty data produces a clear empty state, not a blank page or false error. | Not run |
| TC-F07 | FR-11 Search and filters | 1. Seed groups with known names and tags. 2. Search by a matching term. 3. Apply an interest filter. 4. Clear filters. 5. Try a query with no matches. | Results match the documented search/filter rule; clearing filters restores the full listing; no matches are distinguished from a loading/API error. | Not run |
| TC-F08 | FR-06 Recommendations — known profile | 1. Create a test user with saved interests. 2. Seed groups with overlapping and non-overlapping tags. 3. Request recommendations. 4. Compare returned order with the selected algorithm's expected ranking. | Recommendations are generated using the configured method and saved interests. Any explanation shown in the UI matches actual data. Record ranking output; do not assume the method is effective before evaluation. | Not run |
| TC-F09 | FR-06 Recommendations — no useful matches | 1. Use a profile with no interests or interests absent from the group catalogue. 2. Request recommendations. | The system shows a clear empty/no-suggestion state and still allows general group browsing. It does not fabricate recommendations. | Not run |
| TC-F10 | FR-07 Event details | 1. Seed an available event with complete details. 2. Open it from event discovery. 3. Seed or request an unavailable event. | The available event shows the fields supported by the approved schema, including date/time, location or meeting instructions, organizer, and status. An unavailable event shows a clear status. | Not run |
| TC-F11 | FR-08 Event creation/update | 1. Log in as an authorized organizer. 2. Submit a valid event. 3. Try to publish with missing required fields or an invalid/past date. 4. Try the same action as a user without organizer permission. 5. Edit an event the organizer owns. | Valid authorized submissions persist and show confirmed status. Invalid input is rejected with useful errors. Unauthorized users cannot publish or edit events they do not own/have permission to manage. | Not run |
| TC-F12 | FR-09 RSVP registration | 1. Log in as a registered user. 2. Open an event with registration open. 3. Register. 4. Refresh event details and inspect My activities. | Registration is persisted and confirmed consistently in event details and the user's registration list. Joining a group alone does not create an RSVP. | Not run |
| TC-F13 | FR-09 RSVP cancellation | 1. Register for an event. 2. Cancel participation where allowed. 3. Refresh event details and My activities. 4. Simulate a cancellation failure. | Successful cancellation updates all relevant views. On failure, the last confirmed status is retained or refreshed; the UI does not falsely show cancellation. | Not run |
| TC-F14 | FR-09 Duplicate RSVP action | 1. Submit the same registration action twice quickly or replay the request. 2. Inspect the registration record and UI status. | The system handles duplicate attempts safely: no unintended duplicate participation records, and the UI displays the actual confirmed status. | Not run |
| TC-F15 | FR-10 Registration history | 1. Register for an event. 2. Open My activities. 3. Cancel the registration if permitted. 4. Reopen the list. | Upcoming registrations are listed. After confirmed cancellation, the list and event details show consistent state according to the approved history policy. | Not run |
| TC-F16 | FR-12 Group membership, if in MVP | 1. Join an eligible group as a logged-in user. 2. Refresh group details. 3. Attempt joining as a guest. 4. Simulate join failure. | Membership is shown only after server confirmation and persists on reload. Guests are directed to login. Failure does not show membership as confirmed. | Not run |

## 5. API Security and Authorization Test Cases

API tests should call endpoints directly as well as through the UI. Exact endpoint paths and response codes must be mapped to the implemented API; the cases below specify security outcomes, not assumed routes.

| Test ID | Area | Steps | Expected result | Status |
|---|---|---|---|---|
| TC-S01 | Authentication required | Call a protected profile, interest, RSVP, or event-management endpoint without credentials. | Request is rejected with the API's documented unauthenticated response; no protected data is returned or changed. | Not run |
| TC-S02 | Role/ownership authorization | Authenticate as an ordinary user and attempt to create/edit an event or access another user's private profile/registrations. | Unauthorized operation is rejected server-side; UI hiding alone is not accepted as access control. | Not run |
| TC-S03 | Input validation | Send missing, malformed, oversized, or invalid field values to registration, profile, interest, group search, and event endpoints. | Invalid requests are rejected safely with documented validation errors; application does not crash or persist invalid state. | Not run |
| TC-S04 | Injection and query handling | Submit strings containing SQL-like syntax and unexpected characters in search and text fields. | Inputs are handled as data, not executable query fragments; no unauthorized data access or database error details are exposed. | Not run |
| TC-S05 | Sensitive data exposure | Inspect public profile/group/event responses and error messages. | Responses contain only approved fields. Passwords, password hashes, tokens, private contact data, and stack traces are not exposed. | Not run |
| TC-S06 | Session/token handling | Test missing, expired, malformed, and invalid credentials/tokens using the implemented authentication design. | Invalid credentials are rejected consistently; protected data is not returned. Token/session invalidation follows the selected design. | Not run |
| TC-S07 | RSVP capacity and concurrency, if capacity is in scope | Configure one remaining place; submit registration requests concurrently from two test users. | The server enforces capacity atomically: confirmed registrations do not exceed the limit. If capacity is not in the MVP, record this case as out of scope rather than claiming it passed. | Not run / scope-dependent |
| TC-S08 | Error handling | Trigger a controlled server/database failure and inspect the response. | Client receives a safe, useful error; internal details and secrets are not returned; the UI does not show an unconfirmed operation as successful. | Not run |

Security review should also confirm that password storage uses an appropriate password-hashing approach, secrets are not committed to the repository, and the deployment configuration does not expose development/debug settings. These checks depend on the implementation and must be documented with evidence.

## 6. Frontend–Backend Integration Test Cases

| Test ID | Integration scenario | Steps | Expected result | Status |
|---|---|---|---|---|
| TC-I01 | Contract compatibility | For each implemented core endpoint, compare request fields, response schema, validation errors, and status codes with the API contract used by the frontend. | Frontend and backend agree on field names, types, optionality, and error shapes; no feature depends on undocumented response behavior. | Not run |
| TC-I02 | Persistence after reload | Save interests, update a profile, create an event, and register for an event; reload each relevant screen. | The UI reflects persisted server state rather than only local component state. | Not run |
| TC-I03 | Loading, empty, and error states | Simulate slow responses, empty successful responses, and API errors for groups, recommendations, and events. | Loading is distinguished from empty and error states; a recommendations error does not hide successfully loaded group listings. | Not run |
| TC-I04 | Authenticated navigation | Open a protected action as a guest, log in, and return to the intended group/event. | The user returns to the intended context and must explicitly confirm Join or Register; login alone does not mutate membership or RSVP state. | Not run |
| TC-I05 | Consistent participation status | Register/cancel through the UI and compare event details, My activities, API response, and database state. | All views agree with the final confirmed server state. Unknown outcomes are refreshed rather than guessed. | Not run |
| TC-I06 | Recommendation service integration | Request suggestions for a saved-interest profile; test no interests, no matches, and recommendation-service failure. | The response is parsed correctly, suggestion reasons reflect actual saved interests, and general browsing remains available if recommendations fail. | Not run |

## 7. Responsive UI and Basic Accessibility

### 7.1 Viewport matrix

Test the core screens—landing, registration/login, profile/interests, group list/details, event list/details, My activities, and event form—at the following proposed viewport widths:

| Profile | Viewport width | Checks |
|---|---:|---|
| Small mobile | 360 px | No clipped controls or page-level horizontal scrolling; readable cards/forms; primary actions reachable. |
| Tablet | 768 px | Navigation, filters, cards, and forms reflow without overlapping; important information remains visible. |
| Desktop | 1366 px | Content remains readable and aligned; forms and lists use available width appropriately. |

Record browser/version, actual viewport dimensions, screenshots for defects, and pass/fail per screen. These are proposed test widths, not a claim of universal device coverage.

### 7.2 UI checks

- Verify navigation and return paths preserve group search/filter state where specified.
- Verify labels remain visible, form errors are associated with the relevant fields, and focus moves predictably after validation failures.
- Complete the core journeys using only a keyboard; check visible focus and that dialogs can be opened, used, and dismissed.
- Ensure RSVP, membership, loading, error, and success states are expressed in text, not color alone.
- Check that important status messages are perceivable by assistive technology where supported by the chosen framework.
- Measure color contrast against a chosen target before claiming compliance; no formal accessibility conformance is claimed by this plan.

## 8. Recommendation Evaluation

### 8.1 Methods to compare

**Baseline — Jaccard similarity.** Represent a user's interests and a group's interest tags as sets. For non-empty sets, compute:

\[
J(U,G)=\frac{|U\cap G|}{|U\cup G|}
\]

where \(U\) is the set of user interests and \(G\) is the set of group tags. A larger score means a larger proportion of shared tags relative to the union. If both sets are empty, define the score as 0 for this evaluation to avoid treating absence of information as a strong match. If either set is empty, the score is 0. Rank groups by descending score and use a documented stable tie-breaker, such as group ID, so repeated runs are reproducible.

**Candidate — TF-IDF with cosine similarity.** Build a text representation for each user profile from their saved interest labels and for each group from its interest tags and approved descriptive text. Fit TF-IDF using only the defined evaluation corpus, transform user and group text into vectors, and compute cosine similarity between each user vector and each group vector. Rank groups by descending similarity and use the same tie-breaker as the baseline. Record the corpus, preprocessing, tokenization, TF-IDF configuration, and any text fields included. Do not include private data or test-set relevance labels in ranking inputs.

The candidate method is a hypothesis to evaluate, not an assumed improvement. If the implementation uses different text fields or preprocessing, document that difference before running the comparison.

### 8.2 Relevance labels and evaluation dataset

Prepare a fixed evaluation set of user profiles and candidate groups. For each user, obtain relevance labels for candidate groups using a documented procedure—for example, a participant's explicit relevance judgment or an independently reviewed rubric based on stated interests and group descriptions. Define what counts as relevant before scoring. Keep the same users, candidate groups, relevance labels, and eligibility rules for both methods.

Separate algorithm inputs from relevance labels. Avoid using the same label as both an input feature and the ground truth. Document dataset size, how profiles/groups were selected, who assigned labels, any disagreements and resolution, and limitations. If there are too few judged relevant groups for a user, mark that user's Recall@5 as not defined for the aggregate and report the exclusion rule transparently; do not silently treat it as zero.

### 8.3 Metrics

For each evaluated user, let \(Top5(u)\) be the first five eligible groups returned by the method, and let \(Rel(u)\) be the set of groups judged relevant to that user.

**Precision@5** measures the proportion of the top five recommendations that are relevant:

\[
P@5(u)=\frac{|Top5(u)\cap Rel(u)|}{5}
\]

If fewer than five eligible groups exist, use the number actually returned as the denominator and report this convention. If no groups are returned, Precision@5 is 0 for that user and the empty result is separately counted.

**Recall@5** measures the proportion of all judged relevant eligible groups retrieved in the top five:

\[
R@5(u)=\frac{|Top5(u)\cap Rel(u)|}{|Rel(u)|}
\]

Recall@5 is undefined when \(|Rel(u)|=0\); report the number of such users and exclude them from the mean Recall@5 rather than dividing by zero. Report macro-averaged Precision@5 and Recall@5 across eligible users, alongside the number of users evaluated, the number with no relevant groups, and the per-user scores or score distribution. Use identical eligibility rules for both methods.

### 8.4 Comparison procedure

1. Freeze and describe the evaluation dataset and relevance-labeling procedure.
2. Implement and unit-test Jaccard similarity, including empty sets, identical sets, disjoint sets, and ties.
3. Implement and unit-test the TF-IDF/cosine pipeline, including empty text and deterministic ranking.
4. Run both methods over the same user profiles and candidate groups.
5. Save ranked top-five outputs, per-user metrics, macro averages, and the configuration used.
6. Compare Precision@5 and Recall@5 for the two methods. Report differences descriptively; do not claim statistical significance unless an appropriate analysis is specified and performed.
7. Inspect examples where rankings differ and note possible limitations, including sparse interests, tag quality, short text, popularity effects, and the small evaluation sample.
8. If the dataset or method changes, record a new run rather than overwriting prior results without traceability.

No recommendation scores, measured accuracy, or superiority claim is supplied in this plan. Those results must be filled in only after the methods have been implemented and the evaluation has been run.

## 9. Performance, Usability, and Reliability Measurements

| Area | Proposed measurement | Conditions to record | Result status |
|---|---|---|---|
| API performance | p50 and p95 response time for group/event list and detail endpoints; error rate | Build, environment, dataset size, concurrency, number of requests, warm-up policy, tool, and endpoint | Pending implementation and load test |
| Usability | Task completion rate without moderator assistance; errors; requests for help; qualitative feedback | Participants, recruitment, tasks, device, moderator protocol, and sample size | Pending working prototype and study |
| State consistency | Count of mismatches across API/database/UI after register, cancel, join, edit, retry, and reload scenarios | Scenario, initial state, final server state, and screenshots/logs | Pending integration tests |
| Responsive UI | Pass/fail per core screen at each viewport | Browser/version, OS, viewport, screen and defect notes | Pending implementation |
| Recommendation quality | Macro Precision@5 and Recall@5 for Jaccard and TF-IDF/cosine | Dataset, relevance labels, candidate set, configuration, user count, exclusions | Pending recommendation implementation and evaluation |
| Security | Number and severity of failed authorization, validation, privacy, and error-handling checks | Test account/role, request, expected outcome, actual response, and evidence | Pending API implementation and security tests |

The requirements document proposes a performance target of p95 ≤ 2 seconds for group/event list and detail requests at up to 20 simulated concurrent users, and a usability target of at least 80% of task attempts completed without moderator intervention. These are **proposed targets, not results**; confirm them with the team/supervisor before using them as pass/fail thresholds. Apply the same environment and conditions when comparing repeated runs.

## 10. Defect Management and Reporting

Each failed case should produce a defect record containing: test ID, build/commit, environment, reproduction steps, expected result, actual result, severity/priority, supporting logs or screenshots, owner, status, and retest outcome. Retest the failed case after a fix and run related regression tests for affected requirements.

Use these result labels consistently:

- **Not run:** no execution has taken place.
- **Pass:** observed behavior meets the expected result and evidence is recorded.
- **Fail:** observed behavior does not meet the expected result; create or link a defect.
- **Blocked:** execution cannot proceed because a dependency or environment is unavailable.
- **Out of scope:** feature is not included in the approved MVP; document the scope decision.

A test summary should report counts of pass/fail/blocked/not-run cases, open defects by severity, requirement coverage, environment, and known limitations. Recommendation results must include the dataset and metric definitions. Do not convert planned tests into passed tests or present target values as measured outcomes.

## 11. Exit Criteria

The team may recommend a verification cycle complete when:

1. All in-scope Must requirements have mapped test cases and have been executed, or exceptions are documented and approved.
2. No unresolved critical/high-severity defect blocks core account access, privacy/authorization, group discovery, event creation, or RSVP behavior.
3. API/frontend integration and persisted-state checks have been completed for core flows.
4. Responsive and basic accessibility checks have documented results at the specified viewports and journeys.
5. Recommendation evaluation has run on a documented relevance-labeled dataset, or is explicitly reported as not yet evaluated if the recommendation feature is deferred.
6. Actual results, deviations from targets, defects, and limitations are recorded without unsupported success claims.

## 12. U4 Acceptance Criteria Check

| Acceptance criterion | Evidence in this document | Status |
|---|---|---|
| Test cases cover registration, authentication, interests, recommendations, events, and RSVP. | Section 4, TC-F01–TC-F15. | Defined; execution pending |
| Each test case includes steps and an expected result. | Functional and security/integration case tables. | Defined; execution pending |
| Metrics and measurement conditions are documented. | Sections 3, 7, 8, and 9. | Defined; measurement pending implementation |
| Jaccard is the baseline and TF-IDF with cosine similarity is the candidate. | Section 8.1. | Defined; implementation/evaluation pending |
| Precision@5 and Recall@5 are specified. | Section 8.3. | Defined; evaluation pending |
| No unmeasured results are presented as completed results. | Status labels throughout; Section 10. | No test outcomes claimed |
| `docs/evaluation-plan.md` is created. | Save this file as `docs/evaluation-plan.md`. | File prepared; commit pending |
