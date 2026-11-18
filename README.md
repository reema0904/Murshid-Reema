# Murshid – LLM Application Engineering

**A Structured Service Assistant Simulation**

**Program:** LLM Application Engineering – SDA-AIE-213  
**Training Context:** SDAIA Academy – AI Engineering Track  
**Instructor:** Meaad Al-Marri  
**Project:** Murshid-Reema

## 1. Project Overview

Murshid is an educational service assistant developed to demonstrate the engineering principles behind LLM-based applications.

The project simulates how a service assistant receives user questions, validates requests, retrieves application status through an authorized tool, applies guardrails, evaluates responses, and improves efficiency through caching.

The core project uses a deterministic `FakeClient` rather than a live Large Language Model. All application records are synthetic.

## 2. Problem Statement and Target Users

Service assistants must handle user requests accurately while protecting information, rejecting invalid inputs, and maintaining predictable responses.

Murshid demonstrates how these requirements can be addressed through a structured application workflow.

**Intended users:**
- Students learning LLM application engineering.
- Developers exploring structured response and tool-calling workflows.
- Learners studying application validation, testing, and performance measurement.

## 3. Project Scope and Features

The application demonstrates:

- Arabic and English predefined FAQ responses.
- Structured responses with trace identifiers and latency measurements.
- Reference number extraction and validation.
- Read-only application status lookup.
- Record ownership and authorization checks.
- Input guardrails and response validation.
- Automated golden test cases.
- Public-response caching and performance comparison.

The application does not provide real government services or access live application records.

## 4. Four-Day Development Journey

| Day | Focus | Implementation |
|---|---|---|
| Day 1 | Foundations | Mock client, service directory, input validation, and response contract |
| Day 2 | Structure & Tools | Ticket extraction, authorization, routing, and read-only status lookup |
| Day 3 | Guardrails & Testing | Input guards, response validation, processing pipeline, and ten golden test cases |
| Day 4 | Performance & Evaluation | Public-response caching, regression testing, metrics, and final reporting |

All four stages were developed in one cumulative Google Colab notebook.

## 5. Technology and Environment

**Core project requirements:**

- Python 3
- Google Colab
- CPU runtime
- Python standard library
- JSON for structured outputs
- GitHub for version control

The core project requires no paid API, API key, GPU, or external language-model download.

The optional real-model homework uses a separate environment and additional libraries.

## 6. How to Run

1. Open the cumulative project notebook from the `notebooks` directory in Google Colab.
2. Select Python 3 and CPU, with no hardware accelerator.
3. Start a fresh runtime.
4. Run all notebook cells sequentially, from Day 1 through Day 4.
5. Inspect the printed responses, validation checks, and test results.
6. Review the generated JSON files.
7. Compare the outputs with the documented expected behavior.

**Project files:**

- [Core Project Notebook](notebooks)
- [Completed Homework](homework)
- [Generated Outputs](murshid_output)

The homework notebooks are independent from the core project and should be run separately.

## 7. Dataset and Data Fields

Murshid uses a small, manually created synthetic dataset embedded in the Python code.

The dataset includes:

**Public service directory:** predefined Arabic and English responses to selected service questions.

**Synthetic application records:**

| Request ID | Owner | Status |
|---|---|---|
| REF-1001 | demo-user-1 | under_review |
| REF-1002 | demo-user-2 | approved |
| REF-9999 | Not present | not_found |

The trusted demonstration session uses `demo-user-1`.

Important fields include:

- `request_id`: identifies a synthetic application record.
- `owner`: identifies the fictional record owner.
- `status`: stores the simulated application status.
- `trace_id`: identifies a response for tracing.
- `answer`: contains the returned message.
- `model`: identifies the simulated model.
- `latency_ms`: records local execution time.

All records are educational examples, not real application or government data.

## 8. Application Architecture and Workflow

Murshid follows a structured processing workflow:

1. **Input:** Receive the user's question.
2. **Validation:** Check that the input satisfies the required format.
3. **Guardrails:** Reject unsupported or unsuitable requests.
4. **Extraction:** Identify a valid application reference when relevant.
5. **Authorization:** Verify record ownership using the trusted demonstration session.
6. **Tool Routing:** Call the read-only status tool when appropriate.
7. **Response Validation:** Check the response structure and expected fields.
8. **Caching:** Reuse eligible public FAQ responses without caching user-specific status data.
9. **Output:** Return the structured response.

### Authorization and Tool Safety

Knowing a reference number does not establish ownership.

The status tool verifies the trusted user before returning a record's status. Unsupported actions are rejected, and the synthetic records remain unchanged.

These checks demonstrate application-level security principles, not production authentication.

### Caching Rules

Caching is limited to eligible public questions.

User-specific application status responses are not placed in the shared cache, reducing the risk of disclosing information between users.

## 9. Example Inputs and Expected Outputs

| User Input | Expected Behavior |
|---|---|
| How can I check my application status? | Return instructions to use the reference number |
| Status REF-1001, Riyadh | `under_review` |
| My application status | `needs_clarification` |
| Status REF-9999? | `not_found` |
| Cancel REF-1001 | `unsupported_action` |
| Status REF-1002? | `access_denied` |

These examples demonstrate different application behaviors, including successful requests, clarification, rejection, and authorization enforcement.

## 10. Testing and Evaluation

The project was tested using predefined cases and automated assertions.

### Observed Results

| Test or Metric | Result |
|---|---|
| Day 1 baseline checks | Passed |
| Day 2 structured tool tests | Passed |
| Day 3 golden tests | 10/10 passed |
| Day 4 golden regression tests | 10/10 passed |
| Day 4 cache hit rate | 66.7% |
| Mock calls without caching | 3 |
| Mock calls with caching | 1 |
| External model API calls in core project | 0 |

### Evaluation Interpretation

The application successfully passed the predefined behavioral tests in the simulated environment.

The caching experiment reduced mock-client calls from 3 to 1 for the tested sequence, with two cache hits out of three requests.

This result demonstrates caching behavior within the experiment; it does not establish production speed improvements or financial savings.

Execution times can vary between runs and environments.

## 11. Validation and Safety Testing

The tests cover selected cases involving:

- Correctly structured requests.
- Missing or invalid inputs.
- Unknown application references.
- Unauthorized record access.
- Unsupported operations.
- Blocked instructions.
- Invalid response structures.
- Regression behavior across the application workflow.

A rejected unsafe or unauthorized request is considered a successful test when rejection is the expected behavior.

The ten golden cases measure predefined behaviors, not comprehensive security or real-model language quality.

## 12. Extra Homework

Independent homework activities demonstrate concepts outside the core mock application.

**Day 1 – Real Model:** A small local FLAN-T5 model was used to generate an answer from a supplied context.

**Day 2 – Tool Protocol:** Seven simulated tool-protocol test cases passed, with the original records unchanged.

**Day 3 – Error Handling:** Invalid inputs were intentionally rejected, and a corrected input was accepted.

**Day 4 – Evaluation:** An independent evaluation exercise may be added separately.

These activities are separate from the cumulative core project. The real-model demonstration is not evidence that the core application uses live model inference.

## 13. Project Limitations

Murshid has several limitations:

- The core application uses a deterministic FakeClient, not a trained language model.
- All data is synthetic and limited in scope.
- No actual government service or production API is connected.
- Authorization relies on a trusted demonstration fixture.
- The guardrails do not guarantee protection against every possible attack.
- Ten successful golden cases do not establish comprehensive semantic accuracy.
- The caching results come from a small controlled experiment.
- No actual API cost savings or production latency gains were measured.

## 14. Future Improvements

Potential improvements include:

- Integrating a real language model with appropriate safety controls.
- Evaluating semantic correctness and required facts.
- Expanding the test dataset and edge cases.
- Strengthening authentication and authorization.
- Improving logging and error monitoring.
- Conducting larger performance and security evaluations.

## 15. Training Attribution and References

This educational project was developed as part of the **LLM Application Engineering – SDA-AIE-213** training program in the SDAIA Academy training context, under instructor **Meaad Al-Marri**.

**References:**

- [Original Murshid Training Repository](https://github.com/almiyead-rgb/murshid-llm-application-engineering-sda-aie-213)
- [SDAIA Academy GitHub](https://github.com/SDAIAAcademy)
- [Project Submission Guidelines](https://github.com/almiyead-rgb/murshid-llm-application-engineering-sda-aie-213/blob/main/docs/git.md)

This is an independent educational implementation. It does not represent an official government service, nor does it imply endorsement or certification by SDAIA Academy.
