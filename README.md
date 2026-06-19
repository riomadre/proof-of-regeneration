# Proof of Regeneration

Decentralized AI infrastructure for verifiable ecological stewardship, regenerative land use and agritourism.

**First deployment site:** [Rio Madre](https://riomadre.com)

## Overview

Proof of Regeneration is an open-source system for documenting and verifying ecological observations, restoration activities and regenerative land-management outcomes.

The first physical deployment is being developed at Rio Madre, a seven-hectare conservation and agritourism property in Costa Rica.

The project combines:

- decentralized AI inference;
- original ecological field observations;
- human verification;
- transparent provenance records;
- restoration monitoring;
- regenerative tourism;
- stewardship and conservation finance.

## The Problem

Ecological and regenerative projects frequently make claims about biodiversity, restoration, tree planting, community benefit and environmental impact without maintaining consistent, verifiable evidence.

AI can assist with field documentation, but AI-generated classifications may be uncertain or incorrect. Centralized systems can also control the data, models and continued access to the records.

Proof of Regeneration is designed to create portable, human-verifiable environmental records while allowing land stewards to maintain control of their data.

## Initial Rio Madre Use Case

A land steward, researcher, visitor or field worker submits:

1. A field photograph
2. An observation note
3. A date and approximate location
4. The type of activity or ecological condition being documented

A vision-language model deployed through Nosana analyzes the submission and returns structured information such as:

- observation category;
- provisional species or environmental classification;
- visible supporting evidence;
- alternative interpretations;
- confidence and uncertainty;
- recommended human-review level;
- privacy sensitivity;
- recommended follow-up observation.

The AI output is not treated as final evidence. A human reviewer accepts, corrects or rejects the result.

## Proof Record

Each verified record may contain:

- source image hash;
- original field note;
- observation date;
- approximate or protected location;
- model name and version;
- container version;
- prompt version;
- AI-generated result;
- human correction;
- verification status;
- timestamps;
- follow-up observations.

Sensitive biodiversity locations, personal information and legally sensitive photographs will not be published without appropriate review and redaction.

## Regenerative Agritourism

The long-term system will connect ecological evidence with visitor-supported stewardship.

Potential uses include documenting:

- native-tree planting;
- agroforestry activities;
- habitat restoration;
- biodiversity observations;
- river and watershed monitoring;
- environmental education;
- local employment;
- guest-funded stewardship projects;
- follow-up survival and restoration outcomes.

This creates a transparent record showing what was funded, what occurred on the land and what evidence exists afterward.

## Nosana Workload

The initial prototype will run a containerized open-source vision-language model through Nosana.

The workload will accept an image and field note and return schema-constrained JSON.

Testing will evaluate:

- inference latency;
- cost per observation;
- output consistency;
- structured-output validity;
- hallucinated visual claims;
- human-correction rate;
- reproducibility across repeated jobs.

## Project Status

Early-stage prototype and competition submission.

Current work includes:

- defining the observation schema;
- curating an anonymized Rio Madre test dataset;
- selecting a multimodal model;
- preparing the Nosana workload;
- developing the verification workflow;
- designing the provenance manifest.

## Repository Structure

```text
proof-of-regeneration/
├── README.md
├── LICENSE
├── docs/
├── sample-data/
├── schemas/
├── src/
└── nosana/
