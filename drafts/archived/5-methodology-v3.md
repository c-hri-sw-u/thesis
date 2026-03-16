## 5.1 Methodological Framework

**Research through Design.** The central methodological question is what design requirements emerge when a new input modality—egocentric perception—meets an existing agent memory architecture. No prior system has attempted this integration, so there is no established design to validate or benchmark against. **The appropriate method must support exploratory iteration rather than confirmatory evaluation**. Methods that presuppose a stable design (controlled experiments, benchmarking) or simulate the system without building it (Wizard-of-Oz) cannot resolve the open design decisions identified in Chapter 4—adaptive interval parameters, SSIM threshold, batch window size, prompt wording, nightly summarization, proactive surfacing. Research through Design (RtD) treats iterative building and deployment as the knowledge-generating activity itself *(Research through Design as a Method for Interaction Design Research in HCI (Zimmerman et al., 2007))*, making it the appropriate framework for a study where the design variables outnumber the settled decisions.

**Autoethnography.**RtD requires sustained deployment. The question is who deploys. Autoethnography—extended self-study by the designer-researcher—is selected for two reasons. Methodologically, the designer's intimate knowledge of the system enables diagnostic depth that external participants cannot provide: tracing a personalization failure to a specific pipeline stage rather than merely reporting that the agent's response was unhelpful (Autobiographical Design (Neustaedter & Sengers, 2012)). For a study whose primary contribution is design requirements (RQ3), this depth is essential. Practically, the system is a research prototype requiring daily pipeline monitoring, and always-on egocentric capture raises ethical and logistical barriers that exceed the scope of a master's thesis.

**Triple role and bias mitigation**.The researcher serves simultaneously as designer, participant, and analyst. **This triple role carries real bias risks**—most notably, the temptation to design structured probes that favor successful outcomes, or to unconsciously adjust daily routines to suit the pipeline's strengths. **Three mechanisms constrain this bias**: the perception log is produced automatically by the pipeline, independent of researcher judgment; interaction transcripts are recorded in full, not selectively recalled; and Phase 0 calibration is separated from Phase 1 observation, so that pipeline tuning does not contaminate the data collection period (see Section 5.2). These mechanisms reduce but do not eliminate subjectivity; the remaining limitations—single-subject generalizability, routine bias, interpretive self-reliance—are discussed in Section 7.3.

## 5.2 Study Design

The study has two phases: a calibration period preceding the formal study, followed by a two-week observation period.

\[**Table 1: Study phases**\]

<table style="width: 477px;">
<colgroup><col style="width: 102px;"><col style="width: 184px;"><col style="width: 191px;"></colgroup><tbody><tr><th colspan="1" rowspan="1" colwidth="102"><p></p></th><th colspan="1" rowspan="1" colwidth="184"><p>Phase 0: Calibration</p></th><th colspan="1" rowspan="1" colwidth="191"><p>Phase 1: Observation</p></th></tr><tr><th colspan="1" rowspan="1" colwidth="102"><p>Duration</p></th><td colspan="1" rowspan="1" colwidth="184"><p>Pre-study (approx. 1 week)</p></td><td colspan="1" rowspan="1" colwidth="191"><p>2 weeks</p></td></tr><tr><th colspan="1" rowspan="1" colwidth="102"><p>System state</p></th><td colspan="1" rowspan="1" colwidth="184"><p>Active iteration</p></td><td colspan="1" rowspan="1" colwidth="191"><p>All parameters frozen</p></td></tr><tr><th colspan="1" rowspan="1" colwidth="102"><p>Purpose</p></th><td colspan="1" rowspan="1" colwidth="184"><p>Stabilize pipeline; resolve open design variables</p></td><td colspan="1" rowspan="1" colwidth="191"><p>Collect data for RQ1, RQ2, RQ3</p></td></tr><tr><th colspan="1" rowspan="1" colwidth="102"><p>Output</p></th><td colspan="1" rowspan="1" colwidth="184"><p>Iteration log (→ RQ3)</p></td><td colspan="1" rowspan="1" colwidth="191"><p>All data sources (→ RQ1, RQ2, RQ3)</p></td></tr></tbody>
</table>

**Phase 0: Calibration.** The perception pipeline runs with active iteration permitted. Every modification is logged with its rationale and before/after output comparison. This phase produces no data for RQ1 or RQ2, but the iteration log is a primary data source for RQ3: design requirements are extracted directly from the record of what failed and what was revised. The following design variables are resolved during calibration:

\[**Table 2: Phase 0 design variables**\]

| Variable | Range | Resolution criterion |
| --- | --- | --- |
| Adaptive interval max_interval | 15s / 20s / 30s | Balances pattern accumulation (needs continuous low-frequency coverage) against storage and token cost |
| Adaptive interval ramp curve | e.g., 3s → 5s → 8s → 15s → 30s | Trigger-to-baseline recovery speed balances event capture density against redundancy |
| Batch window max | 10 / 15 min | Produces coherent scene-level summaries |
| SSIM threshold | Continuous | Confirms genuine scene change vs. minor angle/lighting shift; fallback: upgrade to embedding similarity |
| VLM prompt wording | Iterative | Outputs personalization-relevant descriptions, not generic scene captions |
| Importance score weights | w1(visual) / w2(audio) / w3(imu) / w4(sparsity), default 0.3/0.3/0.2/0.2 | Key frame selection prioritizes information-rich frames within each batch |
| Nightly summarization prompt | Iterative | Day-level summary captures longitudinal patterns absent from per-batch output |
| Proactive cron frequency | Hourly / every 4h / twice daily | Generates sufficient decision points without overwhelming the researcher |

**Phase 1: Observation (2 weeks).** All pipeline parameters are frozen. The system runs continuously during waking hours, writing physical-world observations into OpenClaw's memory through the three-tier direct write strategy (physical-logs, physical-insights, physical-pattern.md) described in Section 4.5. Three observation methods operate in parallel.

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