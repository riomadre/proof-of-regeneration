# Proof of Regeneration — Project Overview

## Overview

Proof of Regeneration is an open-source system for creating structured, human-reviewed, and verifiable records of ecological observations, restoration activities, regenerative land use, and future visitor-supported stewardship.

The project is being developed for the Decentralize AI hackathon.

Rio Madre, a conservation-centered landscape and future agritourism project in Costa Rica, will serve as the first real-world test site.

## The Problem

Conservation, regenerative agriculture, and sustainable tourism projects often make claims about:

* biodiversity;
* restoration;
* tree planting;
* watershed protection;
* habitat improvement;
* local employment;
* visitor-supported conservation.

These claims are frequently documented through isolated photographs, written reports, spreadsheets, or promotional language.

The available evidence may not clearly show:

* when an activity occurred;
* where it occurred;
* what was actually observed;
* who reviewed the record;
* whether the interpretation later changed;
* whether follow-up evidence exists;
* which model or method produced an automated result.

AI can assist with organizing ecological evidence, but AI output may also:

* hallucinate visible features;
* overstate confidence;
* confuse similar species;
* make unsupported causal claims;
* produce inconsistent results;
* expose sensitive information.

Proof of Regeneration is intended to create a more transparent workflow.

## Core Concept

A field observer submits:

* a photograph;
* a field note;
* an observation date;
* a generalized location;
* an observation or activity category.

A decentralized vision-language workload processes the evidence and returns structured information such as:

* provisional classification;
* visible evidence;
* alternative interpretations;
* confidence;
* uncertainty;
* human-review priority;
* location sensitivity;
* recommended follow-up.

The AI result is not treated as confirmed evidence.

A human reviewer must:

* approve it;
* correct it;
* reject it; or
* request follow-up evidence.

The system preserves both the original model response and the final reviewed record.

## Core Workflow

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

## Why Decentralized AI

The project plans to use Nosana decentralized GPU infrastructure for multimodal inference.

Decentralized infrastructure is relevant because it may allow land stewards and smaller conservation projects to:

* access GPU compute without maintaining dedicated infrastructure;
* use portable, containerized workloads;
* preserve reproducible deployment information;
* avoid dependence on a single centralized application;
* maintain greater control over their data and record formats.

The hackathon prototype will test whether decentralized inference can produce sufficiently structured, cautious, and repeatable outputs for practical field documentation.

## First Deployment Site

**Rio Madre — Costa Rica**

Rio Madre is a seven-hectare landscape in the Río Nosara watershed focused on:

* natural forest regeneration;
* wildlife-corridor continuity;
* watershed observation;
* ecological documentation;
* conservation education;
* agroforestry;
* responsible long-term agritourism.

Rio Madre provides original field observations and a real land-management context for testing the system.

The project is not relying only on downloaded demonstration images or a simulated conservation scenario.

## Initial Record Types

The prototype is intended to support:

### Ecological observations

Examples:

* plants;
* fungi;
* wildlife;
* tracks;
* feeding evidence;
* habitat conditions.

### Watershed and landscape observations

Examples:

* river levels;
* flooding;
* erosion;
* sediment;
* fallen trees;
* seasonal dryness.

### Restoration and agroforestry activities

Examples:

* native-tree planting;
* mulching;
* nursery transfers;
* habitat restoration;
* soil work;
* shade-tree establishment.

### Human-disturbance observations

Examples:

* visible vegetation clearing;
* burn evidence;
* earth movement;
* altered drainage;
* exposed soil.

The system may describe visible conditions, but it must not automatically determine legal responsibility, regulatory violations, ownership, or intent.

## Human Verification

Human review is central to the project.

AI is used to assist with:

* organizing evidence;
* identifying visible features;
* suggesting provisional interpretations;
* representing uncertainty;
* recommending follow-up.

AI is not used as the final authority.

The system preserves:

* the original field note;
* the original AI output;
* validation results;
* reviewer corrections;
* final interpretation;
* review status;
* publication decision;
* follow-up relationships.

## Provenance

Each completed record may generate a provenance manifest containing:

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
* validation result;
* human corrections;
* reviewed-output hash;
* publication state;
* manifest hash.

The purpose is to make the history of a record inspectable rather than presenting the final interpretation without context.

## Privacy

The system separates public evidence from sensitive source information.

Sensitive records may include:

* exact locations of vulnerable species;
* nests or dens;
* identifiable people;
* neighboring-property details;
* private access routes;
* legal or contentious evidence;
* contributor information.

Public records should use generalized locations and reviewed, redacted evidence where necessary.

Permanent storage must not be used for sensitive material without explicit review and approval.

## Benchmark

The project plans to evaluate a curated Rio Madre dataset containing approximately 50 to 100 records.

The benchmark will measure:

* inference success;
* JSON-schema validity;
* latency;
* estimated cost;
* human approval rate;
* correction rate;
* rejection rate;
* hallucinated features;
* classification overreach;
* uncertainty quality;
* sensitivity classification;
* repeatability across multiple jobs.

The benchmark is not intended to demonstrate perfect species identification.

It is intended to identify where decentralized AI is useful, where it fails, and where human judgment remains essential.

## Relationship to Regenerative Agritourism

Long term, Proof of Regeneration may help connect visitor-supported activities with documented land stewardship.

Examples could include:

* field-learning programs;
* native-tree planting;
* agroforestry activities;
* restoration work;
* biodiversity observations;
* watershed monitoring;
* educational visits;
* stewardship residencies.

The system should distinguish clearly between:

* an activity being funded;
* an activity being completed;
* evidence being recorded;
* a follow-up being performed;
* an ecological outcome being verified.

Payment or participation alone does not prove environmental benefit.

## Repository Structure

```text
proof-of-regeneration/
├── README.md
├── LICENSE
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
│   └── deployment-plan.md
└── src/
    └── README.md
```

## Current Status

The project is currently in the planning, schema-design, documentation, and technical-preparation stage.

Current work includes:

* defining the observation workflow;
* documenting the system architecture;
* establishing privacy principles;
* designing the benchmark;
* preparing JSON schemas;
* creating synthetic sample records;
* planning efficient Nosana deployment.

No live Nosana job, deployed model, completed benchmark, or production platform is claimed unless supporting evidence is later added to the repository.

## Long-Term Direction

Proof of Regeneration may eventually support:

* regenerative farms;
* conservation properties;
* ecological reserves;
* watershed projects;
* agritourism operators;
* research partnerships;
* retreat centers;
* community restoration initiatives.

The immediate priority remains a focused, working, and reproducible prototype grounded in Rio Madre’s real field context.
