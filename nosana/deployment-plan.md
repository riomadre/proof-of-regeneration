# Proof of Regeneration — Nosana Deployment Plan

## Purpose

This document defines the planned use of Nosana decentralized GPU infrastructure for the Proof of Regeneration prototype.

The initial objective is to run a containerized multimodal workload that accepts a field image and observer note, then returns schema-constrained JSON for human review.

No live Nosana deployment is claimed until corresponding job identifiers, configuration files, logs, and results are added to this repository.

## Deployment Principles

Nosana compute credits are limited and should be used only for defined testing and benchmark activity.

The project will:

* use finite-duration deployments;
* select the `Simple` deployment strategy;
* maintain one replica;
* use a limited container timeout;
* stop deployments whenever they are idle;
* test locally before consuming GPU credits;
* begin with one image;
* scale only after schema validation works;
* record runtime and estimated cost;
* avoid continuous public endpoints during early development.

## Initial Workload

The first Nosana workload should:

1. receive one approved Rio Madre field image;
2. receive one short field note;
3. receive an observation category;
4. apply a fixed prompt version;
5. return valid JSON matching the observation schema;
6. preserve the raw output;
7. record deployment and job metadata;
8. terminate after the test.

## Planned Input

The workload input should contain:

```json
{
  "record_id": "rm-2026-0001",
  "category": "flora",
  "field_note": "A compound-leaved plant was observed along a humid forest edge.",
  "image_reference": "private-or-temporary-image-reference",
  "output_schema_version": "0.1.0",
  "prompt_version": "0.1.0"
}
```

The real implementation may use:

* a temporary signed image URL;
* a mounted file;
* an encoded image payload;
* another Nosana-compatible input mechanism.

The selected method must avoid exposing private storage credentials.

## Planned Output

The workload should return only structured JSON containing:

* provisional classification;
* classification level;
* visible evidence;
* alternative interpretations;
* confidence;
* uncertainty;
* human-review priority;
* location sensitivity;
* recommended follow-up;
* possible legal or responsibility claim flag.

Example:

```json
{
  "provisional_classification": "Plant appears consistent with a Mimosa or related legume.",
  "classification_level": "unresolved",
  "visible_evidence": [
    "Compound leaves",
    "Paired leaflets",
    "Low-growing form"
  ],
  "alternative_interpretations": [
    "Related member of the legume family"
  ],
  "confidence": 0.61,
  "uncertainty": "Flowers, fruit, stem details, and leaf response are not visible.",
  "human_review_priority": "medium",
  "location_sensitivity": "low",
  "recommended_follow_up": [
    "Photograph the stem",
    "Capture flowers or fruit",
    "Observe leaf response after touch"
  ],
  "legal_or_responsibility_claim_detected": false
}
```

The model must not include markdown, introductory text, or commentary outside the JSON object.

## Model Selection Criteria

The initial model should be selected based on:

* multimodal image and text support;
* compatibility with containerized deployment;
* GPU memory requirements;
* structured-output reliability;
* inference cost;
* startup time;
* license compatibility;
* ecological-image performance;
* ability to represent uncertainty;
* ability to follow a strict JSON schema.

The project should not select a model only because it is the largest available option.

A smaller model may be preferable if it:

* starts faster;
* costs less;
* follows JSON instructions more reliably;
* performs adequately on the benchmark.

## Local-First Requirement

Before the first Nosana deployment, the project should have:

* a valid observation schema;
* a valid provenance schema;
* an anonymized sample record;
* a fixed prompt draft;
* local schema validation;
* a mock inference provider;
* a method for preserving raw outputs;
* a documented privacy review.

Nosana credits should not be used to solve basic application errors that can be identified locally.

## First Deployment Procedure

When Nosana access is available:

1. Open the Nosana deployment interface.
2. Select the intended container or workload configuration.
3. Click `Configure`.
4. Open `Deployment Configuration`.
5. Select `Simple` as the deployment strategy.
6. Keep the replica count at `1`.
7. choose a finite container timeout;
8. select the lowest-cost compatible GPU market;
9. save the deployment configuration;
10. launch the workload;
11. submit one approved test record;
12. preserve the raw response;
13. record runtime and cost;
14. stop the deployment after the result is retrieved.

## Initial Test Sequence

### Test 1 — Container Startup

Goal:

Confirm that the container starts successfully.

Record:

* deployment identifier;
* selected GPU market;
* startup time;
* container image;
* container digest where available;
* any errors.

Do not submit the full benchmark at this stage.

### Test 2 — Text-Only Structured Output

Goal:

Confirm that the model can return valid schema-constrained JSON before testing image input.

Use a short synthetic observation note.

Record:

* raw output;
* JSON validity;
* schema validity;
* runtime;
* cost.

### Test 3 — Single Image

Goal:

Process one authorized, low-sensitivity Rio Madre image.

Record:

* job identifier;
* image hash;
* prompt version;
* raw output;
* schema-validation result;
* human-review result;
* runtime;
* cost.

### Test 4 — Five-Record Batch

Goal:

Test multiple observation categories before committing to the main benchmark.

Suggested set:

* one flora observation;
* one wildlife or wildlife-sign observation;
* one watershed condition;
* one restoration or agroforestry activity;
* one ambiguous or difficult case.

Proceed to the larger benchmark only after these outputs can be validated and reviewed.

## Prompt Strategy

The inference prompt should instruct the model to:

* describe only visible evidence;
* avoid definitive identification where evidence is insufficient;
* separate observations from interpretations;
* state uncertainty explicitly;
* avoid legal conclusions;
* avoid assigning responsibility;
* identify location sensitivity;
* recommend useful follow-up;
* return JSON only;
* use the exact required field names.

Prompt versions should be stored in the repository once implementation begins.

Suggested future location:

```text
nosana/prompts/observation-v0.1.0.txt
```

## Schema Validation

Every response should be checked against:

```text
schemas/observation.schema.json
```

The application should preserve:

* the original raw output;
* validation status;
* validation errors;
* any repair attempt;
* repaired output;
* final human-reviewed output.

If a repair prompt is used, the original failed response must not be discarded.

## Provenance Recording

Every completed job should contribute to a provenance manifest containing:

* record identifier;
* source hashes;
* Nosana job identifier;
* deployment identifier where applicable;
* model name;
* model version;
* container image;
* container digest;
* prompt version;
* prompt hash;
* inference parameters;
* runtime;
* estimated cost;
* raw output hash;
* validation result;
* review result;
* reviewed output hash.

The manifest should validate against:

```text
schemas/provenance.schema.json
```

## Privacy and Data Handling

Only approved, low-sensitivity images should be used for initial Nosana tests.

Do not submit:

* exact rare-species locations;
* identifiable neighboring-property evidence;
* faces without consent;
* personal documents;
* private correspondence;
* legal records;
* access credentials;
* API keys;
* private storage secrets.

Before inference:

* remove unnecessary image metadata;
* use generalized location text;
* review the image background;
* confirm source rights;
* assign a sensitivity level.

If Nosana execution or job output is publicly visible, do not place private information in prompts, filenames, environment variables, or logs.

## Secrets

Credentials must be provided through secure environment variables or the approved Nosana secret mechanism.

Never commit:

```text
NOSANA_API_KEY
PRIVATE_STORAGE_KEY
DATABASE_URL
ACCESS_TOKEN
PRIVATE_SIGNING_KEY
```

The repository may later include an example environment file:

```text
.env.example
```

It must contain placeholder names only, never real values.

## Credit Allocation

The initial $70 credit allocation should be treated as a testing budget.

Indicative allocation:

| Purpose                             | Target maximum |
| ----------------------------------- | -------------: |
| Container startup and compatibility |             $8 |
| Model and prompt validation         |            $10 |
| Five-record test batch              |             $7 |
| Main benchmark                      |            $15 |
| Repeatability testing               |            $15 |
| Final demonstration                 |             $5 |
| Contingency                         |            $10 |

These are planning limits, not guaranteed costs.

Actual spending should be documented from Nosana usage data where available.

## Cost Tracking

For every test, record:

* GPU market;
* hourly price;
* startup time;
* active runtime;
* number of records;
* estimated or actual cost;
* failed-job cost;
* average cost per completed record.

A future results file may be stored at:

```text
nosana/results/compute-usage.csv
```

## Deployment Artifacts

As the project develops, this directory may contain:

```text
nosana/
├── README.md
├── deployment-plan.md
├── prompts/
│   └── observation-v0.1.0.txt
├── jobs/
│   └── observation-job.json
├── containers/
│   └── README.md
└── results/
    └── compute-usage.csv
```

These files should be added only when they reflect real implementation.

Do not add empty technical artifacts solely to make the repository appear more complete.

## Failure Handling

Document failures including:

* container startup failure;
* insufficient GPU memory;
* model download failure;
* invalid image input;
* request timeout;
* malformed JSON;
* schema-validation failure;
* deployment interruption;
* unavailable GPU market;
* unexpected cost.

Failures should be preserved as benchmark evidence where appropriate.

## Success Criteria

The first Nosana milestone is complete when:

* one authorized Rio Madre image is processed;
* the response is preserved;
* the response is valid JSON or its validation failure is documented;
* model and deployment metadata are recorded;
* a human reviews the result;
* a provenance manifest is generated;
* runtime and cost are reported;
* the deployment is stopped successfully.

The initial goal is not a continuously available production service.

It is a documented, reproducible, and credit-efficient decentralized inference workflow.

## Current Status

Nosana access and compute credits are pending approval.

This document describes the planned deployment process and does not claim that a Nosana model, job, or live deployment currently exists.
