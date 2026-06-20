# Proof of Regeneration

An open-source land-accountability system for creating verifiable, human-reviewed records of ecological stewardship and regenerative land activity using decentralized AI infrastructure.

Built for regenerative farms, conservation properties, retreat centers, and agritourism operators seeking to show what was funded, what happened on the land, what evidence exists, and what changed over time.

**First intended field deployment:** [Rio Madre](https://riomadre.com), Costa Rica

## Central Research Question

**Can decentralized multimodal inference produce ecological and land-stewardship records that are structured, reproducible, cautious, and useful enough for real-world human review?**

The project does not assume that decentralized AI is automatically more accurate, private, or trustworthy.

Instead, it tests whether decentralized infrastructure can support:

* portable containerized workloads;
* reproducible deployment records;
* transparent cost and runtime measurement;
* repeatable inference experiments;
* structured model outputs;
* preserved human corrections;
* auditable provenance.

## Core Thesis

The useful output of conservation AI is not merely an identification.

It is a reviewable evidence chain.

Most image-analysis systems optimize for:

```text
Image
    ↓
Answer
```

Proof of Regeneration is designed around:

```text
Field evidence
        ↓
Provisional interpretation
        ↓
Explicit uncertainty
        ↓
Human correction
        ↓
Provenance record
        ↓
Follow-up evidence
```

The system is intended to preserve not only the final interpretation, but also how that interpretation was produced, reviewed, corrected, and later updated.

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

Rio Madre, a seven-hectare conservation and agritourism landscape in Costa Rica, will serve as the first real-world test site.

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

AI may help organize field evidence, but it may also:

* hallucinate visible features;
* overstate confidence;
* confuse similar species;
* repeat an observer’s mistaken assumption;
* expose sensitive locations;
* produce inconsistent results;
* generate valid-looking but unsupported conclusions.

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

## Planned Experiments

The project will not evaluate Nosana inference in isolation.

The benchmark will include controlled comparisons designed to determine whether the workflow itself improves record quality.

### Structured versus unstructured prompting

The same field records will be tested with:

1. a general ecological-analysis prompt;
2. the Proof of Regeneration evidence-and-uncertainty prompt.

The comparison will measure:

* valid JSON rate;
* evidence-grounding quality;
* hallucinated-feature rate;
* classification overreach;
* uncertainty quality;
* human correction rate;
* usefulness of follow-up recommendations.

### Image and note ablation

A fixed subset will be tested using:

1. image only;
2. observer note only;
3. image plus observer note.

This experiment will assess whether field notes improve interpretation or bias the model toward the observer’s assumption.

### Observer-note disagreement

Controlled records will include notes that are:

* broadly correct;
* tentative;
* incomplete;
* misleading;
* incorrectly specific.

The system will be evaluated on whether it separates visible evidence from observer interpretation or invents evidence that confirms the note.

### Repeatability testing

Identical inputs will be processed across repeated Nosana jobs.

The project will compare:

* classification level;
* visible-evidence statements;
* confidence;
* uncertainty;
* human-review priority;
* location sensitivity;
* recommended follow-up.

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

## Confidence Scores

Model-generated confidence is treated as a comparative output signal, not as a statistically calibrated probability.

A value such as `0.80` does not mean that the identification has an independently verified 80 percent probability of being correct.

The benchmark will test:

* whether confidence decreases for low-quality or incomplete images;
* whether confidence remains stable across repeated runs;
* whether high-confidence outputs still require correction;
* whether observer notes create unjustified confidence;
* whether confidence correlates with human-review outcomes.

## Evidence Grounding

Each model-generated visible-evidence statement may be reviewed using the following scale:

* `2` — directly visible;
* `1` — plausible but ambiguous;
* `0` — unsupported or invented.

The resulting evidence-grounding score will help distinguish outputs that merely sound credible from outputs that remain tied to the actual field evidence.

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

### What provenance can establish

A provenance record may help establish that:

* a specific file or record existed in a particular form;
* a displayed output corresponds to a stored hash;
* a model, prompt, and container version were recorded;
* a human correction was preserved;
* a record changed between versions.

### What provenance cannot establish by itself

A hash or manifest does not prove that:

* the photograph was taken where claimed;
* the timestamp is authentic;
* the field note is truthful;
* the subject was identified correctly;
* an ecological outcome occurred;
* a contributor had authority to make every claim.

Proof of Regeneration distinguishes between:

* integrity verification;
* human review;
* scientific validation;
* field authenticity.

These are related but not equivalent.

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
* estimated cost per inference;
* estimated cost per approved record;
* human approval rate;
* correction rate;
* rejection rate;
* review time;
* hallucinated-feature rate;
* evidence-grounding score;
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

## Longitudinal Stewardship Records

Proof of Regeneration is designed to document change over time rather than isolated events.

A complete stewardship sequence may include:

```text
Baseline condition
        ↓
Activity record
        ↓
Scheduled follow-up
        ↓
Later field evidence
        ↓
Human-reviewed change record
```

For example, a tree-planting image may establish that planting activity occurred.

It does not prove:

* survival;
* restoration success;
* carbon benefit;
* habitat improvement;
* biodiversity gain.

Those claims require later evidence.

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
* evidence grounding;
* privacy protection;
* preserved correction history;
* reproducible infrastructure;
* efficient compute use;
* transparent reporting of failures;
* activity evidence separate from outcome claims;
* technology in service of land and stewardship.

## License

This project is released under the MIT License.
