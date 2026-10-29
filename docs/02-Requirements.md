
# FraudLens — Requirements Specification

## 1. Purpose
This document defines the functional and non-functional requirements, initial scope, and acceptance criteria for FraudLens, an end-to-end fraud-intelligence prototype.

## 2. Users and Stakeholders
- Fraud analyst: Primary user who needs to review and inspect  on critical transaction  based on priority order of risk, and record outcomes
- Financial institution: potential organisational beneficiary of more effective fraud investigation.
- Cardholders: indirect beneficiaries of improved fraud detection.
> The initial prototype is designed around the fraud analyst's investigation workflow.

## 3. Functional Requirements

> FR-0X = Means Functional requirment number X

| ID | Requirement | Acceptance criterion |
|---|--------------|----------------------|
| FR-01 | Validate transaction inputs. | A valid request is accepted; a request with missing or invalid required fields receives a clear validation error and does not crash the service. |
| FR-02 | Predict transaction risk. | A valid request returns a risk score and the model version used. The score is not described as a calibrated probability unless calibration is evaluated. |
| FR-03 | Apply a separate decision policy. | The policy maps the model output to a configured risk category or recommended action. Policy settings are kept separate from model training and prediction code. |
| FR-04 | Rank investigation cases. | Eligible cases can be sorted by risk score. The review capacity and tie-handling behaviour are documented. |
| FR-05 | Explain predictions where supported. | For a supported model and input, the system displays feature-contribution information and states that contributions do not prove causation. If explanations are unavailable, the system reports that limitation clearly. |
| FR-06 | Manage investigation cases. | A user can view a case and record one of the supported outcomes: confirmed fraud, legitimate, or inconclusive. |
| FR-07 | Persist cases and outcomes. | Case details and outcome changes can be saved to and retrieved from PostgreSQL. Outcome changes include a timestamp; the recorded outcome is not treated automatically as verified ground truth. |
| FR-08 | Expose service health. | A health endpoint returns a clear status. Dependency checks, if included, distinguish API health from database availability. |
| FR-09 | Evaluate model performance. | An evaluation workflow calculates the selected metrics on an appropriate labelled evaluation set and records the evaluation setup. |
| FR-10 | Track model versions. | A prediction record identifies the model version that produced it. |
| FR-11 | Show core information in a dashboard. | The dashboard displays model/evaluation summaries and the ranked investigation queue, and supports viewing case details and recording outcomes. |
| FR-12 | Record basic monitoring information. | The system can report basic input/data-quality issues and service errors without logging secrets or unnecessary sensitive transaction data. |


## 4. Non-Functional Requirements
> NFR denotes Non-functional requirement

 
| ID | Area |  acceptance criteria |
|---|-------|------------------------------------|
| NFR-01 | Reliability | Expected validation and application errors return appropriate responses instead of unhandled exceptions. |
| NFR-02 | Performance | Prediction latency is measurable. A numerical latency target will be set after measuring a baseline in the intended environment. |
| NFR-03 | Maintainability | API routing, prediction, decision policy, persistence, and evaluation responsibilities are separated into understandable modules. |
| NFR-04 | Reproducibility | Setup instructions, dataset preparation steps, training configuration, and evaluation procedure are documented. Dataset redistribution is subject to its licence and terms. |
| NFR-05 | Testability | Automated tests cover core decision-policy logic, input validation, key API behaviour, and persistence operations. |
| NFR-06 | Portability | The initial application can be run using documented local setup steps and a Docker-based workflow. |
| NFR-07 | Interpretability | Any displayed explanation identifies feature contributions as model explanations, not causal proof. |


## 5. MVP Scope
> The MVP is the smallest end-to-end version that demonstrates the core fraud-intelligence workflow. Features will be added incrementally as the project and my engineering skills develop.

Included in the Initial Release:
* Audit and prepare the selected historical fraud dataset.
* Train, evaluate, and save a reproducible ML pipeline.
* Provide a FastAPI prediction endpoint.
* Implement a configurable decision policy.
* Build a ranked investigation queue.
* Persist investigation cases and outcomes using PostgreSQL.
* Provide a Streamlit dashboard for predictions and investigation workflows.
* Add automated tests, Docker-based setup, and basic service and data-quality monitoring. 

## 6. Data and System Constraints
* The initial model will use a publicly available historical credit card fraud dataset.
* Dataset provenance, licensing, schema, label quality, feature meanings, timestamps, and suitability for evaluation must be verified before finalising the ML pipeline.
* Anonymised features will not be assigned invented real-world meanings.
* Historical evaluation results do not establish performance on future transactions or in a real financial institution.
* Model scores will not be treated as calibrated probabilities unless calibration is evaluated and justified.
* Analyst-recorded outcomes may be incomplete, delayed, or uncertain and will not automatically be treated as reliable training labels.
* The initial system is a portfolio prototype and will not authorise or block real payments.










