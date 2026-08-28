# RTIntel

**AI-assisted respiratory therapy workflow platform — engineering case study**

RTIntel is a mobile workflow concept and prototype focused on helping respiratory therapists capture, structure, and verify clinical and equipment data during hospital shifts.

> This repository is a **public engineering case study**, not the commercial source repository. Proprietary implementation details and product source remain private.

## Why I built it

Respiratory therapy workflows are often fragmented across handwritten notes, device screens, EHR documentation, shift reports, and memory. That creates friction during handoff and makes it harder to turn bedside observations into structured, reusable information.

RTIntel explores how mobile software and AI-assisted extraction can reduce that friction without removing clinician verification from the loop.

## What has been built

- Mobile workflow capture for ventilator, equipment, and clinical data
- Image-assisted extraction to help structure information from captured screens or documents
- Editable clinician verification before extracted information is accepted
- Privacy-conscious handling designed to avoid unnecessary transmission of patient-identifying information
- A mobile-first workflow informed by real respiratory therapy practice

## Current technical approach

- **Client:** React Native
- **AI / Vision:** OpenAI API / vision-assisted extraction
- **Workflow:** structured capture + editable verification
- **Domain:** respiratory therapy / clinical operations

## Product principles

### Clinician verification stays in the loop
AI-assisted extraction is treated as a drafting mechanism, not an unquestioned source of truth. The clinician remains responsible for reviewing and correcting structured output.

### Privacy by design
The architecture is designed to minimize unnecessary handling of patient-identifying information and keep clinical images local whenever possible.

### Workflow first
The product is built around what respiratory therapists actually need during a shift rather than around an AI feature looking for a use case.

## Architecture

```text
Respiratory Therapist
        |
        v
  Mobile Workflow
        |
        +--> Manual structured entry
        |
        +--> Image-assisted extraction
                    |
                    v
            Clinician verification
                    |
                    v
             Structured shift data
```

See [`docs/architecture.md`](docs/architecture.md) for the design rationale and planned evolution.

## Roadmap / exploration

The following are **planned or exploratory**, not presented as shipped production functionality:

- Retrieval-augmented clinical knowledge support
- Agent orchestration for task-specific clinical workflow assistance
- FastAPI service layer
- PostgreSQL / Redis persistence and caching
- Containerized deployment
- Cloud infrastructure on AWS

## What this case study demonstrates

- Translating domain expertise into product requirements
- Mobile application architecture
- Human-in-the-loop AI design
- Privacy-aware engineering decisions
- AI-assisted data extraction
- Product scoping across prototype and production phases

## Commercial source

RTIntel is intended to remain commercially protectable. This repository therefore focuses on the problem, architecture, technical decisions, and product reasoning rather than publishing the proprietary application source.

## About the builder

I’m Terin Pulley, a software engineer with a background in Android, full-stack development, agentic AI systems, and respiratory therapy. RTIntel sits directly at the intersection of those disciplines.
