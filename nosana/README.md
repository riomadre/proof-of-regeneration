# Nosana

This directory contains the planned Nosana deployment materials for Proof of Regeneration.

Nosana will provide decentralized GPU infrastructure for multimodal inference during the project’s prototype and benchmark phases.

## Current Contents

### `deployment-plan.md`

Defines the intended deployment process, including:

* local-first development;
* finite-duration deployments;
* one replica;
* controlled container timeouts;
* staged testing;
* privacy review;
* cost tracking;
* schema validation;
* provenance recording;
* shutdown procedures.

## Planned Workflow

```text
Field image and note
        ↓
Privacy review
        ↓
Nosana workload
        ↓
Structured JSON output
        ↓
Schema validation
        ↓
Human review
        ↓
Provenance manifest
```

## Deployment Status

Nosana access and compute credits are currently pending approval.

No live deployment, completed job, model benchmark, or production inference endpoint is claimed unless corresponding evidence is added to this directory.

## Planned Artifacts

As implementation progresses, this directory may include:

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

These files should be added only when they represent real implementation work.

## Compute Principles

The project will:

* use the `Simple` deployment strategy;
* keep replica count at `1`;
* use finite container timeouts;
* stop idle deployments;
* test one record before processing batches;
* document runtime and cost;
* avoid continuously running endpoints during early development;
* use the lowest-cost compatible GPU market.

## Privacy

Initial tests should use only approved, low-sensitivity field images.

Do not submit:

* exact vulnerable-species locations;
* identifiable neighboring-property evidence;
* faces without consent;
* personal records;
* legal documents;
* credentials;
* API keys;
* private storage secrets.

## Secrets

Credentials must never be committed to the repository.

Future environment-variable names may include:

```text
NOSANA_API_KEY
PRIVATE_STORAGE_KEY
DATABASE_URL
ACCESS_TOKEN
PRIVATE_SIGNING_KEY
```

Only placeholder names may appear in public files.

## Schemas

Inference outputs should validate against:

```text
schemas/observation.schema.json
```

Provenance manifests should validate against:

```text
schemas/provenance.schema.json
```

## First Milestone

The first Nosana milestone will be complete when:

* one authorized Rio Madre image is processed;
* structured output is returned;
* the output is preserved;
* schema validation is recorded;
* a human reviews the result;
* a provenance manifest is generated;
* runtime and cost are documented;
* the deployment is stopped successfully.

## Current Status

This directory currently documents the planned deployment architecture.

It does not yet contain evidence of a completed Nosana workload.
