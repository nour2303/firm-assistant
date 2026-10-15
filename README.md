# Firm Assistant

**Question.** How can a small firm ask natural-language questions about its own documents and records while keeping database access controlled?

Firm Assistant is a personal n8n practice project described in my [portfolio](https://nour2303.github.io/). The supplied project summary describes a route for document retrieval, a route for read-only SQL questions, and a blocked route for requests outside those boundaries. It also describes semantic caching and logging.

```mermaid
flowchart LR
    Q[User question] --> R[Intent router]
    R -->|Documents| D[Retrieve relevant passages]
    R -->|Structured data| S[Read-only SQL path]
    R -->|Disallowed| B[Blocked response]
    D --> A[Answer with context]
    S --> A
    A --> L[Log and review]
```

## Reported evaluation

The project summary reports **12 of 12 cases passed** on its own evaluation set. The cases and execution logs were not supplied with this repository, so that figure is a narrow self-reported result, not an audited accuracy or security rate.

## Design boundaries and limits

- Intended SQL behavior: reject non-`SELECT` statements and use a read-only database connection.
- The summary names Gemini, Supabase/PostgreSQL, n8n, retrieval, and caching. Exact versions and deployment configuration are not documented here.
- A workflow export, sample schema, evaluation cases/results, and demo recording have not been included. This README is an architecture and evidence summary, not an importable workflow.
- Before deployment, test access control, ambiguous questions, missing data, cache invalidation, malformed input, and sensitive-data exposure with real logs.

**Portfolio status:** personal project; no paying-client deployment or production security review is claimed.
