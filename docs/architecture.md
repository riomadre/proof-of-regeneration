# Proof of Regeneration — System Architecture

## Overview

Proof of Regeneration is designed as a modular system for creating verifiable, human-reviewed records of ecological observations, restoration activities, regenerative land use, and future stewardship participation.

Rio Madre in Costa Rica will serve as the first real-world test site.

The system is intended to combine:

* field evidence;
* decentralized AI inference;
* structured records;
* human verification;
* provenance tracking;
* privacy controls;
* public and private publication options.

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

## 3. Nosana Inference Layer

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
* model name;
* model version;
* container image;
* container digest where available;
* prompt version;
* inference parameters;
* start and completion times;
* runtime;
* estimated cost;
* raw output hash.

## 4. Schema Validation

All model responses must be validated before review.

Validation should check:

* required fields;
* allowed categories;
* valid confidence range;
* valid review-priority values;
* valid sensitivity values;
* valid JSON structure;
* absence of unsupported fields;
* output length limits.

Invalid model output must be preserved but marked as failed validation.

The system may retry once with a repair prompt, but the original failed output must remain available for evaluation.

## 5. Human Review Layer

AI output is provisional and must not be treated as confirmed ecological evidence without review.

The reviewer may:

* approve the result;
* approve with corrections;
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
* review timestamp;
* review status;
* correction history.

Human review must never silently overwrite the original AI response.

## 6. Provenance Service

The provenance service will create a manifest linking the original evidence, AI inference, and human review.

A provenance manifest may include:

* record identifier;
* source image hash;
* source note hash;
* input bundle hash;
* Nosana job identifier;
* model name and version;
* container digest;
* prompt version;
* inference parameters;
* raw output hash;
* reviewed output hash;
* reviewer identifier;
* review status;
* timestamps;
* publication status;
* follow-up record identifiers.

The initial implementation may use SHA-256 hashes.

The manifest should allow another person to verify that the displayed record corresponds to the preserved inputs and outputs.

## 7. Storage Layer

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
* follow-up relationships.

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

## 8. Publication Controls

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

## 9. Location Privacy

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

## 10. Follow-Up Records

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

## 11. Benchmark Architecture

The benchmark system will use a curated Rio Madre dataset.

For each benchmark record, the system should store:

* expected category;
* curator notes;
* known uncertainty;
* sensitivity level;
* model output;
* validation status;
* human review result;
* inference latency;
* estimated cost;
* repeatability results.

The benchmark should support repeated inference for a fixed subset of images.

## 12. Security Principles

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

## 13. Proposed Technical Stack

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

## 14. Local-First Development

The system should work locally before Nosana credits are used.

The local version should support:

* mock inference responses;
* observation creation;
* schema validation;
* human review;
* provenance generation;
* record display.

The Nosana integration should be implemented behind a replaceable inference adapter.

Example interface:

```text
InferenceProvider
├── MockInferenceProvider
└── NosanaInferenceProvider
```

This allows the application to be developed and tested without consuming GPU credits.

## 15. Failure Handling

The system should handle:

* failed uploads;
* invalid images;
* failed Nosana jobs;
* model timeouts;
* invalid JSON;
* schema-validation errors;
* duplicate submissions;
* rejected records;
* unavailable private storage.

Failures should be recorded transparently and must not produce false completed records.

## 16. Architecture Priorities

The initial architecture should prioritize:

1. one complete working workflow;
2. clear human review;
3. preserved original outputs;
4. reproducible metadata;
5. privacy controls;
6. low compute use;
7. simple deployment;
8. measurable benchmark results.

Complex governance, payments, memberships, and multi-property administration are outside the initial architecture.
