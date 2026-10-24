# Literature Review: Interest-Based Group Matching and Offline Social Activities

| Document attribute | Value |
|---|---|
| Project | Development of a Platform for Interest-Based Group Matching and Offline Social Activities |
| Task | IBS-2 / U2 — Verify publications, review available full texts, and finalize the critical analysis |
| Prepared | 24 October 2026 |
| Status | Final draft for team and supervisor review; all 14 sources are open access |

## 1. Scope, source selection, and verification approach

This review examines research relevant to recommending interest-based groups and offline activities, modeling group preferences, handling cold start, fairness, and evaluation.

**Source selection.** The review began with the 12 publications in the project's pre-defense draft. Each record was checked for open access, because every source cited here must be downloadable as a PDF without a subscription. Four of the twelve are open access and are retained: Hong and Ibrahim (2024), Klimashevskaia et al. (2024), Sun, Cautis and Maniu (2023), and Tran, Felfernig and Le (2024). The other eight could not be confirmed as open access and were excluded: Jiang et al. (2023), Leng and Yu (2022), Jia and Chen (2022), Mukta et al. (2024), Alves et al. (2024), Anand and Maurya (2024), the DASIIE study (2022, whose reference lacked authors), and Wang et al. (2022, SEAGR). Ten open-access sources were added to cover event-based social networks (EBSNs), reciprocal matching, social recommendation, cold start, fairness, and evaluation. The selection is therefore not a new systematic search; it is the draft's open-access subset, extended to fill gaps that the draft left uncovered.

**Verification.** For each source, the title, authors, year, venue, and DOI or arXiv identifier were checked against the publisher, repository, or scholarly-index record, and the abstract was read. Where a detail could not be confirmed on a record (a volume, issue, or page range), it is omitted from the reference or marked in Section 7. The abstracts and records were reviewed for this draft; the full texts are linked in Section 6 and still need to be read by the team before claims are finalized (see Section 8).

**Central distinction.** The review separates **group-to-item recommendation** from **person-to-group matching**. Group-to-item recommendation assumes a group of people already exists and ranks items (films, books, events) likely to satisfy that group. Person-to-group matching recommends an existing community or group to an individual based on declared interests and practical constraints. Because most of the literature addresses the first task, reported results cannot be transferred directly to the second.

## 2. Critical synthesis

### 2.1 Group recommendation: what is already known

Group recommenders are well studied. Tran, Felfernig and Le (2024) give an overview of consensus models for group decision-making and group recommender systems, which address how to aggregate the possibly conflicting preferences of group members into one recommendation. Sun, Cautis and Maniu (2023) extend the objective of group recommendation beyond preference relevance to social influence, optimizing how far a recommendation may spread through a social network. Hong and Ibrahim (2024) apply noise-based graph contrastive learning to group recommendation, an example of the neural approaches that dominate recent work.

All three assume a fixed group of users and select items for it. They clarify trade-offs (majority versus minority preferences, relevance versus influence) but do not evaluate whether a new individual fits an existing group. The social-influence and graph-based methods also require social-network or interaction data (Sun, Cautis and Maniu, 2023; Hong and Ibrahim, 2024), which a new platform will not have at launch. Sharma et al. (2024) survey graph neural network (GNN) approaches to social recommendation and screened 2,151 papers to identify 84 relevant studies; their taxonomy shows how many such methods rely on user–user social ties. These methods are candidates for future work, not for the initial MVP.

### 2.2 Event-based social networks and offline activities

EBSN research is the closest to the project's setting. Wu et al. (2024) propose a multiple-features model for leisure-event recommendation that combines preferences for event content, organizers, and close friends, and trains separate weights for active and inactive users to address cold start. Liao et al. (2020) study group event recommendation on two Meetup datasets (New York and San Diego) with an attention-based model that uses organizer, venue, time, and content as context. In both studies the recommended object is an event, not a group, and both depend on historical attendance data; Liao et al. also report only about a 2–3% gain at top-5 over the strongest baseline. These results are therefore better read as evidence about useful features (organizer, venue, time, content) than as performance benchmarks.

Sánchez and Bellogín (2022) review point-of-interest recommendation based on location-based social networks. They report that geographical signals and deep learning are among the most common approaches and that the field suffers from reproducibility problems and inconsistent evaluation protocols. This supports using location as a practical filter for offline groups and treating published accuracy comparisons with caution.

### 2.3 Person-to-group matching and reciprocal recommendation

No reviewed study directly evaluates recommending existing offline interest groups to an individual from declared interests. The nearest framing is reciprocal recommendation, where a match requires acceptance from both sides. Goda, Hayashi and Saito (2024) address this in job search, noting that true match labels are very sparse and proposing to blend observed matches with predicted match probabilities. For this project, the analogy is that a good match depends on both the individual's interest and the group's activity and openness. The transfer from job search to groups is an adaptation, not an established result, and the study relies on production data from a different domain.

A person-to-group model should therefore score the compatibility between an individual's declared interests and a candidate group's interests or description, while keeping thematic similarity separate from practical suitability. Shared tags alone do not show that a group is active, accessible, welcoming, or suitable for a person's schedule or location.

For the MVP, a content-based approach is a defensible baseline. Castells and Jannach (2023) describe content-based filtering, including profiles built from TF-IDF representations, as one of the main algorithm families. Jaccard similarity, a standard measure of overlap between two sets, can compare selected interest tags; TF-IDF vectors with cosine similarity can compare textual group descriptions. Jaccard is simple and interpretable but ignores term frequency and meaning. TF-IDF weights informative terms but remains lexical and depends on the quality and length of the text. Neither measure captures social compatibility, and the two should be compared on the same candidate groups, user profiles, relevance labels, and top-k protocol.

### 2.4 Cold start, fairness, and exposure

Cold start is the defining constraint of a new platform. Zhang et al. (2025) survey cold-start recommendation and organize existing work by the external knowledge it uses: content features, graph relations, domain information, and, in recent work, world knowledge from large language models. The survey supports using content features and explicitly declared interests when no interaction history exists. It is a preprint and does not benchmark methods for a platform like this one. Wu et al. (2024) provide an EBSN-specific example of addressing cold start through event and organizer features.

On fairness, Wang et al. (2023) review more than 60 papers and summarize fairness definitions, classify fairness issues by subject, granularity, and optimization object, and present a taxonomy of methods (data-oriented, ranking, and re-ranking). Klimashevskaia et al. (2024) survey popularity bias, its measurement, and mitigation, and Castells and Jannach (2023) also treat popularity bias as a current topic. In a new platform, interaction counts will be sparse, so popularity may reflect early exposure rather than suitability, and already-visible groups could dominate the ranking and make new or niche groups hard to find. These surveys do not define fairness for a local-groups platform; that definition is a project decision.

The initial evaluation should therefore report relevance metrics together with the distribution of exposure across groups of different popularity or age, where such fields are available and appropriate to collect. The review does not prescribe demographic fairness claims without an approved, lawful, and ethically justified measurement design. Reasonable MVP safeguards are transparent reasons for each recommendation, general browsing when personalization is unavailable, and a check on whether a small number of groups dominates the top results. Any fairness metric and threshold should be chosen before testing, not after seeing results.

### 2.5 Evaluation methods and evidence limitations

Castells and Moffat (2022) review how offline evaluation methods were adapted from machine learning and information retrieval, where recommendation's properties challenge those assumptions, and discuss experimental bias and evaluating value beyond accuracy. Bauer, Zangerle and Said (2023) reviewed 57 papers on recommender evaluation published between 2017 and 2022. They found that offline experiments dominate, that Precision, nDCG, and Recall are the most common metrics, that a few datasets (mainly MovieLens and Amazon) are used widely, and that beyond-accuracy qualities are seldom assessed. Castells and Jannach (2023) note that precision and recall are rank-insensitive and are typically measured at a cutoff (P@n, Recall@n). Sánchez and Bellogín (2022) add that inconsistent protocols can hide the true performance of methods.

Together these studies show that results from movie, book, or social-media datasets cannot be compared directly with recommendations of local offline groups, and that evaluation choices must be stated explicitly. For this project, evaluation should use a held-out set of user profiles and candidate groups with relevance labels checked by participants or a documented reviewer protocol. Precision@5 measures the share of the five recommended groups judged relevant; Recall@5 measures the share of all known relevant candidate groups that appear in the top five. Both should be reported with the number of profiles, the construction of candidate sets, the definition of relevance, and the treatment of profiles with fewer than five candidates. Jaccard and TF-IDF/cosine should be compared on the same test set, with per-profile results and an aggregate summary. If relevance labels are few or subjective, that limitation should be reported alongside qualitative feedback.

## 3. Study comparison matrix

| Study | Contribution reported by the source | Relevance to this project | Limitations for transfer | Evidence checked |
|---|---|---|---|---|
| Tran, Felfernig and Le (2024) | Overview of consensus models for group decision-making and group recommender systems. | Conceptual basis for preference conflict and aggregation. | Concerns recommendations for a fixed group, not matching a person to a group. | Metadata and open-access status confirmed via scholarly index; abstract read. |
| Sun, Cautis and Maniu (2023) | Group recommendation that maximizes social influence alongside preference relevance. | Shows that objectives may include social diffusion, not only fit. | Requires a social network; optimizes spread of information, not offline participation. | Publisher page and metadata confirmed; PDF link verified. |
| Hong and Ibrahim (2024) | Noise-based graph contrastive learning for group recommendation. | Recent neural approach to compare against simpler baselines. | High complexity and data requirements; benchmark results may not transfer. | Open-access journal record confirmed (DOAJ); DOI and article number from the project draft. |
| Sharma et al. (2024) | Systematic survey of GNN-based social recommender systems (84 studies from 2,151 screened). | Maps social-tie-based methods and datasets; locates what needs social data. | Broad survey, not a test on local group matching. | arXiv record and abstract read; DOI 10.1145/3661821. |
| Wu et al. (2024), MFM | Leisure-event recommendation using content, organizer, and friend features, with separate models for active and inactive users. | Offline events in an EBSN with explicit cold-start handling. | Recommends events, not groups; uses friend features; gains are relative to the authors' baselines. | Publisher page (MDPI) and abstract read. |
| Liao et al. (2020), ACGER | Attention-based group event recommendation on Meetup (New York, San Diego), using organizer, venue, time, and content context. | Meetup groups and events; supports organizer/venue/time as features. | Preprint (venue not stated on the page); about 2–3% gain over best baseline at top-5; needs historical event data. | arXiv record and abstract/method read. |
| Sánchez and Bellogín (2022) | Survey of POI recommendation on location-based social networks, with attention to evaluation. | Location as a signal; cautions about reproducibility. | POIs are places, not groups. | arXiv record and abstract read; DOI 10.1145/3510409. |
| Goda, Hayashi and Saito (2024) | Reciprocal recommendation for job search that combines match labels with predicted probabilities. | Two-sided match framing for person–group suitability. | Different domain; production data; preprint venue not stated. | arXiv record and abstract read. |
| Zhang et al. (2025) | Survey of cold-start recommendation organized by external knowledge used, including LLMs. | Supports content features and declared interests under cold start. | Preprint; no benchmark for this setting; LLM methods may exceed MVP scope. | arXiv record and abstract read. |
| Klimashevskaia et al. (2024) | Survey of popularity bias, measurement, and mitigation. | Supports checking exposure of less popular groups. | Application-independent; fairness must be defined for this setting. | arXiv record confirmed; bibliographic details from the project draft. |
| Wang et al. (2023) | Survey of fairness in recommender systems (60+ papers): definitions, issue classification, method taxonomy. | Vocabulary and metrics for exposure and fairness design. | Mostly computational; no local-group case. | arXiv record and abstract read. |
| Castells and Jannach (2023) | Primer on recommender systems, including content-based filtering with TF-IDF, P@n/Recall@n, and popularity bias. | Supports the baseline method and metrics. | General overview; book chapter preprint. | arXiv text read for the cited topics. |
| Castells and Moffat (2022) | Review of offline recommender evaluation: design choices, bias, and value beyond accuracy. | Supports the evaluation protocol. | General, not specific to groups. | Publisher page and abstract read; volume and pages to confirm. |
| Bauer, Zangerle and Said (2023) | Literature review of 57 evaluation studies (2017–2022): experiment types, datasets, metrics. | Shows common metrics and gaps (beyond-accuracy rarely assessed). | Reviews practice, not a method. | Repository PDF located; abstract read. |

## 4. Group-to-item recommendation versus person-to-group matching

| Aspect | Group-to-item recommendation | Person-to-group matching (this project) |
|---|---|---|
| Starting point | A group already exists. | An individual with declared interests; groups already exist. |
| Object ranked | Items or events for the group. | Existing groups or communities for the person. |
| Key difficulty | Aggregating or balancing members' preferences. | Fit of the person to the group, and practical suitability (activity, location, schedule). |
| Typical data | Group–item interactions, social ties. | Declared interest tags, group descriptions, event metadata. |
| Representative sources | Tran et al. (2024); Sun et al. (2023); Hong and Ibrahim (2024); Liao et al. (2020) | Reciprocal framing (Goda et al., 2024); content-based baseline (Castells and Jannach, 2023); cold-start support (Zhang et al., 2025) |

## 5. Research gap and implications for design

The gap is not that group recommendation is unexplored. The reviewed work mostly recommends items or events to existing groups, recommends events in EBSNs, or uses social graphs. In this set, no study evaluates a small cold-start web platform that recommends existing offline groups to an individual from explicit interest tags and practical event information.

The resulting design decisions are provisional:

1. Start from declared interests and group metadata rather than inferred profiles or social graphs (Zhang et al., 2025; Sharma et al., 2024).
2. Use a content-based baseline and compare Jaccard similarity with TF-IDF and cosine similarity on identical candidates and relevance labels (Castells and Jannach, 2023).
3. Report Precision@5 and Recall@5 with the sample and labeling conditions, and do not claim a method is better until the comparison is run (Bauer et al., 2023; Castells and Moffat, 2022).
4. Include group activity, organizer, venue, and time as metadata (Liao et al., 2020; Wu et al., 2024).
5. Inspect exposure by group popularity or age where appropriate data exists (Wang et al., 2023; Klimashevskaia et al., 2024).
6. Preserve non-personalized group browsing when recommendations cannot be produced.
7. Treat shared-interest similarity as one signal, not proof of social compatibility, safety, activity quality, or willingness to attend.

## 6. References

Every source below is open access. The link after each entry is the PDF or the open-access page from which the PDF can be downloaded.

1. Bauer, C., Zangerle, E. and Said, A. (2023) ‘Exploring the Landscape of Recommender Systems Evaluation: Practices and Perspectives’, *ACM Transactions on Recommender Systems*. https://doi.org/10.1145/3629170. PDF: https://dbis.uibk.ac.at/sites/default/files/2024-03/bauer-tors-2023.pdf
2. Castells, P. and Jannach, D. (2023) ‘Recommender Systems: A Primer’, preprint of a chapter in Baeza-Yates, R. and Alonso, O. (eds) *Advanced Topics for Information Retrieval*. ACM Press. arXiv:2302.02579. PDF: https://arxiv.org/pdf/2302.02579
3. Castells, P. and Moffat, A. (2022) ‘Offline Recommender System Evaluation: Challenges and New Directions’, *AI Magazine*. https://doi.org/10.1002/aaai.12051. Open access page: https://ojs.aaai.org/index.php/aimagazine/article/view/21745
4. Goda, S., Hayashi, Y. and Saito, Y. (2024) ‘A Best-of-Both Approach to Improve Match Predictions and Reciprocal Recommendations for Job Search’, arXiv:2409.10992. PDF: https://arxiv.org/pdf/2409.10992
5. Hong, T. and Ibrahim, N.F. (2024) ‘Group Recommendation Fueled by Noise-Based Graph Contrastive Learning’, *Journal of King Saud University – Computer and Information Sciences*, 36(5), 102063. https://doi.org/10.1016/j.jksuci.2024.102063. Open access record: https://doaj.org/article/b7f401afa151484d96cd111340b53040
6. Klimashevskaia, A., Jannach, D., Elahi, M. and Trattner, C. (2024) ‘A Survey on Popularity Bias in Recommender Systems’, *User Modeling and User-Adapted Interaction*, 34, pp. 1777–1834. https://doi.org/10.1007/s11257-024-09406-0. PDF (arXiv version): https://arxiv.org/pdf/2308.01118
7. Liao, G., Huang, X., Xiong, N.N. and Wan, C. (2020) ‘An Intelligent Group Event Recommendation System in Social Networks’, arXiv:2006.08893. PDF: https://arxiv.org/pdf/2006.08893
8. Sánchez, P. and Bellogín, A. (2022) ‘Point-of-Interest Recommender Systems Based on Location-Based Social Networks: A Survey from an Experimental Perspective’, *ACM Computing Surveys*. https://doi.org/10.1145/3510409. PDF (arXiv version): https://arxiv.org/pdf/2106.10069
9. Sharma, K., Lee, Y.-C., Nambi, S., Salian, A., Shah, S., Kim, S.-W. and Kumar, S. (2024) ‘A Survey of Graph Neural Networks for Social Recommender Systems’, *ACM Computing Surveys*. https://doi.org/10.1145/3661821. PDF (arXiv version): https://arxiv.org/pdf/2212.04481
10. Sun, Y., Cautis, B. and Maniu, S. (2023) ‘Social Influence-Maximizing Group Recommendation’, *Proceedings of the International AAAI Conference on Web and Social Media*, 17(1), pp. 820–831. https://doi.org/10.1609/icwsm.v17i1.22191. PDF: https://ojs.aaai.org/index.php/ICWSM/article/view/22191/21970
11. Tran, T.N.T., Felfernig, A. and Le, V.M. (2024) ‘An Overview of Consensus Models for Group Decision-Making and Group Recommender Systems’, *User Modeling and User-Adapted Interaction*, 34(3), pp. 489–547. https://doi.org/10.1007/s11257-023-09380-z. PDF: https://link.springer.com/content/pdf/10.1007/s11257-023-09380-z.pdf
12. Wang, Y., Ma, W., Zhang, M., Liu, Y. and Ma, S. (2023) ‘A Survey on the Fairness of Recommender Systems’, *ACM Transactions on Information Systems*. https://doi.org/10.1145/3547333. PDF (arXiv version): https://arxiv.org/pdf/2206.03761
13. Wu, Y., Peng, X., Niu, Y. and Gui, Z. (2024) ‘MFM: A Multiple-Features Model for Leisure Event Recommendation in Geotagged Social Networks’, *Electronics*, 13(1), 112. https://doi.org/10.3390/electronics13010112. PDF: https://www.mdpi.com/2079-9292/13/1/112/pdf
14. Zhang, W., Bei, Y., Yang, L., Zou, H.P., Zhou, P., Liu, A., Li, Y., Chen, H., Wang, J., Wang, Y., Huang, F., Zhou, S., Bu, J., Lin, A., Caverlee, J., Karray, F., King, I. and Yu, P.S. (2025) ‘Cold-Start Recommendation towards the Era of Large Language Models (LLMs): A Comprehensive Survey and Roadmap’, arXiv:2501.01945. PDF: https://arxiv.org/pdf/2501.01945

## 7. Limitations of this review and open verification items

- **Not a new systematic search.** The set is the open-access subset of the draft plus targeted additions.
- **Full texts.** Records and abstracts were reviewed for this draft; the full texts have not been read end to end. The team should read them (links in Section 6) before the claims are treated as final.
- **Preprints.** Zhang et al. (2025), Goda et al. (2024), Liao et al. (2020) and Castells and Jannach (2023) are preprints whose final publication venues were not confirmed on the repository pages. For the journal articles cited with an arXiv PDF (Klimashevskaia et al.; Sánchez and Bellogín; Sharma et al.; Wang et al.), the PDF is the author's arXiv version, which may differ in layout and page numbers from the published version; cite the published version's DOI.
- **Details still to confirm on the publisher page** (omitted from the references because they were not visible on the records checked): the volume and pages for Bauer et al. (2023), Castells and Moffat (2022), Sánchez and Bellogín (2022), Sharma et al. (2024) and Wang et al. (2023); the DOI of Hong and Ibrahim (2024) was taken from the project draft and the DOAJ record did not display it; the bibliographic details of Klimashevskaia et al. (2024) also come from the project draft. The authors of Castells and Moffat (2022) were not displayed on the AAAI page checked and are listed from the bibliographic record in the project's scholarly index.
- **Publication dates.** 13 of 14 sources date from 2022–2025. Liao et al. (2020) is included as a Meetup-based group-event example.
- **No experiment.** No recommendation experiment has been performed for this project, and no empirical result is claimed here.

## 8. IBS-2 acceptance-criteria checklist

| Acceptance criterion | Status in this draft | Remaining action |
|---|---|---|
| At least 12 meaningfully used sources, at least 8 scientific | 14 sources, all discussed in Section 2 and tabulated in Section 3; 13 are peer-reviewed or survey publications and the rest are preprints of surveys or chapters. | Team and supervisor review. |
| Authors, titles, years, DOIs and bibliographic details checked | Authors, titles, years and DOI or arXiv identifier checked for all 14; unconfirmed volumes and pages are listed in Section 7. | Fill the listed items from the publisher pages. |
| Structured table with contribution, relevance, limitations | Section 3. | Update after full texts are read. |
| Difference between group-to-item recommendation and matching people or groups by interests | Sections 1, 2.1, 2.3 and 4. | Complete. |
| Claims supported by reviewed sources | Every claim in Sections 2 and 5 is attributed to a source; design decisions are marked provisional. | Full-text reading by the team (Section 7). |
| `docs/literature-review.md` with a consistent reference list | This file, with a Harvard-style reference list and PDF links. | Copy into the repository, check the diff, commit, and update YouTrack. |
| Verify the 12 publications in the draft | Done for open access; 4 retained and 8 excluded because open access could not be confirmed (Section 1). | Tell the supervisor about the replacements. |
