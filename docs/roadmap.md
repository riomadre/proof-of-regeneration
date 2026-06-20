# Proof of Regeneration — Development Roadmap

## Project Goal

Proof of Regeneration is an open-source system for creating verifiable, human-reviewed records of ecological observations, restoration activity, regenerative land use, and future visitor-supported stewardship.

Rio Madre in Costa Rica will serve as the first real-world test site.

The project is being developed for the Decentralize AI hackathon, with decentralized multimodal inference planned through Nosana.

## Development Principles

Every feature should meet at least one of these goals:

1. Strengthen the technical hackathon submission
2. Serve a real operational need at Rio Madre
3. Create future value for other regenerative land projects

The project will prioritize:

* working code over speculative features;
* human verification over automated certainty;
* transparent uncertainty;
* privacy protection;
* reproducible infrastructure;
* careful use of limited compute credits;
* measurable outcomes;
* open documentation.

## Phase 0 — Project Foundation

Status: In progress

Objectives:

* define the project scope;
* establish the public repository;
* document the Rio Madre use case;
* define privacy and ethical principles;
* identify initial field records;
* draft observation and provenance schemas;
* prepare for Nosana access.

Deliverables:

* project README;
* development roadmap;
* architecture document;
* privacy and ethics document;
* benchmark plan;
* initial data schemas;
* anonymized sample record.

## Phase 1 — Local Prototype

Objective:

Build the core workflow locally before using Nosana compute credits.

Planned features:

* create a field observation;
* upload or reference an image;
* add a field note;
* assign an observation category;
* generate a mock structured AI response;
* review, edit, approve, or reject the response;
* preserve the original output and human-reviewed output;
* generate a provenance manifest;
* display the completed record.

Success criteria:

* the full observation workflow works locally;
* structured outputs pass schema validation;
* human corrections are preserved;
* sensitive fields can be hidden or excluded.

## Phase 2 — First Nosana Workload

Objective:

Run the first real multimodal inference job through Nosana.

Initial test:

* submit one approved Rio Madre field image;
* include a short observer note;
* receive structured JSON from an open vision-language model;
* record the Nosana job identifier;
* record model and container details;
* record inference latency and estimated cost;
* stop the deployment after testing.

Success criteria:

* one complete Nosana inference is successfully returned;
* the result matches the observation schema;
* deployment and shutdown steps are documented;
* no sensitive information is exposed.

## Phase 3 — Working MVP

Objective:

Connect the complete system.

Target workflow:

```text
Field observation
        ↓
Image and note submission
        ↓
Nosana inference
        ↓
Schema validation
        ↓
Human review
        ↓
Provenance manifest
        ↓
Completed observation record
```

Required features:

* observation submission interface;
* Nosana inference adapter;
* structured JSON output;
* human review workflow;
* correction history;
* hashing of source evidence and outputs;
* provenance manifest generation;
* public/private publication status;
* completed record page.

Success criteria:

* a user can complete the full workflow without manually editing files;
* original AI output and reviewed output are both retained;
* every completed record includes provenance metadata.

## Phase 4 — Rio Madre Benchmark

Objective:

Evaluate the system using a curated Rio Madre dataset.

Target dataset:

* 50 to 100 field records;
* plants and fungi;
* wildlife and tracks;
* watershed and landscape conditions;
* restoration and agroforestry activities;
* human disturbance observations;
* difficult or uncertain control cases.

Planned metrics:

* inference latency;
* estimated cost per record;
* JSON-schema validity;
* failed-job rate;
* human approval rate;
* correction rate;
* rejection rate;
* hallucinated-feature rate;
* uncertainty quality;
* privacy-risk classification;
* species-level overclaim rate.

Success criteria:

* benchmark records are processed consistently;
* results are reviewed by a human;
* strengths and failures are documented;
* cost and performance are reported transparently.

## Phase 5 — Repeatability Testing

Objective:

Test whether repeated decentralized inference jobs produce stable results.

Method:

* select a fixed subset of benchmark images;
* process each image multiple times;
* compare classifications;
* compare visible evidence statements;
* compare confidence and uncertainty;
* identify contradictory or hallucinated outputs;
* record job-level performance.

Success criteria:

* repeatability metrics are published;
* disagreement patterns are documented;
* the system clearly shows where human review remains necessary.

## Phase 6 — Regeneration Activity Records

Objective:

Expand beyond species and ecological observations.

Planned record types:

* native-tree planting;
* restoration work;
* agroforestry activity;
* habitat monitoring;
* erosion and river observations;
* educational field activity;
* visitor-supported stewardship.

Each activity may include:

* baseline evidence;
* action taken;
* responsible party;
* date;
* generalized location;
* funding or program reference;
* follow-up schedule;
* later evidence;
* final status.

Success criteria:

* activities can be linked to later observations;
* the system can show change over time;
* claims remain evidence-based and human-reviewed.

## Phase 7 — Public Demonstration

Objective:

Create a clear public-facing demonstration of the system.

Planned elements:

* selected observation gallery;
* completed record pages;
* generalized map or landscape zones;
* restoration timelines;
* provenance details;
* benchmark dashboard;
* privacy explanation;
* Nosana deployment documentation.

The public demonstration must not expose:

* exact vulnerable-species locations;
* personal information;
* legal allegations;
* sensitive neighboring-property details;
* private source files;
* credentials or API keys.

## Phase 8 — Hackathon Submission

Required outputs:

* public GitHub repository;
* working prototype;
* documented Nosana workload;
* reproducible deployment instructions;
* benchmark results;
* architecture documentation;
* privacy and ethics documentation;
* public demonstration;
* technical article describing the build and results.

The submission should clearly explain:

1. the real-world problem;
2. why Rio Madre is the first test site;
3. why decentralized inference is useful;
4. how human review works;
5. how provenance is preserved;
6. what the benchmark revealed;
7. where the system failed;
8. how the project could extend to other land stewards.

## Future Development

After the hackathon, possible development may include:

* additional pilot properties;
* institutional research partnerships;
* private and public project dashboards;
* visitor-supported stewardship records;
* restoration reporting;
* permanent storage for approved non-sensitive manifests;
* white-label deployments;
* subscription tools for regenerative land projects.

These features are future possibilities and are not part of the current working prototype unless explicitly implemented and documented.

## Current Status

The project is currently in the planning, schema-design, data-curation, and technical preparation stage.

No live Nosana deployment is currently claimed in this repository unless deployment evidence is added later.
