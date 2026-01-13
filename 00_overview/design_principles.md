# Design Principles — Enterprise GenAI Architecture & Context Engineering

These principles guide every build, document, and diagram in this repository. They are intentionally enterprise-minded: they prioritize trust, controls, traceability, and long-term operability over demos.

## 1) The LLM is not the system
An LLM is a reasoning component—not a product. The system includes:
- context assembly
- retrieval
- guardrails
- validation
- workflow integration
- audit logging
- evaluation and drift controls

## 2) The LLM is not the source of truth
Enterprise facts must come from **approved sources**. The model must not “fill gaps” from prior training knowledge when accuracy matters.

If evidence is missing, the correct behavior is: **refuse or escalate**.

## 3) Context determines behavior
Most failures are context failures, not model failures. Context is engineered intentionally:
- role context (permissions and scope)
- task intent (summarize, compare, assess, draft)
- constraints (what the model must not do)
- policy injection (rules that override user intent)
- formatting requirements (structured outputs)

## 4) Retrieval must be intentional, not naive
“Vectorize everything and top-k” is not an enterprise retrieval strategy.
Retrieval must handle:
- tiers (must-include vs optional)
- source authority and weighting
- recency relevance
- conflicting documents
- token budgets
- citation rules

## 5) Governance is architectural, not procedural
Governance cannot depend on “people remembering the rules.”
Controls are embedded into the flow:
- RBAC / role scoping
- output classification
- mandatory citations
- prohibited outputs (e.g., legal conclusions)
- human-in-the-loop triggers
- refusal conditions
- audit artifacts

## 6) Refusal is a product feature
A reliable system must say:
- “I don’t know”
- “Insufficient evidence”
- “Conflicting sources”
- “Not permitted for your role”

Refusal rules are explicit and testable.

## 7) Traceability is non-negotiable
Every meaningful output should be explainable via:
- sources used (documents + chunks)
- context assembled (policy/constraints applied)
- model and prompt versions
- timestamps and user role
- evaluation outcome (pass/fail/needs review)

## 8) Guardrails are layered
No single technique is sufficient. Combine:
- pre-processing constraints (policy injection, role scope)
- retrieval discipline (evidence required)
- generation constraints (format + allowed claims)
- post-processing validation (citation checks, classification)
- workflow controls (review gates)

## 9) Design for the audit, not the demo
If a system can’t survive:
- an audit inquiry,
- a model upgrade,
- a policy change,
- or a user attempting misuse,
then it isn’t enterprise-ready.

## 10) Optimize for stable patterns over changing tools
Vendors, models, and libraries change quickly. Architecture patterns should remain stable:
- trust boundaries
- control points
- escalation paths
- evaluation harnesses
- governance artifacts

## 11) Security and privacy are first-class constraints
Assume:
- sensitive data exists
- prompts can leak data
- logs can become liabilities
- least privilege is mandatory

## 12) Evaluation is continuous, not an afterthought
Quality must be measured with repeatable tests:
- hallucination rate (within lab constraints)
- citation accuracy
- refusal correctness
- policy compliance
- drift scenarios

## 13) “Production-ready” means operable
Operable systems include:
- monitoring signals
- defined failure handling
- versioning
- rollback/upgrade strategy
- documentation that new teams can use

## 14) Prefer boring solutions that work
Enterprise systems should be:
- predictable
- explainable
- testable
- maintainable

“Boring” is a reliability compliment.

## 15) Document decisions like an architect
For every major choice, capture:
- intent
- constraints
- tradeoffs
- failure modes
- mitigations
- residual risks
