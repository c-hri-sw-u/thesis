## 5.1 Methodological Framework

**Research through Design.** The central methodological question is what design requirements emerge when a new input modality—egocentric perception—meets an existing agent memory architecture. No prior system has attempted this integration, so there is no established design to validate or benchmark against. **The appropriate method must support exploratory iteration rather than confirmatory evaluation**. Methods that presuppose a stable design (controlled experiments, benchmarking) or simulate the system without building it (Wizard-of-Oz) cannot resolve the open design decisions identified in Chapter 4—capture interval, batch window size, prompt wording, nightly summarization, proactive surfacing. Research through Design (RtD) treats iterative building and deployment as the knowledge-generating activity itself *(Research through Design as a Method for Interaction Design Research in HCI (Zimmerman et al., 2007))*, making it the appropriate framework for a study where the design variables outnumber the settled decisions.

**Autoethnography.**RtD requires sustained deployment. The question is who deploys. Autoethnography—extended self-study by the designer-researcher—is selected for two reasons. Methodologically, the designer's intimate knowledge of the system enables diagnostic depth that external participants cannot provide: tracing a personalization failure to a specific pipeline stage rather than merely reporting that the agent's response was unhelpful (Autobiographical Design (Neustaedter & Sengers, 2012)). For a study whose primary contribution is design requirements (RQ3), this depth is essential. Practically, the system is a research prototype requiring daily pipeline monitoring, and always-on egocentric capture raises ethical and logistical barriers that exceed the scope of a master's thesis.

**Triple role and bias mitigation**.The researcher serves simultaneously as designer, participant, and analyst. **This triple role carries real bias risks**—most notably, the temptation to design structured probes that favor successful outcomes, or to unconsciously adjust daily routines to suit the pipeline's strengths. **Three mechanisms constrain this bias**: the perception log is produced automatically by the pipeline, independent of researcher judgment; interaction transcripts are recorded in full, not selectively recalled; and Phase 0 calibration is separated from Phase 1 observation, so that pipeline tuning does not contaminate the data collection period (see Section 5.2). These mechanisms reduce but do not eliminate subjectivity; the remaining limitations—single-subject generalizability, routine bias, interpretive self-reliance—are discussed in Section 7.3.

## 5.2 Study Design

The study has two phases: a calibration period preceding the formal study, followed by a two-week observation period.

\[**Table 1: Study phases**\]

|  | Phase 0: Calibration | Phase 1: Observation |
|---|---|---|
| Duration | Pre-study (approx. 1 week) | 2 weeks |
| System state | Active iteration | All parameters frozen |
| Purpose | Stabilize pipeline; resolve open design variables | Collect data for RQ1, RQ2, RQ3 |
| Output | Iteration log (→ RQ3) | All data sources (→ RQ1, RQ2, RQ3) |

**Phase 0: Calibration.** The perception pipeline runs with active iteration permitted. Every modification is logged with its rationale and before/after output comparison. This phase produces no data for RQ1 or RQ2, but the iteration log is a primary data source for RQ3: design requirements are extracted directly from the record of what failed and what was revised. The following design variables are resolved during calibration:

\[**Table 2: Phase 0 design variables**\]

| Variable | Range | Resolution criterion |
| --- | --- | --- |
| Capture interval | 3s / 5s / 8s | Balances frame redundancy against information loss |
| Batch window max | 5 / 10 / 15 min | Produces coherent scene-level summaries |
| VLM prompt wording | Iterative | Outputs personalization-relevant descriptions, not generic scene captions |
| Similarity threshold | Continuous | Deduplication removes redundant frames without discarding scene transitions |
| Nightly summarization prompt | Iterative | Day-level summary captures longitudinal patterns absent from per-batch output |
| Proactive cron frequency | Hourly / every 4h / twice daily | Generates sufficient decision points without overwhelming the researcher |

**Phase 1: Observation (2 weeks).** All pipeline parameters are frozen. The system runs continuously during waking hours, writing physical-world observations into OpenClaw's memory through the hybrid integration strategy described in Section 4.5. Three observation methods operate in parallel.

- **Passive observation.** The researcher uses OpenClaw for daily tasks—scheduling, writing, planning, information lookup—without steering conversations toward physical-world topics.
  - *Protocol:* After each interaction, tag in the journal whether the agent's response referenced physical-world memory, and if so, whether the reference improved the response. No intervention is made to increase or decrease the likelihood of physical context surfacing.
  - *Example:* Asking the agent to draft a weekly plan; observing whether it accounts for the morning runs the pipeline logged.
- **Structured probes.** Once or twice daily, the researcher reviews the perception log, selects an entry where the pipeline captured information that could plausibly aid a task, and poses a request where that information is relevant but not explicitly mentioned.
  - *Protocol:* (1) Select a perception log entry. (2) Design a request that an agent with only digital traces would answer generically, but an agent with physical-world memory could answer specifically. (3) Pose the request to the agent. (4) Log the chain: perception entry → probe wording → agent response → whether physical-world memory surfaced. This is not a blind evaluation; the audit trail ensures traceability.
  - *Example:* Perception log shows the researcher worked from a café three afternoons this week. Probe: "suggest a workspace for this afternoon." An agent without physical-world memory defaults to generic suggestions; an agent with it references the café pattern.
- **Proactive cron.** A scheduled job triggers OpenClaw at a fixed interval (set during Phase 0) to review recent physical-world memory entries and decide whether to proactively contact the researcher.
  - *Protocol:* The agent either sends a message or decides not to act; both outcomes are logged with the agent's stated reasoning. The researcher does not influence the trigger or the decision.
  - *Example:* Cron fires after the pipeline logs four hours of stationary desk work. The agent decides whether to suggest a break based on prior movement patterns.

\[**Table 3: Observation methods compared**\]

|  | Passive observation | Structured probes | Proactive cron |
| --- | --- | --- | --- |
| Tests | Does physical-world memory surface organically? | Can the agent use physical context when the opportunity arises? | Can the agent judge when to act on physical context unprompted? |
| Isolates | Baseline utilization under natural conditions | "No opportunity to use" vs. "had information but failed to use" | Agent's autonomous judgment about when physical context warrants action |
| Frequency | All interactions during study period | 1–2 probes per day | Fixed interval (set in Phase 0) |
| Researcher intervention | None | Non-blind; audit trail logged | None |

These three methods are complementary lenses on the same deployment, not independent conditions; their combined output feeds the analysis described in Section 5.4.

## 5.3 Data Collection

The study produces two categories of data: automated records generated by the pipeline and agent independent of researcher judgment, and researcher-produced records that capture structured observations and reflections.

Three data sources are automated. The **perception log** stores every VLM output produced by the pipeline, unfiltered by OpenClaw's memory heuristics—the complete record of what egocentric capture made visible. **OpenClaw's retained memory**—daily logs and MEMORY.md changes—records what the agent's existing memory pipeline chose to keep from that input. Together these form a paired record: what the pipeline produced versus what the memory architecture preserved, discarded, or distorted. **Interaction transcripts** record every conversation with OpenClaw during the observation period in full, including natural interactions, structured probes, and proactive messages initiated by the cron job. Proactive messages are logged as a distinct interaction type, annotated with the agent's stated reasoning for acting or declining to act.

Two data sources are researcher-produced. The **design iteration log** from Phase 0 records every pipeline modification with its rationale and before/after output comparison, documenting the design decisions that shaped the final system configuration. The **autoethnographic journal**, maintained throughout Phase 0 and Phase 1, documents daily reflections across four dimensions: interactions where physical context improved agent responses, missed opportunities where relevant physical information existed in memory but did not surface, cases where physical context introduced noise or irrelevance, and observations about pipeline behavior. The journal covers all interactions—passive and probe-based alike—but focuses on interpretive assessment rather than transcription, which the interaction records already provide.

\[**Table 4: Data sources**\]

| Data source | Production | Content | Collection period | Primary RQ |
|---|---|---|---|---|
| Perception log | Automated (pipeline) | All VLM outputs, unfiltered | Phase 1 | RQ1 |
| Retained memory | Automated (OpenClaw) | Daily logs + MEMORY.md changes retained by agent | Phase 1 | RQ3 |
| Interaction transcripts | Automated (OpenClaw) | All conversations: passive, probe, and proactive; annotated by type | Phase 1 | RQ2 |
| Design iteration log | Researcher-produced | Pipeline modifications with rationale and before/after comparison | Phase 0 | RQ3 |
| Autoethnographic journal | Researcher-produced | Daily reflections on physical-context utilization, missed opportunities, noise, pipeline behavior | Phase 0 + Phase 1 | RQ1, RQ2, RQ3 |

## 5.4 Analysis

Analysis proceeds in four stages, each building on the prior stage's output.

**Content classification (→ RQ1).** All perception log entries are categorized by information type through open coding—categories emerge from the data rather than a predefined taxonomy, though initial passes are guided by the broad domains summarized in Table 5. The resulting classification is compared against the digital traces available during the same period—OpenClaw's pre-existing memory entries, calendar events, and chat logs—to identify information categories that are exclusively or primarily accessible through physical-world observation.

\[**Table 5: Initial content classification domains**\]

| Domain | What it captures |
|---|---|
| Activity | What the user is doing (cooking, working, exercising) |
| Environment | Where the user is and what the space looks like (home office, café, kitchen) |
| Objects | What objects the user interacts with (groceries, books, equipment) |
| Social context | Who is present, whether conversation is occurring |
| Temporal patterns | Recurring routines that emerge over days or weeks |

**Interaction-level coding (→ RQ2).** Each interaction transcript is coded for the role physical-world information played. The initial coding scheme is summarized in Table 6; codes are iteratively refined as sub-patterns emerge during analysis. Coding is performed across all three observation methods (passive, structured probe, proactive cron), enabling comparison along two dimensions: whether the agent uses physical context spontaneously versus only when prompted, and whether proactive surfacing changes utilization patterns.

\[**Table 6: Initial interaction-level codes**\]

| Code | Definition |
|---|---|
| Useful | Physical context improved response relevance |
| Unused | Relevant physical information existed in memory but was not surfaced |
| Irrelevant | Physical context surfaced but did not help or distracted |
| Absent | Interaction type where physical context has no bearing |

**Perception log versus retained memory comparison (→ RQ3).** The paired record described in Section 5.3 is analyzed through entry-level comparison—each perception log entry is traced to determine whether OpenClaw's memory pipeline retained, discarded, or distorted it—supplemented by category-level aggregation to identify systematic patterns (e.g., whether certain information types are consistently lost). This surfaces specific failure modes: information lost at ingestion, misformatted during storage, or unretrievable at inference time.

**Thematic analysis of journal and iteration log (→ RQ3).** Recurring themes across daily reflections and Phase 0 design iterations are extracted following reflexive thematic analysis *(Thematic Analysis (Braun & Clarke, 2006))*. Codes are generated inductively from the data, grouped into candidate themes, and reviewed against the full dataset. These themes feed the design implications presented in Chapter 7.

A final cross-cutting analysis links the first two stages: the content classification from RQ1 is mapped against the interaction-level codes from RQ2 to determine whether certain information types are inherently more useful for personalization, or whether utility depends primarily on task context. Two credibility mechanisms apply throughout: the perception log, interaction transcripts, and iteration log provide a complete audit trail that makes every analytic inference traceable to source data; and negative case analysis—deliberately seeking interactions where physical context should have helped but did not, or where it introduced noise—guards against confirmatory bias.

---

These five data sources and four analytic stages collectively address the three research questions from complementary angles: content classification establishes what egocentric perception makes visible (RQ1), interaction coding determines when that information aids personalization (RQ2), and log comparison together with thematic analysis surface the design requirements for integrating physical-world sensing into agent memory architectures (RQ3). Chapter 6 reports the findings.