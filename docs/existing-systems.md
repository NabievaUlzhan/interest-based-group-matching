# Research and Comparison of Existing Systems

- **Project:** Development of a Platform for Interest-Based Group Matching and Offline Social Activities
- **University and programme:** Astana IT University, Software Engineering diploma project
- **Prepared for:** IBS-10 — S1. Research and Compare Existing Systems
- **Team member:** Syndaly Yerzhan — Frontend Developer
- **Stage:** Preliminary research and problem validation
- **Source verification date:** 23 October 2026

## 1. Introduction

The proposed project concerns a web platform through which people could discover groups with shared interests and participate in offline social activities. Its initial audience includes university students, particularly freshmen, and people who have recently moved to a new city. These groups are a proposed research audience; their difficulties, existing practices, and willingness to use another platform have not yet been established by this comparison.

Meetup, Discord, Bumble For Friends, and Eventbrite provide relevant reference points because they address different parts of the journey from discovering an interest to interacting with people and attending an activity. Meetup connects interest communities with events; Discord provides ongoing community communication; Bumble's friendship products connect people and groups; and Eventbrite supports event discovery and registration. Their documented capabilities are examined below. [M1] [D1] [B2] [E1] [E3]

This review informs subsequent interviews, requirements analysis, and interface exploration. It does not establish final requirements, select an architecture, or claim that the proposed platform has been implemented.

## 2. Purpose and methodology

The purpose is to identify established interaction patterns, relevant limitations, and questions that require direct investigation with potential users. Four systems are assessed against the same ten criteria. The unit of comparison is a documented native product capability, including features that depend on an organizer role or community configuration. Third-party bots, integrations, and custom workflows are outside scope.

Official product pages and help documentation were searched and read on **23 October 2026**. All 25 product references were cross-checked against the claims attributed to them, including the comparison cells and source descriptions in Section 10. Eventbrite's app and event-creation help pages were inspected in the browser because automated research retrieval could not access them. E1 now records the app article's verified destination after redirection; E3 was reopened directly and remained accessible at its existing URL. Verification means that the cited documentation was accessible and supported the stated capability on that date. No accounts were created, events booked, or authenticated product workflows tested.

Evidence is interpreted at three levels:

- **Verified capability:** explicitly described in an official source; this establishes documented support, not its quality or effectiveness.
- **Potential limitation:** an analytical implication of a documented workflow or restriction, identified as such rather than presented as a measured usability problem.
- **Research assumption:** a proposition about local users or the proposed solution that requires interviews, observation, or prototype testing.

Documentation may retain legacy instructions or describe experimental features. Bumble For Friends is therefore assessed with an explicit distinction between its legacy app and its current BFF successor. Discord's discovery restrictions are retained rather than assuming universal availability. Market availability, local community activity, recommendation quality, accessibility for disabled users, and actual attendance outcomes were not independently tested. No usage statistics or comparative performance rankings are inferred.

## 3. Overview of the four platforms

### 3.1. Meetup

Meetup documents groups and events discoverable through location and interests. Its event workflow includes a venue, description, topics, and attendance settings. [M1] [M3] For this project's preliminary scope, we interpret that combination as a directly relevant reference for connecting an ongoing interest community with an offline gathering.

### 3.2. Discord

Discord organizes communication into servers and channels, with text, voice, and video interaction. Scheduled Events can also specify a physical location. It is relevant because discovering a group is only one step: participants may also need conversation and coordination before and after an activity. [D1] [D3]

### 3.3. Bumble For Friends and its BFF successor

The legacy Bumble For Friends help center now announces closure and directs users to the new BFF app. The notice does not establish an exact worldwide shutdown date. Legacy Plans documentation describes public or private plans with a location, date, and time, invitations, and requests to join nearby public plans. These are verified descriptions of the **legacy workflow**, not proof that it remains operational everywhere. [B1] [B8]

Current BFF documentation describes profiles, interest-based People and Groups discovery, community rooms, and event creation and RSVP. The comparison column below evaluates this **documented successor**, while retaining the requested Bumble For Friends context. It does not combine legacy Plans and successor features into one product version. [B2] [B3] [B5]

BFF's availability article lists the United States, Canada, and Mexico and states that users outside those markets cannot create an account or use the app. Thus, the successor is a design reference rather than a currently available alternative for users in Kazakhstan according to the verified documentation. The operational status of legacy Bumble For Friends in Kazakhstan remains unverified. [B6]

### 3.4. Eventbrite

Eventbrite provides event browsing, ticket registration, and organizer tools for creating event listings and ticket types. It is relevant as a reference for moving from discovery to a recorded booking, including free activities, rather than assuming that every offline gathering requires paid admission. [E1] [E3]

## 4. Comparison criteria

The following definitions are applied consistently across the four systems. They describe capabilities, not satisfaction or social outcomes.

| No. | Criterion | Operational definition |
| --- | --- | --- |
| 1 | Interest-based discovery | Find people, communities, or activities using topics, interests, categories, or related search terms. |
| 2 | Group discovery | Find and inspect ongoing communities that a user could join; finding an event or following an organizer alone is only partial support. |
| 3 | Personalized recommendations | Receive discovery suggestions adapted to individual preferences or behaviour; manual filters or unspecified recommended lists establish only partial support. |
| 4 | Offline event discovery | Find activities intended to take place at a physical location; discovery limited to an existing community is partial support. |
| 5 | Event creation | Create an activity with scheduling information; role or community permissions are noted without treating organizer features as universally available to members. |
| 6 | Event registration / RSVP | Record a response or registration for a particular activity; an interest notification without confirmed registration is partial support. |
| 7 | User profiles | Maintain a personal identity or introduction within the service, rather than only an organizer listing. |
| 8 | Community interaction | Communicate with participants or organizers; following and sharing without a documented community discussion space constitute partial support. |
| 9 | Mobile accessibility | Access core participant functions through a documented mobile app or mobile web interface; this does not establish full desktop parity or accessibility compliance. |
| 10 | Support for new users | Documented guidance for first use and entry into a community or activity; procedural help or an organizer-dependent welcome alone is partial support. |

**Evaluation categories:**

- **Yes:** official evidence directly supports the defined capability, subject to stated role and availability conditions.
- **Partial:** evidence supports a narrower, indirect, or limited form of the criterion; Section 5 explains the boundary.
- **No:** official evidence explicitly establishes that the capability is unsupported in the evaluated scope.
- **Not verified:** the consulted sources do not establish whether the capability exists. Missing evidence is not treated as evidence of absence.

The labels are categorical judgments, not numerical scores. No overall winner is calculated because the systems serve different purposes.

## 5. Comparative analysis table

**Scope of the Bumble column:** current BFF successor documentation in supported markets; see Section 3.3 for the legacy product and geographic restriction. All cells refer to documentation verified on 23 October 2026.

| Comparison criterion | Meetup | Discord | Bumble For Friends / BFF successor | Eventbrite |
| --- | --- | --- | --- | --- |
| Interest-based discovery | Yes [M1] | Partial [D2] | Yes [B3] [B4] | Yes [E1] |
| Group discovery | Yes [M1] | Partial [D2] [D6] | Yes [B4] | Partial [E1] |
| Personalized recommendations | Yes [M2] | Not verified [D2] [D6] | Partial [B3] [B4] | Yes [E2] |
| Offline event discovery | Yes [M1] [M3] | Partial [D3] | Partial [B2] [B5] | Yes [E1] |
| Event creation | Yes [M3] | Yes [D3] | Yes [B5] | Yes [E3] |
| Event registration / RSVP | Yes [M6] | Partial [D3] | Yes [B5] | Yes [E1] [E3] |
| User profiles | Yes [M4] | Yes [D4] | Yes [B7] | Yes [E1] |
| Community interaction | Yes [M5] | Yes [D1] | Yes [B2] [B5] | Partial [E1] |
| Mobile accessibility | Yes [M6] | Yes [D1] [D4] | Yes [B3] [B5] [B7] | Yes [E1] |
| Support for new users | Partial [M1] [M6] [M7] | Yes [D1] [D5] | Yes [B7] [B9] | Partial [E1] [E3] |

### Interpretation of partial and uncertain evaluations

1. **Discord discovery:** the Discover Tab article describes categories and community previews but labels the feature experimental and available to only a percentage of desktop and mobile users. It also limits server search to desktop during that experiment. The separate Server Discovery article says its earlier experiment ended and directs readers to Discover. Consequently, discovery is rated Partial; neither article establishes universal access. [D2] [D6]
2. **Discord personalization:** Discover documents category and popularity ordering. The older Server Discovery article explicitly describes its former list as non-personalized, but that statement cannot establish the behaviour of every current discovery surface. Personalized recommendations are therefore Not verified. Selecting roles and channels during onboarding is a different capability from recommending new communities. [D2] [D6] [D5]
3. **Discovery within a community:** Discord can schedule an event at a physical location, and BFF documents group-based planning of offline hangouts and events. These support finding activities through communities, but the cited evidence does not establish a general city-wide offline-event catalogue for either service. Both receive Partial for offline event discovery. [D3] [B2] [B5]
4. **Discord participation:** selecting Interested informs the host and enables an event notification. This is an expression of intention; the documentation does not establish an admission reservation or ticket registration. It is rated Partial rather than equated with a confirmed booking. [D3]
5. **BFF recommendations:** Discover adjusts results according to preferences and location, and the Groups page includes recommended groups. This establishes some tailoring, but the consulted articles do not explain whether group suggestions are individually ranked beyond filters. Partial avoids assuming an adaptive matching algorithm. [B3] [B4]
6. **Eventbrite groups and interaction:** following organizers, finding friends, contacting organizers, and sharing events are documented. These provide continuity and coordination, but do not establish discovery of joinable interest communities or a persistent participant discussion space. These criteria receive Partial, not No. [E1]
7. **Support for newcomers:** Meetup provides discovery and RSVP instructions and allows an optional organizer welcome after membership approval. Eventbrite documents registration and event setup. These are useful procedural supports, but their effectiveness in helping a newcomer enter an unfamiliar social group is unverified. Discord has configurable community onboarding; BFF documents account setup and default introduction rooms. Their Yes ratings establish mechanisms, not a proven welcoming experience. [M1] [M6] [M7] [E1] [E3] [D5] [B7] [B9]
8. **Permissions and mobile scope:** event creation on Discord depends on event permissions; Meetup's documented flow starts from a group's page; BFF documents events in group rooms and calendars. Mobile Yes ratings concern participant access and do not imply that every administrative function is available on mobile. [D3] [M3] [B5] [M6] [D4] [B7] [E1]

## 6. Strengths and limitations of each system

### 6.1. Meetup

**Documented capabilities and relevance:** Meetup combines interest and location discovery, personalized event suggestions, event setup, RSVP, and group discussion. Profiles can include interests with visibility controls. [M1] [M2] [M3] [M4] [M5] [M6] We interpret this combination as relevant to the proposed discovery-to-participation journey; its suitability for the target audience remains to be evaluated.

**Documented constraints:** messaging access depends on membership, organizer status, and privacy settings; unrestricted messaging between all members should not be assumed. [M5]

**Potential limitation requiring validation:** the existence of relevant groups does not show whether their schedules, locations, or social expectations suit a particular freshman. Interviews should investigate whether students already use Meetup successfully and whether any difficulty concerns discovery, first attendance, or the supply of suitable activities. Local adoption and perceived affordability were not measured here.

### 6.2. Discord

**Documented capabilities and relevance:** topic channels and text, voice, and video communication support ongoing interaction. Community Onboarding can assign channels and roles from members' answers. [D1] [D5] These mechanisms offer design references for introducing participants to an established community; their effectiveness for the target audience is untested.

**Documented constraints:** the reviewed discovery interface has experimental availability, while events are organized within servers and participation can be expressed through Interested. These constraints distinguish community coordination from a broadly accessible local event-registration journey. [D2] [D3]

**Potential limitation requiring validation:** a newcomer might need an invitation or prior knowledge to reach a relevant local community when discovery is unavailable or the community is not listed. Whether channel structure helps or burdens AITU students must be tested; familiarity with Discord should not be assumed from their student status.

### 6.3. Bumble For Friends / BFF

**Documented capabilities and relevance:** the successor combines friendship profiles, interest and location discovery, joinable groups, chat, and events with RSVP. Group creation includes a location, topic tags, and visibility settings. [B2] [B3] [B4] [B5] [B9] These documented features show overlap with the proposed scope, without establishing suitability or successful social outcomes for local users.

**Documented constraints:** BFF is currently limited to three listed markets, excluding Kazakhstan. Its account guidance requires users to be at least 18, verify a phone number, upload photos, and complete selfie verification. These are onboarding conditions; they do not prove that offline meetings are safe. [B6] [B7]

**Potential limitation requiring validation:** the relevance of profile-led discovery, group interaction, and verification requirements to local students remains unknown. Research should establish the intended audience's age range before proposing eligibility or safeguarding requirements; this review contains no evidence about freshmen's ages. The closure notice and legacy Plans instructions do not establish migration completeness or the current operation of legacy Plans in Kazakhstan. [B1] [B8]

### 6.4. Eventbrite

**Documented capabilities and relevance:** category and location browsing, personalized app recommendations, free or paid tickets, and structured event setup are documented. [E1] [E2] [E3] We interpret them as useful references for activity discovery and participation management, subject to local user research.

**Evidence boundary:** the reviewed documentation establishes organizer and friend following and organizer contact. It does not establish a joinable interest-group discussion model. This limits what can be concluded about persistent community interaction; it is not proof that every such feature is absent. [E1]

**Potential limitation requiring validation:** registration for an activity may not address uncertainty about who will attend or how to enter an existing social circle. Conversely, event listings alone may meet students' needs. Research should test both possibilities before adding community features. No conclusion is drawn about Eventbrite's local event supply or suitability for Kazakhstan payments.

## 7. Identified gaps and user needs requiring validation

The comparison does not demonstrate a universal missing feature. Meetup already covers much of the proposed functional scope, while BFF also combines groups and activity planning in its supported markets. [M1] [M3] [M6] [B4] [B5] The more defensible research question is whether a specific local audience encounters unmet needs despite these capabilities.

The following are **research questions arising from untested hypotheses**, not findings about students or proven competitor deficiencies. No need, barrier, or demand in this table has been established by a participant study:

| Research question | Validation approach | Evidence that would affect the project scope |
| --- | --- | --- |
| Do new students experience difficulty finding active groups that fit their interests and location? | Ask freshmen and recent arrivals to reconstruct their most recent search and demonstrate their current tools. | Successful existing workflows would weaken the need for a separate discovery service; repeated failures could identify specific information gaps. |
| Which factors, if any, beyond shared interests influence participation: time, travel, cost, language, or activity experience? | Compare recent choices with rejected activities and ask participants to rank concrete alternatives. | Only repeatedly consequential factors should become candidate filters or profile fields. |
| Does uncertainty about attending alone discourage first participation? | Interview students about a real first visit, cancellation, or abandoned intention; test event-description prototypes. | Evidence could support clearer host introductions, meeting instructions, or expectations for first-time attendees. |
| Do participants want continuing group contact after an event, and how do they currently maintain it? | Interview attendees and organizers about follow-up and observe their existing communication workflow with consent. | Existing messaging tools may be sufficient; integration or a link could be preferable to building chat. |
| Do organizers encounter problems communicating attendance changes? | Walk through an organizer's recent event, including cancellations and actual attendance tracking. | Distinguish expressed interest, confirmed RSVP, waiting lists, and actual attendance before defining participation states. |
| Could a local platform attract enough active organizers and participants to sustain useful activity listings? | Map current AITU clubs and public activity channels, then discuss participation in a small pilot with organizers. | Insufficient event supply or willingness to maintain listings could invalidate the platform concept. |
| What identity, privacy, and reporting arrangements would participants expect? | Explore desired visibility of interests, contact information, and attendance; clarify the audience's age range and discuss moderation responsibilities. | Findings should shape consent, data collection, reporting, and eligibility requirements before implementation. |

Interviews should include freshmen, students who already organize or attend activities, and people who recently moved to Astana. Recruitment should include users of existing services and people who do not currently seek groups online, rather than assuming that non-use reflects a product failure. Subsequent reporting should document recruitment, sample characteristics, limitations, and contradictory evidence; this review contains no participant study or invented interview results.

## 8. Preliminary differentiation of our proposed platform

The preliminary direction is a **locally focused journey from an expressed interest to a suitable group and a clearly explained offline activity**, initially investigated with AITU students and recent arrivals. Its possible value would lie in how well that journey meets validated local needs, not in claiming invention of profiles, recommendations, groups, or RSVP.

Candidate directions to investigate include:

- **Local relevance:** make campus or nearby activity information easier to evaluate, if research shows that existing sources are fragmented or incomplete.
- **Clear first participation:** connect group information, host expectations, venue directions, and attendance status, if uncertainty is a demonstrated barrier.
- **Understandable matching:** explain a suggested group using visible shared interests and practical constraints. A transparent rule-based approach could be tested before deciding whether more complex recommendations are justified.
- **Focused mobile web experience:** test whether a browser-based path suits local participants and organizers. Competitors already provide mobile access, so mobile availability alone is not a distinguishing feature. [M6] [D4] [B7] [E1]

These are alternatives for research and prototyping, not approved functionality. For the frontend role, the immediate implication is to test the clarity of interest selection, group information, activity details, and participation feedback using low-fidelity prototypes. The team should compare these prototypes with participants' existing workflows, including the option of improving an existing club process instead of developing a separate platform.

Requirements and architecture should follow evidence and supervisor review. A decision to proceed would need both a recurring user problem and a plausible supply of organizers and activities. No uniqueness, superiority, recommendation accuracy, or improvement in social wellbeing is claimed.

## 9. Conclusion

The four systems provide complementary references: Meetup for the relationship between interests, groups, and events; Discord for ongoing community interaction; Bumble For Friends and BFF for friendship discovery and group activity; and Eventbrite for event discovery and registration. The evidence supports substantial functional overlap with the proposed project. The remaining question is whether local students need a more suitable workflow, information model, or organizing process, which requires direct research rather than a feature checklist alone.

Unresolved matters include Discord's account-specific discovery availability and personalized recommendations, BFF's recommendation logic and legacy-app operation in Kazakhstan, and whether Discord or BFF provides a general offline-event catalogue beyond the reviewed community workflows. Local adoption, event supply, usability, willingness to join another service, and the effect of any proposed design on attendance remain untested. The existence of a help article does not establish usability, and a registration does not establish actual participation.

### IBS-10 acceptance-criteria check

The following six criteria were read from the YouTrack task on 23 October 2026. Status refers to this review artifact; the issue itself has not been updated.

| Acceptance criterion from IBS-10 | Status | Evidence in this document |
| --- | --- | --- |
| Three to five relevant systems are included. | Satisfied | Four systems in Section 3; the BFF successor is distinguished within the Bumble analysis. |
| Six to ten consistent comparison criteria are defined. | Satisfied | Ten operational definitions and a common evaluation legend in Section 4. |
| Interest discovery, group discovery, event creation, and event participation features are examined where applicable. | Satisfied | Section 5 compares all four areas and explains partial support. |
| Factual claims are supported by sources and a verification date. | Satisfied | Inline source references, explicit evidence boundaries, and dated official references in Section 10. |
| docs/existing-systems.md is created. | Satisfied | This file is the requested artifact. |
| The proposed platform's differentiation is explained. | Satisfied | Section 8 presents conditional local differentiation without asserting uniqueness or implementation. |

## 10. References

The 25 product references below are official vendor documentation or product pages; T1 separately records the project task specification. **Each product reference was accessed and its relevant content verified on 23 October 2026.** This is an access date, not a claim that every article was updated that day. B1 and B8 concern the legacy app; B2–B7 and B9 concern the successor. E1 and E3 were verified through the browser; the remaining product references were read through the web research tool. The sources support the attributed feature descriptions; the comparison ratings and judgments about project relevance are the authors' interpretations, and user needs remain unvalidated.

### Meetup

- **M1.** Meetup Help Center. [What is a Meetup group?][M1] — interest and location discovery, communities, and offline gatherings.
- **M2.** Meetup Help Center. [How can I improve visibility for my events and groups?][M2] — personalized recommendations based on preferences and past activity.
- **M3.** Meetup Help Center. [Creating an event][M3] — group-based event setup, physical venues, topics, and attendance options.
- **M4.** Meetup Help Center. [How do I hide my interests?][M4] — profiles, interests, privacy controls, and documented mobile interfaces.
- **M5.** Meetup Help Center. [How do I send a message to another member?][M5] — group discussions, event comments, and messaging restrictions.
- **M6.** Meetup Help Center. [How to attend a hybrid event][M6] — RSVP, participation changes, and web/iOS/Android access.
- **M7.** Meetup Help Center. [What notifications Meetup can send][M7] — membership-approval welcome messages and organizer customization.

### Discord

- **D1.** Discord Support. [Beginner's Guide to Discord][D1] — servers, channels, communication, signup, and participant guidance.
- **D2.** Discord Support. [Discover Tab][D2] — community discovery, category ordering, experimental access, and mobile-search restrictions.
- **D3.** Discord Support. [Scheduled Events][D3] — event permissions, physical locations, and the Interested response.
- **D4.** Discord Support. [Custom Profiles][D4] — personal profile fields and mobile editing.
- **D5.** Discord Support. [Community Onboarding FAQ][D5] — configurable onboarding, roles, channels, and device/configuration boundaries.
- **D6.** Discord Support. [Server Discovery][D6] — ended experiment, former non-personalized list, and direction to Discover.

### Bumble For Friends / BFF

- **B1.** Bumble For Friends Support. [Bumble For Friends is closing down][B1] — closure notice and migration direction; article updated 8 September 2026.
- **B2.** Bumble BFF Support. [Moving from the Bumble For Friends app to BFF][B2] — successor profiles, groups, communication, and offline hangout planning.
- **B3.** Bumble BFF Support. [Using the ‘Discover’ page][B3] — People and Groups discovery and preference/location tailoring.
- **B4.** Bumble BFF Support. [Discovering and joining Groups][B4] — recommended groups and interest/activity/location searches.
- **B5.** Bumble BFF Support. [Chat Rooms][B5] — interaction and event creation, viewing, and RSVP within rooms/calendars.
- **B6.** Bumble BFF Support. [Availability of BFF][B6] — United States, Canada, and Mexico availability; article updated 9 September 2026.
- **B7.** Bumble BFF Support. [Creating an account][B7] — mobile signup, profile interests, verification steps, and minimum age.
- **B8.** Bumble For Friends Support. [How can I create a plan?][B8] — legacy public/private Plans and invitations; not used as proof of successor functionality.
- **B9.** Bumble BFF Support. [Creating a Group][B9] — group topics, location, visibility, and default introduction and discussion rooms.

### Eventbrite

- **E1.** Eventbrite Help Center. [Using the Eventbrite app][E1] — event filters, registration, profiles, organizer contact, friend following, and mobile access. The URL records the official destination reached when the earlier help link was reopened in the browser.
- **E2.** Eventbrite. [The Eventbrite App — Local Events & Things To Do][E2] — documented personalized discovery feed; recommendation effectiveness is not established.
- **E3.** Eventbrite Help Center. [Create an event][E3] — in-person venues, free/paid/donation tickets, order forms, and publishing. This exact URL was reopened directly and confirmed accessible in the browser on 23 October 2026, so it was retained. Automated research retrieval could not open the page; its claims were checked against the rendered official article.

### Task specification

- **T1.** Project YouTrack. [IBS-10 — S1. Research and Compare Existing Systems][T1] — six acceptance criteria, read in the authenticated browser on 23 October 2026. Access may require project authorization.

[M1]: https://help.meetup.com/hc/en-us/articles/39489496646925-What-is-a-Meetup-group
[M2]: https://help.meetup.com/hc/en-us/articles/39489043789325-How-can-I-improve-visibility-for-my-events-and-groups
[M3]: https://help.meetup.com/hc/en-us/articles/39790436736525-Creating-an-event
[M4]: https://help.meetup.com/hc/en-us/articles/360002866812-How-do-I-hide-my-interests
[M5]: https://help.meetup.com/hc/en-us/articles/39488807979277-How-do-I-send-a-message-to-another-member
[M6]: https://help.meetup.com/hc/en-us/articles/19318209614349-How-to-attend-a-hybrid-event
[M7]: https://help.meetup.com/hc/en-us/articles/40708711818637-What-notifications-Meetup-can-send
[D1]: https://support.discord.com/hc/en-us/articles/360045138571-Beginner-s-Guide-to-Discord
[D2]: https://support.discord.com/hc/en-us/articles/25323248535319-Discover-Tab
[D3]: https://support.discord.com/hc/en-us/articles/4409494125719-Scheduled-Events
[D4]: https://support.discord.com/hc/en-us/articles/4403147417623-Custom-Profiles
[D5]: https://support.discord.com/hc/en-us/articles/11074987197975-Community-Onboarding-FAQ
[D6]: https://support.discord.com/hc/en-us/articles/360023968311-Server-Discovery
[B1]: https://support.bumbleforfriends.com/hc/en-us/articles/38993514244637-Bumble-For-Friends-is-closing-down
[B2]: https://support.bumblebff.com/hc/en-us/articles/29706304198429-Moving-from-the-Bumble-For-Friends-app-to-BFF
[B3]: https://support.bumblebff.com/hc/en-us/articles/33949872719773-Using-the-Discover-page
[B4]: https://support.bumblebff.com/hc/en-us/articles/30291683710109-Discovering-and-joining-Groups
[B5]: https://support.bumblebff.com/hc/en-us/articles/33949439952413-Chat-Rooms
[B6]: https://support.bumblebff.com/hc/en-us/articles/37693593412637-Availability-of-BFF
[B7]: https://support.bumblebff.com/hc/en-us/articles/30291649228061-Creating-an-account
[B8]: https://support.bumbleforfriends.com/hc/en-us/articles/16704016326045-How-can-I-create-a-plan
[B9]: https://support.bumblebff.com/hc/en-us/articles/33945550399005-Creating-a-Group
[E1]: https://support.eventbrite.com/hc/en-us/articles/34823063209362-Using-the-Eventbrite-app
[E2]: https://www.eventbrite.com/consumer/eventbrite-app/
[E3]: https://support.eventbrite.com/hc/en-us/articles/34824366421522-Create-an-event
[T1]: https://interest-based-group-matching.youtrack.cloud/issue/IBS-10/S1.-Research-and-Compare-Existing-Systems
