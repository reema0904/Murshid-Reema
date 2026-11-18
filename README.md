# Murshid – LLM Application Engineering

**SDAIA Academy | AI Engineering Track**

Developed as part of the **LLM Application Engineering (SDA-AIE-213)** training program, under the guidance of **Meaad Al-Marri**.

**Training References:** [SDAIA Academy](https://github.com/SDAIAAcademy) | [Original Course Repository](https://github.com/almiyead-rgb/murshid-llm-application-engineering-sda-aie-213)

## Overview

Murshid is an educational service assistant designed to demonstrate the engineering workflow of LLM-based applications using Python and Google Colab.

The project focuses on structured responses, input validation, secure tool calling, authorization, guardrails, automated testing, and caching.

The core application uses a deterministic **FakeClient (mock mode)** and synthetic data rather than a live LLM or real government services.

**Target Users:** Students and developers learning LLM application engineering, secure tool integration, and automated evaluation.

## Repository Structure

```text
Murshid-Reema/
├── notebooks/          # Main project – Days 1–4
├── homework/           # Independent homework notebooks
├── murshid_output/     # Generated JSON results
└── README.md           # Project documentation
```

### Project Files

- [Main Project Notebook](notebooks/)
- [Extra Homework – Days 1–4](homework/)
- [Generated Results and Reports](murshid_output/)

The main notebook contains all four core labs. Each completed extra homework is maintained separately.

## Key Features

- **Structured Responses:** Consistent answers with trace IDs and latency measurements.
- **Input Validation:** Rejects missing, invalid, and unsupported requests.
- **Secure Tool Calling:** Read-only application status lookup with ownership verification.
- **Guardrails:** Input and response validation to support safe processing.
- **Automated Testing:** Golden test cases and regression checks.
- **Caching:** Reuses eligible public responses while excluding user-specific status information.

## Development Overview

| Day | Implementation |
|---|---|
| Day 1 | FakeClient, FAQ responses, and input validation |
| Day 2 | Reference extraction, tool routing, and authorization |
| Day 3 | Guardrails, response validation, and golden tests |
| Day 4 | Caching, performance measurements, and final evaluation |

## Key Results

| Metric | Result |
|---|---|
| Day 1 baseline checks | Passed |
| Day 2 tool tests | Passed |
| Day 3 golden tests | 10/10 |
| Day 4 regression tests | 10/10 |
| Cache hit rate | 66.7% |
| Mock calls without caching | 3 |
| Mock calls with caching | 1 |
| External model API calls (core) | 0 |

These results were obtained from controlled tests using synthetic data and mock components.

The caching experiment reduced mock-client calls from 3 to 1 for the tested requests. It does not establish real-world cost savings or production performance.

## Setup and Execution

1. Open the cumulative notebook from the `notebooks/` folder in Google Colab.
2. Select Python 3 with a CPU runtime.
3. Restart the runtime and run all cells sequentially from Day 1 to Day 4.
4. Review the generated outputs, test results, and final evaluation report.

The core project requires only Python's standard library, with no paid API, API key, GPU, or external model download.

The optional real-model homework uses separate notebooks and additional libraries.

## Dataset and Workflow

Murshid uses manually created **synthetic FAQ responses and application records**, not real user or government data.

The dataset contains reference IDs, fictional record owners, and simulated application statuses.

**Main Data Fields:**

- `request_id`: Identifies a simulated application.
- `owner`: Represents the fictional record owner.
- `status`: Stores the simulated application status.
- `answer`: Contains the returned response.
- `trace_id`: Identifies the request for tracing.
- `latency_ms`: Records local execution time.

**Example Test Cases:**

| Input | Expected Result |
|---|---|
| How can I check my application status? | Use the reference number |
| Status REF-1001 | `under_review` |
| Request without a reference number | `needs_clarification` |
| Status REF-9999 | `not_found` |
| Cancel REF-1001 | `unsupported_action` |
| Status REF-1002 | `access_denied` |

**Application Workflow:**

Input → Validation → Guardrails → Reference Extraction → Authorization → Tool Routing → Response Validation → Output

The read-only tool verifies record ownership against the trusted demonstration session. Caching is restricted to eligible public questions.

## Testing and Evaluation

The project uses predefined test cases to verify input validation, tool routing, authorization, guardrails, and response structure.

All ten golden test cases passed during Days 3 and 4.

**Extra Homework:**

- **Day 1:** Real-model inference using `google/flan-t5-small`.
- **Day 2:** Simulated tool-protocol validation (7/7 tests passed).
- **Day 3:** Error handling and invalid-input validation.
- **Day 4:** Real-model evaluation with 3/3 keyword checks and manual review of required facts.

Real-model homework is independent of the core mock application.

## Limitations and Future Improvements

Murshid uses a simulated client and synthetic records. It does not connect to real government services or provide production-level authentication.

Passing the predefined tests does not guarantee comprehensive semantic accuracy or security.

Future improvements could include real LLM integration, semantic evaluation, broader test coverage, and stronger authentication.

---

*This project is an independent educational implementation developed within the SDAIA Academy training context. It does not represent an official government service or imply SDAIA Academy endorsement.*
