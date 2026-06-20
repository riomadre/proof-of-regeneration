# Source Code

This directory will contain the application code for the Proof of Regeneration prototype.

The initial software should implement one complete workflow before expanding into additional features.

## Initial Development Goal

The first working version should support:

```text
Create observation
        ↓
Attach image and field note
        ↓
Run mock inference
        ↓
Validate structured output
        ↓
Review and correct result
        ↓
Generate provenance manifest
        ↓
Display completed record
```

The local prototype should work before Nosana compute credits are used.

## Planned Components

The exact framework and directory structure may change during implementation.

A likely structure is:

```text
src/
├── app/
├── components/
├── inference/
├── validation/
├── provenance/
├── storage/
├── review/
├── privacy/
└── tests/
```

## Application Layer

The application layer should provide interfaces for:

* creating a new observation;
* attaching an image;
* entering a field note;
* selecting an observation category;
* assigning a generalized location;
* setting a sensitivity level;
* viewing provisional AI output;
* reviewing and correcting the result;
* selecting publication status;
* viewing the final record and provenance information.

The application must not publish records automatically.

## Inference Layer

Inference should be implemented through a replaceable provider interface.

Suggested structure:

```text
InferenceProvider
├── MockInferenceProvider
└── NosanaInferenceProvider
```

### Mock Inference Provider

Used during local development.

It should:

* return predictable structured responses;
* allow schema validation to be tested;
* simulate successful and failed outputs;
* avoid consuming GPU credits;
* support interface development.

### Nosana Inference Provider

Added after Nosana access is approved.

It should:

* submit approved inputs;
* preserve job identifiers;
* record model and prompt information;
* retrieve raw output;
* record runtime and cost where available;
* handle failed or timed-out jobs;
* return data for validation and review.

## Validation Layer

The validation layer should check records against:

```text
schemas/observation.schema.json
```

and provenance manifests against:

```text
schemas/provenance.schema.json
```

Validation must preserve:

* original invalid output;
* validation errors;
* repair attempts;
* repaired output;
* final validation status.

Invalid model output should not be silently discarded.

## Human Review Layer

The review workflow should allow a reviewer to:

* approve;
* approve with minor edits;
* correct;
* reject;
* request follow-up evidence;
* change sensitivity;
* restrict publication.

The original AI response must remain preserved after correction.

## Provenance Layer

The provenance layer should generate:

* source hashes;
* input-bundle hash;
* output hashes;
* prompt metadata;
* model metadata;
* validation history;
* review history;
* publication history;
* manifest hash.

The implementation should use deterministic serialization before calculating the final manifest hash.

The exact canonicalization method must be documented.

## Privacy Layer

The application should support:

* private coordinates;
* generalized public zones;
* public and private image states;
* metadata removal;
* sensitivity flags;
* restricted publication;
* redaction notes.

Exact location data should remain private by default.

## Storage

The early prototype may use local files or a lightweight database.

Possible initial options include:

* local JSON files;
* SQLite;
* local object storage;
* a simple development database.

The project should avoid adding complex infrastructure before the core workflow works.

## Testing Priorities

Initial tests should cover:

* valid observation records;
* missing required fields;
* invalid confidence values;
* malformed hashes;
* unsupported categories;
* failed inference;
* invalid JSON;
* human correction history;
* publication restrictions;
* sensitive location handling;
* provenance generation;
* deterministic manifest hashing.

## Security

Never commit:

* API keys;
* access tokens;
* passwords;
* database credentials;
* private signing keys;
* private image URLs;
* personal information;
* exact sensitive-species locations.

Secrets must be provided through environment variables or secure deployment configuration.

## Out of Scope for the First Prototype

Do not prioritize:

* payments;
* memberships;
* booking systems;
* multi-property administration;
* tokens;
* decentralized governance;
* public social features;
* automated legal conclusions;
* continuous GPU endpoints;
* mobile applications;
* complex mapping.

The first priority is a complete, auditable observation workflow.

## Current Status

No production application code is currently claimed in this directory.

Source files should be added only when they represent working implementation or tests.
