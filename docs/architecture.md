# RTIntel Architecture Notes

## Design goal

RTIntel is designed around a simple constraint: AI can reduce documentation friction, but clinical users must remain able to inspect and correct what the system extracts.

The prototype therefore favors transparent workflow steps over opaque automation.

## Current prototype flow

```text
Capture / Entry
    |
    v
Normalize input
    |
    +--> Manual structured fields
    |
    +--> Vision-assisted extraction
                |
                v
        Editable verification
                |
                v
         Structured record
```

## Key decisions

### 1. Human-in-the-loop extraction

Clinical information is too important to treat model output as authoritative. Extracted values are presented for review and correction before they become trusted structured data.

### 2. Minimize sensitive-data movement

The architecture is intentionally conservative about clinical images and patient-identifying information. Where possible, source images remain local and only the minimum necessary information should move between system components.

### 3. Separate capture from future intelligence

The first product problem is reliable workflow capture. Retrieval, agents, and knowledge assistance should sit on top of clean structured data rather than becoming dependencies for the basic workflow.

## Production evolution under consideration

```text
React Native Client
        |
        v
     FastAPI
        |
        +--> PostgreSQL
        |
        +--> Redis
        |
        +--> Retrieval layer
        |
        +--> Task-specific agents
        |
        v
 Containerized services
        |
        v
       AWS
```

These components represent a production roadmap, not a claim that the prototype is already deployed with this full stack.

## Engineering questions I am exploring

- What information truly needs persistence versus shift-local storage?
- Which extraction tasks are safe and useful enough to automate?
- Where should deterministic validation sit around model output?
- How can the product provide useful clinical context without drifting into unsupported clinical decision-making?
- What auditability is necessary when AI contributes to a documented workflow?
- How should permissions and tenancy work for department-level deployments?

## Why this architecture matters

The technical challenge is not simply connecting a mobile app to an LLM. The interesting work is designing a trustworthy boundary between clinical workflow, structured data, AI assistance, privacy, and eventual production operations.
