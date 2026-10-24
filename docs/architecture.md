# System Architecture

**Project:** Interest-Based Social Platform (platform for interest-based group matching and offline social activities)

## 1. Diagram Files

All diagrams are stored in the `diagrams/` folder. Each diagram has an editable source file (Mermaid, `.mmd`) and readable exports (`.svg`, `.png`) in `diagrams/exports/`. Sources can be edited in any text editor and previewed at https://mermaid.live.

| Diagram | Editable source | Exports |
| --- | --- | --- |
| System Context Diagram | `diagrams/system-context.mmd` | `diagrams/exports/system-context.svg`, `.png` |
| Use Case Diagram | `diagrams/use-case.mmd` | `diagrams/exports/use-case.svg`, `.png` |
| Component Diagram | `diagrams/component.mmd` | `diagrams/exports/component.svg`, `.png` |
| Entity-Relationship Diagram | `diagrams/er-diagram.mmd` | `diagrams/exports/er-diagram.svg`, `.png` |

To re-export after editing a source file (requires Node.js):

```
npx -p @mermaid-js/mermaid-cli mmdc -i diagrams/component.mmd -o diagrams/exports/component.svg
```

## 2. System Context Diagram

![System Context Diagram](../diagrams/exports/system-context.png)

External actors: Visitor, Registered User, Event Organizer (a Registered User), and System Maintainer. All use the web application, which exchanges data with its own REST API, which persists records in PostgreSQL. An external notification provider is outside the MVP scope and is shown only as a dashed boundary.

## 3. Use Case Diagram

![Use Case Diagram](../diagrams/exports/use-case.png)

| Actor | Allowed use cases |
| --- | --- |
| Visitor | View publicly visible groups and events; register (FR-01); log in (FR-02) |
| Registered User | Log in/out; edit profile (FR-03); select interests (FR-04); browse groups (FR-05); view recommendations (FR-06, FR-11); view event information (FR-07); join/leave events (FR-09); view own registrations (FR-10) |
| Event Organizer | All Registered User actions; create/update own events (FR-08); view RSVP count |
| System Maintainer | Manage system configuration and operational logs (not part of the public UI) |

## 4. Component Diagram

![Component Diagram](../diagrams/exports/component.png)

| Component | Responsibility | Related requirements |
| --- | --- | --- |
| React + TypeScript web client | Six screens: Sign up / Log in, Profile, Interest Selection, Group Discovery, Events Listing, Event Detail / RSVP; responsive layout | NFR-03, NFR-07 |
| Auth service | Registration, login, JWT issuing and verification, Argon2 password hashing | FR-01, FR-02, NFR-01 |
| Profile / Interests service | Profile editing, interest tag selection | FR-03, FR-04 |
| Group recommendation service | Ranks groups by TF-IDF vectors of tags and descriptions with cosine similarity (Jaccard as baseline); returns scores and shared tags | FR-05, FR-06, FR-11 |
| Event / RSVP service | Event CRUD for organizers, join/leave, capacity enforcement | FR-07 to FR-10, NFR-05 |
| Data-access layer | SQLAlchemy models and queries | all |
| PostgreSQL | Persistent storage; Alembic manages schema migrations | all |

Security decisions: access tokens are verified on each protected endpoint; authorization rules prevent a user from changing another organizer's event; secrets are provided through environment variables and never committed to Git (NFR-01, NFR-02).

## 5. Initial Data Model (Entity-Relationship Model)

![Entity-Relationship Diagram](../diagrams/exports/er-diagram.png)

### 5.1 Tables

**users**

| Column | Type | Constraints |
| --- | --- | --- |
| id | integer | PK |
| email | string | unique, not null |
| password_hash | string | not null (Argon2 hash, never plain text) |
| display_name | string | not null |

**interests**

| Column | Type | Constraints |
| --- | --- | --- |
| id | integer | PK |
| name | string | unique, not null |

**user_interests** (link table, many-to-many between users and interests)

| Column | Type | Constraints |
| --- | --- | --- |
| user_id | integer | PK, FK to users.id |
| interest_id | integer | PK, FK to interests.id |

**groups**

| Column | Type | Constraints |
| --- | --- | --- |
| id | integer | PK |
| title | string | not null |
| description | string | |
| owner_id | integer | FK to users.id |

**group_interests** (link table, many-to-many between groups and interests)

| Column | Type | Constraints |
| --- | --- | --- |
| group_id | integer | PK, FK to groups.id |
| interest_id | integer | PK, FK to interests.id |

**events**

| Column | Type | Constraints |
| --- | --- | --- |
| id | integer | PK |
| group_id | integer | FK to groups.id |
| organizer_id | integer | FK to users.id |
| title | string | not null |
| start_at | datetime | not null |
| location | string | not null |
| capacity | integer | not null, greater than 0 |

**rsvps**

| Column | Type | Constraints |
| --- | --- | --- |
| user_id | integer | PK, FK to users.id |
| event_id | integer | PK, FK to events.id |
| status | string | not null (for example joined / cancelled) |
| created_at | datetime | not null |

### 5.2 Relationships

- A user selects many interests, and an interest is chosen by many users (via `user_interests`).
- A group is tagged with many interests, and an interest describes many groups (via `group_interests`).
- A user owns many groups; each group has one owner.
- A group hosts many events; each event belongs to one group.
- A user organizes many events; each event has one organizer.
- A user registers for many events, and an event has many registrations (via `rsvps`). The composite primary key (`user_id`, `event_id`) enforces one RSVP per user per event.

### 5.3 Integrity rules

- Table names `users` and `groups` are plural because `user` and `group` are reserved words in SQL.
- The number of RSVPs with status "joined" for an event must not exceed `events.capacity`. This is enforced in a database transaction in the Event / RSVP service (NFR-05).
- The link tables use composite primary keys, so duplicate selections are rejected by the database.

## 6. Consistency with Requirements and Technology Stack

| Check | Result |
| --- | --- |
| Every Must requirement (FR-01 to FR-09) maps to a use case and a component | Yes, see Sections 3 and 4 |
| Data model covers users, interests, groups, events, and RSVP registrations | Yes, see Section 5 |
| Layers match the selected stack (React, FastAPI, SQLAlchemy/Alembic, PostgreSQL) | Yes, see Section 4 |
| Recommendation component matches the chosen approach (TF-IDF + cosine, Jaccard baseline) | Yes |
| Security requirements (NFR-01, NFR-02) reflected | Yes, in Auth service and security decisions |

## 7. Status and Limitations

- These are initial design diagrams. They should be reviewed with the team and may change during implementation.
- Column types and constraints are a first draft. Final definitions will be fixed in the first Alembic migration.
- Optional fields (for example event description, user bio, group creation date) and the reporting workflow (FR-12, Could priority) are not modeled yet.
