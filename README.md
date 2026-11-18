# Murshid – LLM Application Engineering

**Developed as part of the SDAIA Academy – AI Engineering Track, within the LLM Application Engineering (SDA-AIE-213) training program, under the guidance of Meaad Al-Marri.**

**Training Reference:** [Original Training Repository](https://github.com/almiyead-rgb/murshid-llm-application-engineering-sda-aie-213)

## Overview

Murshid is an educational service assistant developed to demonstrate the engineering workflow of LLM-based applications using Python.

The project focuses on structured responses, input validation, secure tool calling, authorization, guardrails, evaluation, and caching.

The core application uses a deterministic **FakeClient (mock mode)** and synthetic data rather than a live language model or real government services.

## Repository Structure

```text
Murshid-Reema/
├── notebooks/          # Main project (Days 1–4)
├── homework/           # Independent homework notebooks
├── murshid_output/     # Generated JSON results and reports
└── README.md           # Project documentation
```

## Key Features

- **Structured Responses:** Consistent responses with trace IDs and latency measurements.
- **Input Validation & Guardrails:** Reject invalid and unsupported requests.
- **Secure Tool Calling:** Read-only status lookup with ownership verification.
- **Automated Testing:** Golden test cases and regression checks.
- **Caching:** Reuse eligible public responses to reduce repeated calls.

## Development Overview

| Day | Implementation |
|---|---|
| Day 1 | Mock client, FAQ responses, and input validation |
| Day 2 | Reference extraction, tool routing, and authorization |
| Day 3 | Guardrails, response validation, and golden tests |
| Day 4 | Caching, performance measurements, and final evaluation |

## Key Results

| Metric | Result |
|---|---|
| Day 1 baseline tests | Passed |
| Day 2 tool tests | Passed |
| Day 3 golden tests | 10/10 |
| Day 4 regression tests | 10/10 |
| Cache hit rate | 66.7% |
| Mock calls without caching | 3 |
| Mock calls with caching | 1 |
| External model API calls (core project) | 0 |

These results were obtained from controlled tests using synthetic data and mock components.

## Setup and Execution

1. Open the cumulative project notebook from the `notebooks/` directory in Google Colab.
2. Select Python 3 with a CPU runtime.
3. Run all cells sequentially from Day 1 through Day 4.
4. Review the generated JSON results and final evaluation report.

The core project requires no paid API, API key, GPU, or external model download.

## Dataset and Workflow

Murshid uses synthetic FAQ responses and application records, including reference IDs, record ownership, and simulated application statuses.

**Example Test Cases:**

| Input | Expected Result |
|---|---|
| How can I check my application status? | Use the reference number |
| Status REF-1001, Riyadh | `under_review` |
| My application status | `needs_clarification` |
| Status REF-9999? | `not_found` |
| Cancel REF-1001 | `unsupported_action` |
| Status REF-1002? | `access_denied` |

**Application Workflow:**

Input → Validation → Guardrails → Reference Extraction → Authorization → Tool Routing → Response Validation → Output

Caching is applied only to eligible public questions to protect user-specific information.

## Limitations and Future Improvements

The core project uses a simulated client and synthetic data rather than real government services or a live LLM.

The predefined tests do not guarantee comprehensive semantic accuracy or production-level security. The caching results do not represent actual API cost savings.

Future improvements may include real LLM integration, semantic evaluation, expanded testing, and stronger authentication.

---

*This project is an independent educational implementation developed within the SDAIA Academy training context and does not represent an official government service or imply Academy endorsement.*
