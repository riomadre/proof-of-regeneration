# Proof of Regeneration — System Architecture

## Overview

Proof of Regeneration is designed as a modular system for creating structured, human-reviewed records of ecological observations, restoration activities, regenerative land use, and future stewardship participation.

Rio Madre in Costa Rica will serve as the first intended real-world test site.

The system is intended to combine:

* field evidence;
* decentralized AI inference;
* structured records;
* human verification;
* provenance tracking;
* privacy controls;
* public and private publication options;
* follow-up evidence over time.

## Architectural Principle

The system is not designed around the assumption that AI output is authoritative.

It is designed around an evidence chain:

```text
Source evidence
        ↓
Provisional model interpretation
        ↓
Schema validation
        ↓
Human review
        ↓
Correction history
        ↓
Provenance manifest
        ↓
Follow-up record
```

The primary technical object is therefore not an AI answer.

It is a reviewable and versioned record.

## Core Workflow

```text
Field observation
        ↓
Image and note submission
        ↓
Input validation and privacy checks
        ↓
Decentralized AI inference on Nosana
        ↓
Structured JSON response
        ↓
Schema validation
        ↓
Human review and correction
        ↓
Provenance manifest
        ↓
Public or private record
        ↓
Optional follow-up observation
```

## Main Components

### 1. Observation Interface

The observation interface will allow a contributor to submit:

* one or more images;
* observation date and time;
* general location;
* field note;
* observation category;
* contributor identifier;
* publication preference;
* sensitivity flag.

The interface should support both ecological observations and land-stewardship activities.

Examples include:

* flora;
* fauna;
* fungi;
* watershed condition;
* erosion;
* restoration;
* agroforestry;
* tree planting;
* habitat monitoring;
* human disturbance.

## 2. Application API

The application API will:

* validate incoming data;
* remove unnecessary image metadata;
* detect missing required fields;
* assign a record identifier;
* generate source hashes;
* prepare the inference request;
* submit the workload to Nosana;
* store the raw model response;
* pass the response to schema validation;
* preserve all review history.

The API should not publish any record automatically.

## 3. Inference Provider Layer

Inference should use a replaceable provider interface.

```text
InferenceProvider
├── MockInferenceProvider
└── NosanaInferenceProvider
```

### Mock Inference Provider

Used for:

* interface development;
* schema testing;
* deterministic failure cases;
* validation testing;
* local-first development.

### Nosana Inference Provider

Used for:

* decentralized GPU execution;
* job metadata;
* deployment experiments;
* cost measurement;
* repeatability testing;
* container portability testing.

The provider abstraction allows the project to distinguish workflow design from infrastructure-specific execution.

## 4. Nosana Inference Layer

The Nosana workload will run a containerized open-source vision-language model.

The workload will receive:

* a field image;
* an observer note;
* an observation category;
* a structured prompt;
* a required output schema.

The model will return structured JSON containing fields such as:

* observation category;
* provisional classification;
* visible evidence;
* alternative interpretations;
* confidence;
* uncertainty;
* human-review priority;
* location sensitivity;
* recommended follow-up.

The system will record:

* Nosana job identifier;
* deployment identifier where applicable;
* GPU market reference where appropriate;
* model name;
* model version;
* container image;
* container digest where available;
* prompt version;
* inference parameters;
* start and completion times;
* runtime;
* estimated cost;
* raw-output hash.

## 5. Experimental Input Modes

The architecture should support multiple input configurations for benchmark testing:

### Image only

Used to test model interpretation without observer context.

### Note only

Used to test how much of the output is driven by text alone.

### Image plus note

Used for the intended production workflow.

### Controlled disagreement

Used where the observer note is intentionally incomplete, overly specific, or misleading.

The system should record the input mode for every benchmark run.

## 6. Schema Validation

All model responses must be validated before review.

Validation should check:

* required fields;
* allowed categories;
* valid confidence range;
* valid review-priority values;
* valid sensitivity values;
* valid JSON structure;
* absence of unsupported fields;
* output-length limits.

Invalid model output must be preserved but marked as failed validation.

The system may retry once with a repair prompt, but the original failed output must remain available for evaluation.

## 7. Evidence-Grounding Review

The review system should support scoring each visible-evidence statement:

* `2` — directly visible;
* `1` — plausible but ambiguous;
* `0` — unsupported or invented.

This allows the system to distinguish between:

* valid-looking structured output;
* genuinely grounded output.

Evidence-grounding scores should be stored separately from the final ecological interpretation.

## 8. Human Review Layer

AI output is provisional and must not be treated as confirmed ecological evidence without review.

The reviewer may:

* approve the result;
* approve with minor edits;
* correct the result;
* reject the result;
* request follow-up evidence;
* change the sensitivity level;
* restrict publication.

The system must preserve:

* original field note;
* original AI output;
* reviewer changes;
* final reviewed record;
* reviewer identifier;
* reviewer role;
* review timestamp;
* review duration;
* review status;
* correction history;
* correction severity.

Human review must never silently overwrite the original AI response.

## 9. Confidence Handling

Model-generated confidence should be stored as a model output signal.

It must not be represented as a statistically calibrated probability unless a separate calibration method is implemented and documented.

The architecture should support analysis of:

* confidence across repeated runs;
* confidence versus human approval;
* confidence versus correction severity;
* confidence under image-only and note-only conditions;
* confidence under misleading observer notes.

## 10. Provenance Service

The provenance service will create a manifest linking the original evidence, AI inference, validation, and human review.

A provenance manifest may include:

* record identifier;
* source-image hash;
* source-note hash;
* input-bundle hash;
* Nosana job identifier;
* model name and version;
* container digest;
* prompt version;
* inference parameters;
* raw-output hash;
* reviewed-output hash;
* reviewer identifier;
* review status;
* timestamps;
* publication status;
* follow-up record identifiers.

The initial implementation may use SHA-256 hashes.

## 11. Provenance Boundaries

Provenance can help demonstrate that:

* a specific record existed in a particular form;
* a displayed file corresponds to a known hash;
* a model and prompt version were recorded;
* a human correction was preserved;
* a record changed between versions.

Provenance does not prove by itself that:

* a photograph was taken where claimed;
* a timestamp is authentic;
* a field note is truthful;
* a species identification is scientifically correct;
* an activity produced an ecological outcome;
* a contributor had authority to make every claim.

The architecture distinguishes between:

### Integrity verification

Whether stored content matches a recorded hash.

### Human review

Whether an authorized reviewer accepted or corrected the interpretation.

### Scientific validation

Whether the ecological conclusion is supported by appropriate expertise and evidence.

### Field authenticity

Whether the source evidence genuinely represents the claimed place, time, and event.

These are separate layers.

## 12. Storage Layer

The system may use separate storage for different data types.

### Private object storage

Used for:

* original images;
* high-resolution files;
* sensitive evidence;
* private contributor materials.

### Application database

Used for:

* structured observations;
* review history;
* publication settings;
* model metadata;
* activity records;
* follow-up relationships;
* benchmark run metadata.

### Public record storage

Used for:

* approved observation summaries;
* redacted images;
* public provenance manifests;
* benchmark results.

### Optional permanent storage

Approved, non-sensitive manifests may later be anchored to decentralized permanent storage.

Permanent storage is not required for the initial local prototype.

Sensitive or legally contentious material must not be permanently published.

## 13. Publication Controls

Every record should have a publication status.

Suggested values:

* private;
* restricted;
* public;
* archived;
* rejected.

A public record may contain:

* approved image or thumbnail;
* generalized location;
* final reviewed description;
* confidence and uncertainty;
* model metadata;
* provenance hash;
* follow-up status.

A private or restricted record may contain more detailed evidence but should remain inaccessible to the public.

## 14. Location Privacy

Exact coordinates should not be public by default.

The system should support:

* exact private coordinates;
* generalized public zones;
* rounded coordinates;
* named habitat areas;
* fully hidden locations.

Sensitive examples include:

* nests;
* dens;
* rare species;
* vulnerable plants;
* private access routes;
* neighboring-property observations.

## 15. Follow-Up and Longitudinal Records

Proof of Regeneration should support linked records over time.

Examples:

```text
Tree planting
    ↓
Three-month survival check
    ↓
Six-month growth record
    ↓
One-year condition review
```

```text
Riverbank condition
    ↓
Restoration activity
    ↓
Rainfall event
    ↓
Post-event observation
```

Each follow-up record should reference the original record while maintaining its own evidence, review, and provenance.

The system should not infer success from the existence of an activity record.

## 16. Benchmark Architecture

The benchmark system will use a curated Rio Madre dataset.

For each benchmark record, the system should store:

* expected category;
* curator notes;
* known uncertainty;
* sensitivity level;
* input mode;
* prompt version;
* model output;
* validation status;
* evidence-grounding review;
* human-review result;
* review duration;
* inference latency;
* estimated cost;
* repeatability results.

The benchmark should support:

* structured versus unstructured prompts;
* image-only runs;
* note-only runs;
* image-plus-note runs;
* controlled note disagreement;
* repeated inference for a fixed subset.

## 17. Cost Accounting

The system should record:

* cost per completed inference;
* cost per valid structured output;
* cost per human-approved record;
* failed-job cost;
* startup time;
* active runtime;
* selected GPU market.

Cost per approved record is more meaningful than cost per inference because rejected or unusable outputs still consume compute.

## 18. Security Principles

The system must not store secrets in the public repository.

Never commit:

* API keys;
* private tokens;
* passwords;
* private storage credentials;
* personal identification;
* exact sensitive-species coordinates;
* unredacted legal documents.

Environment variables should be used for all credentials.

Public sample files must use:

* placeholder keys;
* anonymized identifiers;
* generalized locations;
* redacted evidence.

## 19. Proposed Technical Stack

The final stack may change during development.

Initial options include:

* frontend: Next.js or another lightweight web framework;
* application API: TypeScript or Python;
* validation: Zod, JSON Schema, or Pydantic;
* database: SQLite for local development, PostgreSQL for deployment;
* private image storage: S3-compatible object storage;
* inference: Nosana decentralized GPU infrastructure;
* model packaging: Docker;
* hashing: SHA-256;
* deployment: container-based hosting.

The project should avoid unnecessary infrastructure during the hackathon.

## 20. Local-First Development

The system should work locally before Nosana credits are used.

The local version should support:

* mock inference responses;
* observation creation;
* schema validation;
* human review;
* provenance generation;
* record display;
* controlled benchmark cases.

The Nosana integration should remain behind the inference-provider interface.

## 21. Failure Handling

The system should handle:

* failed uploads;
* invalid images;
* failed Nosana jobs;
* model timeouts;
* invalid JSON;
* schema-validation errors;
* duplicate submissions;
* rejected records;
* unavailable private storage;
* disagreement between image and note;
* repeated-run contradictions.

Failures should be recorded transparently and must not produce false completed records.

## 22. Architecture Priorities

The initial architecture should prioritize:

1. one complete working workflow;
2. clear human review;
3. preserved original outputs;
4. evidence-grounding review;
5. reproducible metadata;
6. privacy controls;
7. low compute use;
8. simple deployment;
9. measurable benchmark results;
10. longitudinal field records.

Complex governance, payments, memberships, and multi-property administration are outside the initial architecture.
