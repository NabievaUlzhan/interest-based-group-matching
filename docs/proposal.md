# Project Proposal: Interest-Based Social Platform

* **Project title:** Development of a Platform for Interest-Based Group Matching and Offline Social Activities
* **University:** Astana IT University, School of Software Engineering, group SE-2424
* **Supervisor:** Alshynov Shyngys Kairatuly
* **Team:** Arstanbek Fariza (Backend), Yerzhan Syndaly (Frontend), Nabieva Ulzhan (Full-stack / QA)

---

## 1. Problem Statement
Finding people with compatible interests and coordinating face-to-face activities often involves fragmented channels and manual communication. The proposed system consolidates interest profiles, group discovery, relevant recommendations, and event participation in one place.

The extent of this problem among intended users will be assessed through 3-5 user interviews.

## 2. Target Users
- University students
- Members of interest-based communities
- Individuals looking for small-group offline activities

## 3. Project Aim
To design and implement a web platform that connects users based on declared interests, suggests suitable groups, and supports organizing and joining offline activities.

## 4. Objectives
1. Elicit and prioritize user and system requirements with documented evidence.
2. Design a coherent system architecture, data model, API interfaces, and security approach.
3. Implement authentication, profiles, and interest management.
4. Develop and evaluate an interest-based group recommendation mechanism.
5. Build a responsive web interface for group discovery and event participation.
6. Implement event creation, registration, and participation tracking.
7. Integrate the frontend, API, database, and event module.
8. Test functional quality, integration, usability, and recommendation relevance.

## 5. Expected Outcomes
An integrated working web prototype with:
- Interest-aware group discovery
- Event management (create, edit, RSVP)
- Documented tests
- Reproducible setup instructions

## 6. MVP Scope

| In scope (MVP) | Out of scope (first prototype) |
| :--- | :--- |
| Web registration, login, user profiles | Native iOS/Android application |
| Interest selection and modification | Paid ticketing / online payments |
| Group discovery and explainable ranking | Large-scale machine learning personalization |
| Event listing, creation and RSVP | Real-time chat, video meetings |
| Security controls and test coverage | Third-party identity verification |

## 7. Engineering Complexity
The work spans relational data design (PostgreSQL), REST APIs, token-based authentication, ranking logic (TF-IDF + cosine similarity, Jaccard as baseline), user interface state management, and cross-component integration.

## 8. Team Allocation

| Owner | Main responsibilities |
| :--- | :--- |
| **Fariza (Backend)** | PostgreSQL data model; REST API; authentication; group ranking algorithm |
| **Syndaly (Frontend)** | React + TypeScript user flows; responsive views; interest selection; group and event screens; API integration |
| **Ulzhan (Full-stack / QA)** | Event CRUD and RSVP workflow; integration; test planning, automation and execution |
| **Joint** | Interviews, literature analysis, diagrams, documentation, GitHub reviews, supervisor meetings |

## 9. Supervisor Review Status
**Status:** Pending review. The scope exclusions above are proposed planning assumptions and have not yet been approved by the supervisor.