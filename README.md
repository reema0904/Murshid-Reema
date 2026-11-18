# Murshid – LLM Application Engineering

**Program:** LLM Application Engineering (SDA-AIE-213)  
**Instructor:** Meaad Al-Marri  
**Training:** SDAIA Academy

## Overview

Murshid is an educational service assistant developed to demonstrate the engineering workflow of LLM-based applications using Python.

The project focuses on structured responses, input validation, secure tool calling, authorization, guardrails, testing, and caching.

The core application uses a deterministic **FakeClient (mock mode)** and synthetic data, rather than a live language model or real government services.

## Repository Structure

```text
Murshid-Reema/
├── notebooks/          # Cumulative project (Days 1–4)
├── homework/           # Independent homework notebooks
├── murshid_output/     # Generated JSON results and reports
└── README.md           # Project documentation
```

## Key Features

- **Structured Responses:** Consistent answers with trace IDs and execution time.
- **Input Validation:** Rejects invalid or unsupported requests.
- **Tool Calling:** Simulates read-only application status lookups.
- **Authorization:** Prevents unauthorized access to application records.
- **Guardrails:** Validates inputs and response structures.
- **Automated Testing:** Uses golden test cases and regression checks.
- **Caching:** Reuses eligible public responses to reduce repeated calls.

## Development Overview

| Day | Implementation |
|---|---|
| Day 1 | Mock client, FAQ responses, and validation |
| Day 2 | Ticket extraction, tool routing, and authorization |
| Day 3 | Guardrails, response validation, and golden tests |
| Day 4 | Caching, performance measurements, and final evaluation |

## Setup and Execution

1. Open the cumulative notebook from the `notebooks/` directory in Google Colab.
2. Select Python 3 with a CPU runtime.
3. Run all cells sequentially from Day 1 to Day 4.
4. Review the generated results and evaluation reports.

The core project uses Python's standard library and requires no GPU, paid API, or API key.

## Dataset and Application Flow

Murshid uses manually created synthetic FAQ responses and application records.

The demonstration includes request IDs, record ownership, and application statuses. For example, `REF-1001` belongs to `demo-user-1` and has the status `under_review`.

**Example requests:**

| Input | Expected Result |
|---|---|
| How can I check my application status? | Use the reference number |
| Status REF-1001, Riyadh | `under_review` |
| My application status | `needs_clarification` |
| Status REF-9999? | `not_found` |
| Cancel REF-1001 | `unsupported_action` |
| Status REF-1002? | `access_denied` |

**Processing flow:**

Input → Validation → Guardrails → Reference Extraction → Authorization → Tool Routing → Response Validation → Output

The shared cache is restricted to eligible public questions.

## Testing and Results

| Metric | Result |
|---|---|
| Day 1 baseline tests | Passed |
| Day 2 tool tests | Passed |
| Day 3 golden tests | 10/10 |
| Day 4 regression tests | 10/10 |
| Cache hit rate | 66.7% |
| Mock calls without cache | 3 |
| Mock calls with cache | 1 |
| External model API calls (core) | 0 |

The results are based on controlled tests using synthetic data and mock components.

## Limitations and Future Improvements

Murshid does not use a live LLM in its core application, connect to real government records, or provide production-level authentication.

The predefined tests do not guarantee complete semantic accuracy or security. The caching measurements do not represent real-world API cost savings.

Future improvements may include real LLM integration, semantic evaluation, expanded testing, and stronger authentication.

## Training Attribution

Developed as part of **LLM Application Engineering – SDA-AIE-213**, within the SDAIA Academy training context, under **Meaad Al-Marri**.

- [Original Training Repository](https://github.com/almiyead-rgb/murshid-llm-application-engineering-sda-aie-213)
- [SDAIA Academy GitHub](https://github.com/SDAIAAcademy)

This is an independent educational implementation and does not imply official endorsement by SDAIA Academy.
