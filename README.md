# Proof of Regeneration

An open-source land-accountability system for creating verifiable, human-reviewed records of ecological stewardship and regenerative land activity using decentralized AI infrastructure.

Built for regenerative farms, conservation properties, retreat centers, and agritourism operators seeking to show what was funded, what happened on the land, what evidence exists, and what changed over time.

**First intended field deployment:** [Rio Madre](https://riomadre.com), Costa Rica

## Overview

Proof of Regeneration is an open-source system for documenting ecological observations, restoration activities, regenerative land use, and future visitor-supported stewardship through a transparent evidence and review workflow.

The system is designed to connect:

* original field evidence;
* structured AI-assisted interpretation;
* explicit uncertainty;
* human review and correction;
* provenance and integrity records;
* privacy and publication controls;
* follow-up observations over time.

Rio Madre, a eight-hectare conservation and agritourism landscape in Costa Rica, will serve as the first real-world test site.

The project is currently in the planning, schema-design, documentation, and technical-preparation stage.

No live Nosana deployment, completed benchmark, or production platform is currently claimed.

## The Problem

Conservation, regenerative agriculture, and responsible-tourism projects often make claims concerning:

* biodiversity;
* restoration;
* native-tree planting;
* watershed protection;
* habitat improvement;
* community participation;
* visitor-supported conservation.

These claims are frequently supported by scattered photographs, field notes, spreadsheets, and retrospective reports.

The available evidence may not clearly show:

* when an observation or activity occurred;
* what was actually visible;
* how an automated interpretation was produced;
* which model and prompt were used;
* whether a human corrected the result;
* whether sensitive information was removed;
* whether follow-up evidence exists;
* whether an activity produced a measurable outcome.

AI may help organize field evidence, but it may also hallucinate features, overstate confidence, confuse similar species, expose sensitive locations, or produce inconsistent results.

Proof of Regeneration is intended to make that process more transparent and auditable.

## Core Workflow

A field observer, land steward, researcher, or authorized participant submits:

1. a field photograph;
2. an observation note;
3. a date and generalized location;
4. an ecological or stewardship category;
5. an initial sensitivity and publication setting.

The planned workflow is:

```text
Field observation
        ↓
Image and note submission
        ↓
Privacy and input review
        ↓
Decentralized AI inference
        ↓
Structured JSON output
        ↓
Schema validation
        ↓
Human review and correction
        ↓
Provenance manifest
        ↓
Public, restricted, or private record
        ↓
Optional follow-up observation
```

The AI result is never treated as final evidence by default.

A human reviewer must:

* approve it;
* approve it with minor edits;
* correct it;
* reject it; or
* request follow-up evidence.

The original model output remains preserved alongside the reviewed result.

## Planned Nosana Workload

The initial prototype is intended to run a containerized open-source vision-language model through Nosana decentralized GPU infrastructure.

The workload will accept an approved image and field note and return schema-constrained JSON containing fields such as:

* provisional classification;
* classification level;
* visible evidence;
* alternative interpretations;
* confidence;
* uncertainty;
* human-review priority;
* location sensitivity;
* recommended follow-up;
* possible legal or responsibility-claim warning.

The model will be instructed to describe visible conditions without automatically determining:

* legality;
* ownership;
* responsibility;
* intent;
* regulatory compliance;
* ecological success.

Nosana access and compute credits are currently pending approval.

See:

* [Nosana deployment plan](nosana/deployment-plan.md)
* [Initial observation prompt](nosana/prompts/observation-v0.1.0.txt)
* [Planned job template](nosana/jobs/observation-job.json)

## Record Types

The initial system is intended to support:

### Ecological observations

Examples include:

* plants;
* fungi;
* wildlife;
* tracks and signs;
* habitat conditions.

### Watershed and landscape observations

Examples include:

* river level;
* flooding;
* erosion;
* sediment;
* fallen trees;
* seasonal dryness.

### Restoration and agroforestry activities

Examples include:

* native-tree planting;
* nursery transfers;
* mulching;
* soil work;
* shade establishment;
* habitat restoration.

### Human-disturbance observations

Examples include:

* cleared vegetation;
* burn evidence;
* earth movement;
* altered drainage;
* construction activity;
* exposed soil.

The system may describe visible conditions, but human review remains required before any broader interpretation or publication.

## Human Review and Uncertainty

Proof of Regeneration is not designed to treat AI-generated classifications as confirmed ecological findings.

The system explicitly distinguishes between:

* visible evidence;
* provisional interpretation;
* uncertainty;
* human correction;
* final reviewed record.

Preferred language includes:

* provisionally identified;
* appears consistent with;
* unresolved from available evidence;
* further observation required.

A structurally valid AI response may still be ecologically incorrect, unsafe to publish, or excessively confident.

## Provenance

Each completed record may generate a provenance manifest connecting:

* source-image hashes;
* field-note hash;
* input-bundle hash;
* inference provider;
* Nosana job identifier;
* model and version;
* container information;
* prompt version;
* inference parameters;
* raw-output hash;
* schema-validation result;
* human corrections;
* reviewed-output hash;
* publication state;
* manifest-integrity hash.

The purpose is to preserve how a record was created and changed rather than showing only the final interpretation.

See:

* [Observation schema](schemas/observation.schema.json)
* [Provenance schema](schemas/provenance.schema.json)
* [Schema documentation](schemas/README.md)

## Privacy and Publication Controls

Not every record should become public.

Sensitive information may include:

* exact locations of vulnerable species;
* nests or dens;
* identifiable people;
* neighboring-property details;
* private access routes;
* legal or contentious evidence;
* contributor information.

The system is designed to support:

* private coordinates;
* generalized public zones;
* redacted images;
* restricted records;
* public records;
* archived or rejected records.

Permanent storage should be used only for approved, non-sensitive material.

See:

* [Privacy and ethics](docs/privacy-and-ethics.md)

## Benchmark Plan

The project plans to evaluate approximately 50 to 100 curated Rio Madre records.

The benchmark will measure:

* inference success rate;
* JSON-schema validity;
* latency;
* estimated cost per record;
* human approval rate;
* correction rate;
* rejection rate;
* hallucinated-feature rate;
* classification overreach;
* uncertainty quality;
* privacy classification;
* repeatability across repeated jobs.

The benchmark is not intended to demonstrate perfect ecological identification.

Its purpose is to identify where decentralized multimodal inference is useful, where it fails, and where human judgment remains essential.

See:

* [Benchmark plan](docs/benchmark-plan.md)

## Rio Madre Use Case

Rio Madre provides a real land-management context for the project.

Potential records may include:

* forest-regeneration observations;
* flora and wildlife documentation;
* river and watershed conditions;
* native-tree planting;
* agroforestry activity;
* habitat restoration;
* weather-linked field observations;
* stewardship and educational activities.

The project will begin with authorized, low-sensitivity records and generalized locations.

## Regenerative Agritourism

Long term, Proof of Regeneration may help regenerative tourism and land projects document the relationship between participation, funding, field activity, and follow-up evidence.

Potential uses include:

* educational field programs;
* native-tree planting;
* agroforestry work;
* habitat restoration;
* biodiversity observation;
* watershed monitoring;
* stewardship residencies;
* conservation-supported visitor experiences.

The system should distinguish clearly between:

* an activity being funded;
* an activity being completed;
* evidence being recorded;
* a follow-up being performed;
* an ecological outcome being verified.

Participation or payment alone does not prove environmental benefit.

## Start Here

For a concise introduction:

* [Project overview](docs/project-overview.md)

For the technical direction:

* [System architecture](docs/architecture.md)
* [Development roadmap](docs/roadmap.md)
* [Benchmark plan](docs/benchmark-plan.md)

For governance of data and claims:

* [Privacy and ethics](docs/privacy-and-ethics.md)

For machine-readable structures:

* [Observation schema](schemas/observation.schema.json)
* [Provenance schema](schemas/provenance.schema.json)

For examples:

* [Example observation](sample-data/example-observation.json)
* [Example provenance manifest](sample-data/example-provenance.json)
* [Sample-data documentation](sample-data/README.md)

For Nosana preparation:

* [Nosana documentation](nosana/README.md)
* [Deployment plan](nosana/deployment-plan.md)

## Repository Structure

```text
proof-of-regeneration/
├── README.md
├── LICENSE
├── .env.example
├── docs/
│   ├── project-overview.md
│   ├── roadmap.md
│   ├── architecture.md
│   ├── privacy-and-ethics.md
│   └── benchmark-plan.md
├── schemas/
│   ├── README.md
│   ├── observation.schema.json
│   └── provenance.schema.json
├── sample-data/
│   ├── README.md
│   ├── example-observation.json
│   └── example-provenance.json
├── nosana/
│   ├── README.md
│   ├── deployment-plan.md
│   ├── prompts/
│   │   └── observation-v0.1.0.txt
│   └── jobs/
│       └── observation-job.json
└── src/
    └── README.md
```

## Project Status

Current work includes:

* defining the observation and provenance schemas;
* documenting the system architecture;
* preparing privacy and ethical safeguards;
* designing the benchmark methodology;
* creating synthetic sample records;
* preparing the planned Nosana workload;
* curating candidate Rio Madre field observations;
* designing a local-first prototype workflow.

No production application, live inference endpoint, completed Nosana job, permanent-storage integration, or verified ecological outcome is claimed at this stage.

## Development Principles

The project prioritizes:

* working code over speculative features;
* human review over automated certainty;
* explicit uncertainty;
* privacy protection;
* preserved correction history;
* reproducible infrastructure;
* efficient compute use;
* transparent reporting of failures;
* activity evidence separate from outcome claims;
* technology in service of land and stewardship.

## License

This project is released under the MIT License.
