# User Interviews

## 1. Research Purpose

The purpose of the interviews is to explore how university students meet new people, discover communities, and participate in offline activities based on shared interests. The findings are intended to help identify user needs and inform the requirements for the proposed platform, which aims to connect students with compatible groups and support the organization of offline social activities.

The interviews focus on students' experiences of meeting people, difficulties finding individuals with similar interests, methods of discovering activities, barriers to participation, and suggestions for improving the process.

## 2. Interview Methodology

The study uses a semi-structured interview format based on five core questions:

1. How did you meet new people when you first started university?
2. Did you experience any difficulties finding friends or people with similar interests?
3. How do you usually find groups, communities, or offline activities?
4. Can you describe a situation when you wanted to join an activity but could not find suitable people?
5. What would make it easier for you to meet people with similar interests and join offline activities?

Four anonymous participant labels (P1–P4) are used to protect privacy. Participant descriptions contain only general information relevant to the research.

The interview summaries should reflect the participants' actual responses. Dates, participant types, and reported experiences must be checked against the original interview notes. Responses may be paraphrased, provided that their original meaning is preserved.

The analysis distinguishes between recurring observations, individual experiences, and proposed design recommendations.

## 3. Interview Summaries

### P1 — First-Year Student

**Date:** 18 October 2026

The participant described meeting people through classes and group assignments. Although these situations provided opportunities to make acquaintances, finding people with similar hobbies remained a challenge. Information about social activities was encountered through different communication channels, making relevant announcements easy to miss.

The participant's experience concerning a gaming event illustrates a potential difficulty in finding companions with similar interests. A centralized activity listing and interest-based group discovery could help users find relevant activities and potential participants.

**Potential design implication:** Interest-based discovery and centralized activity information.

### P2 — Student Interested in Technology

**Date:** 18 October 2026

The participant described meeting people through laboratory classes and academic projects. Finding potential collaborators with similar interests, experience levels, and schedules could be challenging. Information about communities and activities was obtained through messaging platforms, social networks, and personal contacts.

The participant's experience with finding people to prepare for a programming event illustrates the practical difficulties of coordinating individuals with similar goals. In addition to shared interests, potential participants may need compatible schedules and a clear understanding of a group's purpose.

**Potential design implication:** Interest-based group filters, group creation, and clear information about planned activities.

### P3 — Student Interested in Social Activities

**Date:** 21 October 2026

The participant's experience highlighted the uncertainty that can arise when joining activities involving unfamiliar people. Although lectures and university activities provided opportunities to meet others, participating in activities outside an established social circle could be more difficult.

The example of a board-game evening illustrates a potential barrier: a student may be interested in an activity but feel uncertain about attending without friends or knowing the other participants.

**Potential design implication:** Clear event descriptions and accessible information about groups and their activities.

### P4 — Student Interested in Sports and Creative Activities

**Date:** 21 October 2026

The participant described meeting people through classes and shared activities. Finding individuals with similar interests was not always sufficient, as their schedules also needed to match. Information about activities was obtained through friends, social media, and university announcements.

The participant described an interest in attending a board-game evening but found it difficult to gather enough people who were interested and available at the same time. This experience illustrates the challenge of coordinating participants for offline social activities.

**Potential design implication:** Event listings with clear dates, times, and locations, together with functionality for creating activities and finding participants.

## 4. Cross-Interview Analysis

The interview records can be compared to distinguish needs that recur across participants from experiences specific to individuals. The table below summarizes the themes identified in the prepared interview summaries and their potential implications for the platform. These themes must be confirmed against the actual interview records before being reported as empirical findings.

| Theme | Participants to compare | Potential design implication |
|---|---|---|
| Finding people with shared interests | P1, P2, P4 | Interest-based group discovery |
| Discovering activities through different channels | P1, P2, P4 | Centralized activity listings |
| Coordinating schedules and availability | P2, P4 | Clear event dates, times, and locations |
| Feeling comfortable joining unfamiliar groups | P3 | Detailed group and event descriptions |
| Finding enough participants for an activity | P2, P4 | Group and event creation functionality |

The participant assignments in this table are provisional and should be checked against the original interview notes.

### 4.1. Recurring Needs

The comparison should establish whether participants share difficulties in discovering relevant activities, finding people with similar interests, coordinating schedules, or joining unfamiliar groups.

If these themes are supported by the actual responses, they may indicate the following user needs:

1. **Interest-based discovery:** finding groups related to personal interests.
2. **Relevant recommendations:** receiving suggestions for potentially suitable groups.
3. **Centralized activity information:** discovering relevant activities without relying exclusively on multiple communication channels.
4. **Clear event information:** understanding an event's purpose, time, location, and participation conditions.
5. **Activity organization:** creating events and managing participation.

These needs have different levels of evidential support depending on the interview records. Proposed features should not automatically be treated as verified user requirements. Their status must be determined by reviewing the actual responses.

### 4.2. Individual Experiences and Disagreements

Individual experiences should be distinguished from observations shared by several participants. For example, uncertainty about joining an unfamiliar group may be specific to one participant, whereas difficulties coordinating schedules may be reported by multiple participants.

The prepared summaries describe different barriers: P1 focuses on discovering activities and finding companions, P2 emphasizes finding collaborators with compatible goals and schedules, P3 highlights uncertainty about joining unfamiliar social groups, and P4 focuses on coordinating participants for an activity.

These differences are not necessarily disagreements. A disagreement should be recorded only when participants express conflicting preferences or views about the same issue.

The available summaries do not establish whether any actual disagreements occurred. The original responses should therefore be compared before drawing conclusions about conflicting preferences. If no disagreements were identified, this should be reported explicitly.

## 5. Mapping User Needs to Functional Requirements

The following mapping uses the functional requirement IDs from the project's requirements specification. It identifies existing requirements that may address the needs explored in the interviews. The mapping itself does not prove that a need has been validated by participants.

| Potential user need | Related requirement | Proposed verification method |
|---|---|---|
| Find groups related to personal interests | **FR-05 — Browse interest groups** | Verify that users can browse groups and identify those matching their selected interests. |
| Receive relevant group suggestions | **FR-06 — Recommend groups** | Test whether recommendations are generated based on saved user interests. |
| Understand an event before joining | **FR-07 — View event information** | Verify that event information includes the required time, location, capacity, and organizer details. |
| Organize an offline activity | **FR-08 — Create/update own event** | Verify that an authorized organizer can create or update their own event. |
| Join or leave an activity | **FR-09 — Join/leave an event** | Verify that participation status updates correctly and event capacity is not exceeded. |
| Review planned participation | **FR-10 — View my registrations** | Verify that users can view their registrations for upcoming events. |

### 5.1. Evidence Status

The interview findings and design recommendations should be classified as follows:

- **Verified by interviews:** supported by actual participant responses.
- **Recurring observation:** independently reported by multiple participants.
- **Individual observation:** reported by one participant.
- **Assumption:** proposed by the research team but not yet supported by sufficient evidence.
- **Design recommendation:** a proposed solution derived from the analysis.

A requirement may be relevant to the project even if no participant explicitly requested it. In such cases, its justification should be documented separately, for example through project objectives, technical considerations, or the literature review.

The final mapping should identify which requirements are supported by interview evidence and which remain assumptions or design decisions.

## 6. Limitations

The study is exploratory and focuses on a small number of university students. Four participants, if confirmed, cannot represent the experiences of the entire student population.

The reliability of the findings depends on the accuracy and completeness of the interview records. Dates, participant descriptions, and reported experiences must correspond to the actual data collected. Summaries written in the researcher's own words are acceptable when they preserve the participants' intended meaning.

Recurring observations must be distinguished from individual experiences. A problem reported by one participant should not be presented as a general student need without additional evidence.

Similarly, assumptions and proposed features must not be presented as verified findings. The available summaries do not independently establish whether disagreements occurred or whether every proposed feature is necessary.

These limitations should be considered when interpreting the results and translating them into functional requirements.

## 7. Conclusion

The interviews explore how university students meet people with similar interests, discover offline activities, coordinate schedules, and participate in social groups. The analysis considers both recurring challenges and individual experiences that may affect students' willingness or ability to join activities.

The findings can inform the evaluation of existing functional requirements, including group discovery (FR-05), group recommendations (FR-06), event information (FR-07), event creation (FR-08), event participation (FR-09), and registration management (FR-10).

The final conclusions must be based on the actual responses collected from participants. Recurring needs should be reported only when supported by multiple interviews, while individual experiences should remain attributed to the relevant anonymous participant. Proposed platform features should be treated as design recommendations unless the collected evidence supports them as validated user needs.