# Technology Comparison

* **Project:** Interest-Based Social Platform (platform for interest-based group matching and offline social activities)
* **Purpose:** Compare alternative technologies for the frontend, backend, database, and recommendation algorithm, and justify the proposed stack: React with TypeScript, FastAPI, PostgreSQL, and TF-IDF with cosine similarity.

---

## 1. Method

### 1.1 Decisions compared

| # | Decision | Alternatives |
| :--- | :--- | :--- |
| **D1** | Frontend framework | React + TypeScript, Vue + TypeScript, Angular |
| **D2** | Backend framework | FastAPI (Python), Django (Python), Express (Node.js) |
| **D3** | Database | PostgreSQL, MySQL, MongoDB |
| **D4** | Recommendation approach | Tag overlap (Jaccard), TF-IDF + cosine similarity, neural embeddings |

### 1.2 Comparison criteria (the same for every decision)

| ID | Criterion | Meaning for this project |
| :--- | :--- | :--- |
| **C1** | Team fit | How quickly the three-person team can become productive with it |
| **C2** | Development speed | How little boilerplate is needed to deliver the MVP |
| **C3** | Ecosystem and security | Maturity, libraries, and support for authentication and validation |
| **C4** | Maintainability | Type safety, testability, clarity of structure |
| **C5** | Fit for the data and features | How well it matches users, interests, groups, events, and RSVPs |

### 1.3 Rating scale
**High / Medium / Low** fit for the project, based on the sources in Section 7 and the team's assessment. Ratings are qualitative judgments, not benchmark results. C1 ratings reflect planned team experience and should be confirmed by the team.

---

## 2. D1: Frontend Framework

| Criterion | React + TypeScript | Vue + TypeScript | Angular |
| :--- | :--- | :--- | :--- |
| **C1 Team fit** | High (planned team experience) | Medium | Medium |
| **C2 Development speed** | High: component model, large library ecosystem | High: gentle learning curve | Medium: more configuration and concepts up front |
| **C3 Ecosystem and security** | High: very large ecosystem, many UI and form libraries | Medium to High: smaller, but mature ecosystem | High: batteries-included framework |
| **C4 Maintainability** | High with TypeScript types and reusable components | High with TypeScript | High: strong structure, but heavier |
| **C5 Fit for the project** | High: suits state-heavy views such as filters, tag selection, RSVP status | High | Medium: heavier than needed for six screens |

**Decision:** **React + TypeScript**. It matches planned team experience, offers a component model suited to reusable cards (groups, events) and interest chips, and TypeScript adds compile-time checks on data exchanged with the API. Vite is used as the build tool.

---

## 3. D2: Backend Framework

| Criterion | FastAPI | Django | Express (Node.js) |
| :--- | :--- | :--- | :--- |
| **C1 Team fit** | High: Python, backend owner's choice | Medium: Python, but a larger framework to learn | Medium: JavaScript shared with the frontend |
| **C2 Development speed** | High: validation and API docs come from type hints | High: admin panel, ORM, and auth built in | Medium: many parts are assembled by hand |
| **C3 Ecosystem and security** | Medium to High: Pydantic validation, JWT and Argon2 libraries | High: mature built-in security features | Medium to High: large npm ecosystem, security depends on chosen packages |
| **C4 Maintainability** | High: typed request and response models, automatic OpenAPI schema | High: strong conventions | Medium: structure is up to the developer |
| **C5 Fit for the project** | High: REST API and direct access to Python ML libraries (scikit-learn) | Medium: full-stack features not needed, since the frontend is React | Medium: recommendation code would need a separate service or JS libraries |

**Decision:** **FastAPI**. According to its documentation, FastAPI is built on standard Python type hints and the open standards OpenAPI and JSON Schema, so request validation and interactive API documentation (Swagger UI, ReDoc) come directly from the code. This helps frontend and backend integration, and Python makes it straightforward to run the ranking logic with scikit-learn in the same service.

---

## 4. D3: Database

| Criterion | PostgreSQL | MySQL | MongoDB |
| :--- | :--- | :--- | :--- |
| **C1 Team fit** | High: standard SQL | High: standard SQL | Medium: document model and query language |
| **C2 Development speed** | Medium to High: schema and migrations (Alembic) up front | Medium to High | High at first: flexible schema |
| **C3 Ecosystem and security** | High: mature, well documented, strong Python support | High: mature | High: mature, but different consistency approach |
| **C4 Maintainability** | High: constraints and foreign keys enforce data rules | High | Medium: integrity rules are mostly in application code |
| **C5 Fit for the project** | High: data is relational (User-Interest, Group-Interest, Event-RSVP many-to-many links, unique user + event pair) | Medium to High | Medium: relationships and uniqueness are less natural |

**Decision:** **PostgreSQL**. The platform's data is naturally relational: users, interests, groups, events, and RSVPs with many-to-many links. Foreign keys, unique constraints, and transactions help enforce rules such as one RSVP per user per event and the event capacity limit (NFR-05). SQLAlchemy and Alembic provide the data-access layer and migrations from FastAPI.

---

## 5. D4: Recommendation Approach

| Criterion | Tag overlap (Jaccard) | TF-IDF + cosine similarity | Neural embeddings |
| :--- | :--- | :--- | :--- |
| **C1 Team fit** | High: simple set math | Medium to High: scikit-learn provides a ready implementation | Low: requires ML experience |
| **C2 Development speed** | High | High | Low: model selection, training or fine-tuning |
| **C3 Ecosystem and security** | High: no external dependency | High: scikit-learn | Medium: model hosting or external API |
| **C4 Maintainability** | High: easy to test and explain | High: deterministic and testable | Low: harder to debug and explain |
| **C5 Fit for the project** | Medium: ignores how informative each tag is and the group's description text | High: works from tag and description text, needs no interaction history | Medium: needs data the new platform does not have |

**Decision:** **TF-IDF + cosine similarity**, with Jaccard as the baseline. A newly launched platform has no interaction history, so approaches based on social graphs or user behavior are not feasible at the MVP stage. TF-IDF vectors built from interest tags and group descriptions can be compared with cosine similarity, and the shared tags can be shown to users (FR-11, explainable ranking). Jaccard is the simple baseline against which TF-IDF is evaluated on labeled example pairs. Neural embeddings are a possible future extension once enough consented data exists.

---

## 6. Selected Technology Stack

| Layer | Choice | Main reason |
| :--- | :--- | :--- |
| **Frontend** | React + TypeScript (Vite) | Component model, type safety, team fit |
| **Backend** | FastAPI (Python) with Pydantic | Typed API, automatic OpenAPI docs, Python ML libraries |
| **Data access** | SQLAlchemy + Alembic | ORM and database migrations |
| **Database** | PostgreSQL | Relational integrity for users, groups, events, RSVPs |
| **Authentication** | JWT (PyJWT), Argon2 password hashing (pwdlib) | Token-based auth, strong salted hashes (NFR-01) |
| **Recommendation** | TF-IDF + cosine similarity (scikit-learn), Jaccard baseline | Works without interaction history, explainable |
| **Testing** | Pytest, Postman | Unit and API testing |
| **DevOps** | Git, GitHub Actions, Docker, Docker Compose | Version control, CI, reproducible setup |

### Overall justification
The stack is consistent: one typed API contract (OpenAPI) between React and FastAPI, a relational database matching the data model, and a Python service that can run the ranking logic. Every choice is open source, widely documented, and appropriate for the size of the MVP (six screens, a small user base).

### Limitations and risks
- Ratings in Sections 2-5 are qualitative, and the C1 ratings depend on actual team experience.
- TF-IDF on short tag lists may give limited signal. This is why the Jaccard baseline and an evaluation on labeled pairs are planned.
- Versions of all tools should be recorded in a decision log when implementation begins.

---

## 7. References

*Accessed 24 October 2026. Verify that links still work before final submission.*

1. FastAPI documentation. https://fastapi.tiangolo.com
2. Pydantic documentation. https://docs.pydantic.dev
3. React documentation. https://react.dev
4. TypeScript documentation. https://www.typescriptlang.org/docs/
5. Vue.js documentation. https://vuejs.org/guide/introduction.html
6. Angular documentation. https://angular.dev
7. Django documentation. https://docs.djangoproject.com
8. Express documentation. https://expressjs.com
9. PostgreSQL documentation. https://www.postgresql.org/docs/
10. MySQL Reference Manual. https://dev.mysql.com/doc/
11. MongoDB documentation. https://www.mongodb.com/docs/
12. SQLAlchemy documentation. https://docs.sqlalchemy.org
13. Alembic documentation. https://alembic.sqlalchemy.org
14. scikit-learn: Text feature extraction (TfidfVectorizer) and pairwise cosine similarity. https://scikit-learn.org/stable/modules/feature_extraction.html
15. OpenAPI Specification. https://spec.openapis.org/oas/latest.html