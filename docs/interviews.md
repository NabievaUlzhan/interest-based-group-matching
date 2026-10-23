# User Interviews

## 1 Research Objectives
The primary objective of this qualitative investigation is to examine how university students establish interpersonal connections, discover specialized communities, and engage in offline, interest-driven activities. By identifying key user pain points and behavioral patterns, the empirical insights gathered through these interviews serve to establish baseline functional requirements for the proposed system, titled *Development of a Platform for Interest-Based Group Matching and Offline Social Activities*.

The qualitative inquiry focuses on five core thematic areas:
* Academic and social onboarding experiences when entering university;
* Impediments to identifying peers with aligned personal or professional interests;
* Existing practices and channels used to discover communities and localized events;
* Perceived barriers to active participation in group activities;
* Desired functionality and feature sets capable of facilitating interest-based matching and event organization.

## 2 Methodology and Data Collection
This study adopts a short semi-structured interview protocol. A standardized set of five open-ended core questions was administered across all participants to ensure methodological consistency, while allowing room for follow-up prompts to clarify nuanced responses.

**Interview Protocol Questions:**
1. *How did you establish your initial social network upon starting university?*
2. *What specific challenges, if any, did you encounter when searching for peers with similar interests?*
3. *Through what channels or tools do you currently discover student groups, communities, or offline activities?*
4. *Could you describe an instance where you intended to join an activity but were unable to find suitable co-participants?*
5. *Which features or solutions would most effectively assist you in connecting with like-minded peers and attending offline events?*

* **Target Cohort:** Currently enrolled university students seeking to broaden their social networks, join interest-based groups, or participate in physical offline events.
* **Format:** Brief semi-structured qualitative interviews.
* **Ethical Considerations & Privacy:** To preserve anonymity, participants are designated using standardized identifiers ($P_1$–$P_4$). All personal identifiable information (PII), contact data, and extraneous metadata have been excluded.
* **Data Status Note:** *The four response profiles documented herein represent provisional reference models (illustrative prototypes). These profiles must be validated against or replaced by empirical qualitative data collected from live interviewees prior to final thesis submission.*

---

## 3 Interview Records and Qualitative Insights

### Interview $P_1$ — First-Year Student
* **Participant Profile:** First-year university undergraduate.
* **Interview Date:** 21.10.2026
* **Key Findings:**
  * Initial socialization relied primarily on compulsory course cohorts and group projects.
  * Encountered friction when searching for niche hobby groups, as standard academic peer groups rarely shared similar personal interests.
  * Information regarding social events remained highly fragmented, leading to missed opportunities due to scattered communication channels.
  * Expressed explicit difficulty in organizing peer groups for specialized activities (e.g., gaming events).
  * Highlighted a need for centralized, interest-driven recommendations and automated activity alerts.
* **Identified Core Problem:** High search costs and fragmented communication hinder students from finding peers who share specific non-academic interests and possess matching availability.

### Interview $P_2$ — Technology Focus
* **Participant Profile:** University student with a focus on technology and engineering.
* **Interview Date:** 21.10.2026
* **Key Findings:**
  * Social connections formed primarily within structured laboratory environments and academic coursework.
  * Main challenges involved identifying collaborators with compatible skill levels, specific technical domains, and aligning busy academic schedules.
  * Current discovery relies on informal platforms (e.g., Telegram, Discord and mainstream social media).
  * Reported difficulty sourcing appropriate teammates for extra-curricular technical endeavors (e.g., hackathons and collaborative coding sessions).
  * Recommended granular interest filters and structured group creation workflows.
* **Identified Core Problem:** Existing informal communication channels lack structured filtering mechanisms based on expertise, shared goals, and schedule alignment.

### Interview $P_3$ — Social Orientation
* **Participant Profile:** University student actively seeking to expand their social circle.
* **Interview Date:** 18.10.2026
* **Key Findings:**
  * Socialization occurred predominantly during institutional orientation events and large lecture settings.
  * Identified psychological discomfort and social friction when initiating contact with unfamiliar peers.
  * Evaluated event announcements as insufficient regarding event culture and participant demographics.
  * Recounted a scenario of wanting to attend an off-campus board game event but hesitating due to uncertainty regarding the participant group.
  * Emphasized the necessity of detailed event previews, explicit group descriptions, and participant visibility.
* **Identified Core Problem:** Social anxiety and information asymmetry concerning event environments and co-participants disincentivize students from attending offline gatherings.

### Interview $P_4$ — Recreational and Creative Focus
* **Participant Profile:** University student focused on athletic and creative pursuits.
* **Interview Date:** 18.10.2026
* **Key Findings:**
  * Social circle expansion primarily occurred through academic coursework and extracurricular clubs.
  * Logistics served as a major bottleneck; aligning schedules and finding specific skill-level matches for active sports presented continuous challenges.
  * Relying on Telegram Groups and general social media proved inefficient for spontaneous activity planning.
  * Described an instance of attempting to organize a weekend badminton session but failing to secure the minimum required participants.
  * Suggested an integrated platform incorporating activity scheduling, participant management, and event hosting capabilities.
* **Identified Core Problem:** Operational difficulties in coordinating time slots and gathering the requisite number of participants complicate the hosting of informal offline activities.

---

## 4 Cross-Interview Analysis

The synthesized qualitative data reveals several recurring thematic patterns. These initial indicators offer strategic guidance for system architecture, though they remain subject to empirical verification.

| Theme / Observed Pattern | Empirical Source | Systemic Implication |
| :--- | :--- | :--- |
| **High Friction in Peer Discovery** | $P_1$, $P_2$, $P_4$ | Implement algorithmic interest matching and discovery feeds. |
| **Information Fragmentation** | $P_1$, $P_2$, $P_4$ | Centralize group directories and offline event listings into a unified portal. |
| **Schedule & Logistics Mismatch** | $P_2$, $P_4$ | Embed temporal scheduling details and capacity trackers directly into event listings. |
| **Participation Hesitation** | $P_3$ | Provide transparent activity descriptions, safety guidelines, and participant overviews. |
| **Ad-Hoc Activity Hosting** | $P_2$, $P_4$ | Provide user-facing creation workflows for both long-term groups and single events. |

### Recurring User Needs
Synthesizing the participant profiles yields five fundamental user requirements:
1. **Targeted Interest Discovery:** Mechanisms that allow users to query and filter peers or groups by specific shared interests.
2. **Centralized Activity Hub:** A consolidated interface mitigating information fragmentation across disparate messaging platforms.
3. **Transparent Event Context:** Comprehensive metadata regarding activity scope, schedules, locations, and participant expectations prior to commitment.
4. **Self-Service Event Management:** Tools enabling individual users to initiate, configure, and manage custom groups or ad-hoc activities.
5. **Low-Friction RSVP Mechanisms:** Streamlined workflows for users to express intent, join activities, and track event status effortlessly.

### Profile Divergence Analysis
While recurring needs exist, participant motivations diverge based on personal priorities:
* $P_1$ emphasizes information visibility and content delivery.
* $P_2$ prioritizes skill-level alignment and technical project compatibility.
* $P_3$ underscores psychological comfort, group dynamics, and trust factors.
* $P_4$ focuses on operational logistics, scheduling, and quorum fulfillment.

This divergence demonstrates that the platform must support dual workflows: passive discovery of established communities and active hosting of ad-hoc offline events.

---

## 5 Functional Requirements Traceability Matrix

The preliminary user needs identified above map directly to the system functional requirements detailed in `docs/requirements.md`.

| Identified User Need | Traceable Requirement ID | Verification / Acceptance Criterion |
| :--- | :--- | :--- |
| **Interest-Based Discovery** | `FR-04` (Group Discovery) | Verify that the search engine successfully filters groups based on selected user interest tags. |
| **Personalized Recommendations** | `FR-05` (Recommendation Engine) | Validate that the recommendation module generates accurate suggestions derived from profile interests. |
| **Comprehensive Event Context** | `FR-08` (Event Detail View) | Ensure the event module displays mandatory metadata fields (e.g., date, time, location, description). |
| **User Event Generation** | `FR-06` / `FR-07` (Group/Event Creation) | Confirm that authenticated users can create, configure, and publish dynamic groups or standalone events. |
| **Participation Workflows** | `FR-09` (RSVP System) | Test that users can join, alter status, or leave an event with real-time updates to participant lists. |

---

## 6 Research Limitations
To maintain academic rigor, several methodological limitations of the current dataset must be noted:
* **Illustrative Nature of Data:** The presented records serve as synthetic reference models intended to guide system modeling; they do not constitute validated empirical data.
* **Temporal and Metadata Gaps:** Exact dates, durations, and formal consent logs remain pending real-world field administration.
* **Sample Scope:** The small sample size ($N=4$) limits statistical generalizability across the broader university demographic.
* **Response Heterogeneity:** Varied personal socio-economic backgrounds and social preferences may introduce subjective bias.

Future empirical phases must execute formal interviews, log precise timestamps, anonymize real respondents strictly, and systematically differentiate between validated behavioral trends and individual anecdotes.

---

## 7 Conclusion
The preliminary analysis demonstrates that university students encounter notable operational, informational, and social barriers when attempting to organize offline activities and identify peers with similar interests. These qualitative insights establish a strong justification for key platform capabilities—specifically, centralized activity feeds, interest-based recommendation algorithms, transparent event details, and native event management features. Final confirmation of these design priorities will follow the completion of live participant data collection.