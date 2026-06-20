# Proof of Regeneration — Benchmark Plan

## Purpose

The Proof of Regeneration benchmark will evaluate whether decentralized multimodal inference can support responsible ecological and land-stewardship documentation.

The benchmark is not intended to prove that AI can replace ecological expertise.

It is intended to measure:

* how consistently a model interprets field evidence;
* whether outputs follow the required structure;
* how often human correction is necessary;
* where the model overstates certainty;
* how much decentralized inference costs;
* whether repeated jobs produce comparable results;
* whether the system handles privacy and uncertainty responsibly.

Rio Madre in Costa Rica will provide the initial field dataset.

## Core Research Question

Can decentralized vision-language inference produce sufficiently structured, cautious, reproducible, and auditable records to assist community conservation, regenerative agriculture, and land stewardship?

## Benchmark Objectives

The benchmark will assess:

1. Technical reliability
2. Structured-output quality
3. Ecological interpretation quality
4. Representation of uncertainty
5. Human-review requirements
6. Privacy and sensitivity classification
7. Repeatability across inference runs
8. Runtime and compute cost

## Dataset Scope

The initial benchmark should contain approximately 50 to 100 curated Rio Madre records.

The final number will depend on:

* image quality;
* contributor rights;
* ecological sensitivity;
* time available for human review;
* available Nosana compute credits.

## Proposed Dataset Distribution

| Category                                | Target Records |
| --------------------------------------- | -------------: |
| Plants and fungi                        |          20–30 |
| Wildlife, tracks, and signs             |          10–20 |
| Watershed and landscape conditions      |          10–15 |
| Restoration and agroforestry activities |          10–20 |
| Human disturbance observations          |           5–10 |
| Difficult, ambiguous, or control cases  |          10–15 |

A single record may belong to more than one category, but the primary benchmark category should be identified clearly.

## Record Requirements

Each benchmark record should include:

* anonymized record identifier;
* authorized field image;
* observation date;
* generalized location;
* original field note;
* primary category;
* curator notes;
* known uncertainty;
* sensitivity level;
* expected review concerns;
* publication status;
* human-reviewed final interpretation.

Optional fields may include:

* weather context;
* habitat type;
* seasonal context;
* follow-up evidence;
* related restoration activity.

## Dataset Exclusions

Do not include public benchmark records containing:

* exact locations of vulnerable species;
* identifiable neighboring-property details;
* faces without consent;
* vehicle plates;
* personal contact information;
* private legal records;
* confidential access information;
* unsupported accusations;
* images without clear rights for project use.

Sensitive records may be tested privately if appropriate, but they must not be included in the public dataset.

## Benchmark Categories

### 1. Flora and Fungi

Examples:

* emerging fern;
* juvenile pioneer plant;
* possible Mimosa species;
* fungi on decaying wood;
* leaf damage;
* flowering or fruiting plants;
* unresolved understory vegetation.

The model should describe visible evidence and avoid unjustified species-level certainty.

### 2. Wildlife and Signs

Examples:

* mammals;
* birds;
* reptiles;
* amphibians;
* tracks;
* droppings;
* feeding evidence;
* nests or dens;
* partially visible animals.

Exact locations may require restriction.

The model should distinguish between:

* directly visible animal;
* indirect wildlife sign;
* uncertain interpretation.

### 3. Watershed and Landscape Conditions

Examples:

* river level;
* flooding;
* sediment;
* erosion;
* exposed soil;
* fallen trees;
* seasonal dryness;
* bank condition;
* water movement.

The model should describe visible conditions without inferring unsupported causes.

### 4. Restoration and Agroforestry

Examples:

* tree planting;
* mulching;
* nursery transfer;
* shade establishment;
* soil work;
* native regeneration;
* invasive vegetation management;
* follow-up survival observations.

The benchmark should distinguish between an activity being documented and a successful ecological outcome.

### 5. Human Disturbance

Examples:

* cleared vegetation;
* visible burn evidence;
* earth movement;
* altered drainage;
* construction activity;
* raised riverbank;
* exposed sediment.

The model must not determine:

* legality;
* ownership;
* responsibility;
* intent;
* regulatory compliance.

These records should receive elevated human-review priority.

### 6. Difficult and Control Cases

Examples:

* blurred images;
* low light;
* partial subjects;
* multiple possible species;
* non-ecological objects;
* duplicated images;
* insufficient evidence;
* intentionally ambiguous records.

These cases will test whether the model admits uncertainty rather than fabricating detail.

## Model Output Requirements

Each inference should return schema-constrained JSON containing fields such as:

* record type;
* observation category;
* provisional classification;
* visible evidence;
* alternative interpretations;
* confidence;
* uncertainty;
* human-review priority;
* location sensitivity;
* recommended follow-up.

The model should not be rewarded merely for producing a classification.

It should also be evaluated on whether it:

* cites only visible evidence;
* identifies limitations;
* avoids invented features;
* selects an appropriate review level;
* recommends useful follow-up.

## Benchmark Procedure

### Step 1: Dataset Preparation

For each record:

1. Confirm image-use authorization.
2. remove unnecessary metadata;
3. assign an anonymized identifier;
4. generalize or hide sensitive location data;
5. prepare the original field note;
6. add curator notes;
7. assign a primary category;
8. identify expected uncertainty;
9. assign a sensitivity level.

### Step 2: Baseline Inference

Process each record once using:

* the selected model;
* a fixed prompt version;
* a fixed output schema;
* documented inference parameters;
* a documented Nosana workload.

Record:

* job identifier;
* start time;
* completion time;
* runtime;
* model version;
* container details;
* estimated compute cost;
* raw output;
* validation status.

### Step 3: Schema Validation

Check whether the output:

* is valid JSON;
* contains all required fields;
* uses allowed values;
* keeps confidence within the valid range;
* stays within output limits;
* excludes unsupported fields.

Invalid outputs should be retained for analysis.

### Step 4: Human Review

A reviewer should assess:

* whether the category is appropriate;
* whether the classification is supportable;
* whether visible evidence is accurately described;
* whether any evidence was hallucinated;
* whether uncertainty is adequate;
* whether privacy sensitivity is correct;
* whether follow-up advice is useful;
* whether the record can be approved, corrected, or rejected.

### Step 5: Repeatability Testing

Select a representative subset of approximately 10 to 20 records.

Each selected record should be processed multiple times under the same documented settings.

Where possible, repeatability testing should include:

* separate Nosana jobs;
* identical prompt version;
* identical model version;
* identical inference settings;
* the same input bundle.

Compare:

* provisional classification;
* visible evidence statements;
* alternative interpretations;
* confidence;
* uncertainty;
* review priority;
* sensitivity classification;
* recommended follow-up.

## Technical Metrics

### Inference Success Rate

Percentage of submitted jobs that return a usable response.

```text
Successful inference jobs / Total submitted jobs
```

### Schema Validity Rate

Percentage of outputs that pass schema validation without repair.

```text
Valid first-pass outputs / Total completed outputs
```

### Repair Rate

Percentage of outputs requiring a repair prompt or parsing intervention.

```text
Repaired outputs / Total completed outputs
```

### Failure Rate

Percentage of jobs that fail because of:

* deployment error;
* timeout;
* model error;
* invalid response;
* infrastructure issue.

### Latency

Record:

* deployment startup time where applicable;
* inference runtime;
* total request-to-result time.

Report:

* average;
* median;
* minimum;
* maximum.

### Estimated Cost Per Record

```text
Total compute cost / Number of completed records
```

Costs should be reported transparently and identified as estimates where exact billing attribution is unavailable.

## Quality Metrics

### Human Approval Rate

Percentage of outputs approved without substantive correction.

### Correction Rate

Percentage approved only after human correction.

### Rejection Rate

Percentage judged unsuitable as an ecological or stewardship record.

### Hallucinated-Feature Rate

Percentage of outputs claiming visible evidence not supported by the image.

Examples include:

* flowers not visible;
* thorns not visible;
* animal markings not visible;
* water conditions not visible;
* human activity not visible.

### Classification Overreach Rate

Percentage of outputs giving a more specific classification than the evidence reasonably supports.

Example:

* assigning a species where only genus or family-level interpretation is justified.

### Uncertainty Adequacy

Assess whether uncertainty language is:

* adequate;
* insufficient;
* excessive;
* missing.

### Follow-Up Usefulness

Assess whether the recommended follow-up would meaningfully improve interpretation.

Examples:

* photograph flowers;
* capture leaf underside;
* record scale;
* photograph tracks from directly above;
* repeat after rainfall;
* perform a survival check.

## Privacy and Safety Metrics

### Sensitivity Classification Accuracy

Measure whether the model correctly identifies records that should be:

* public;
* restricted;
* private;
* escalated for review.

### Location-Risk Detection

Evaluate whether the system recognizes records involving:

* nests;
* dens;
* vulnerable species;
* access routes;
* neighboring-property details.

### Legal-Conclusion Avoidance

Measure whether the model avoids unsupported claims about:

* illegality;
* ownership;
* responsibility;
* intent;
* environmental liability.

Any automated legal accusation should be treated as a serious failure.

## Repeatability Metrics

### Classification Agreement

Percentage of repeated runs producing the same primary classification level.

### Evidence Agreement

Degree to which repeated runs identify the same visible features.

### Confidence Variation

Measure the range and standard deviation of confidence values across repeated runs.

### Review-Priority Agreement

Percentage of repeated runs assigning the same human-review priority.

### Contradiction Rate

Percentage of repeated runs producing materially contradictory interpretations.

## Human Review Scale

Reviewers may use the following outcome labels:

### Approved

The output is suitable with no substantive correction.

### Approved with Minor Edits

The interpretation is generally sound but requires wording, formatting, or caution adjustments.

### Corrected

The output contains meaningful classification, evidence, uncertainty, or privacy errors that require revision.

### Rejected

The output is unsuitable or misleading.

### Follow-Up Required

The available evidence is insufficient and further observation is necessary.

## Severity of Model Errors

### Low Severity

* awkward wording;
* minor formatting issue;
* slightly excessive caution;
* nonessential omitted detail.

### Medium Severity

* incorrect category;
* unsupported confidence;
* poor follow-up recommendation;
* meaningful but noncritical hallucination;
* incorrect sensitivity level.

### High Severity

* definitive false species claim;
* invented environmental condition;
* exposure of sensitive location;
* accusation of legal wrongdoing;
* identification of an uninvolved person;
* fabricated evidence supporting an environmental claim.

## Prompt and Model Comparison

If compute credits permit, compare a limited number of:

* prompt versions;
* output-schema strategies;
* model sizes;
* inference settings.

Do not spend credits on broad model comparison before the complete workflow functions.

Each comparison should use the same fixed subset of records.

## Compute-Efficiency Plan

Nosana credits should be used in controlled stages:

1. one-image deployment test;
2. small five-record validation batch;
3. prompt and schema refinement;
4. main benchmark batch;
5. repeatability subset;
6. final demonstration and contingency.

Deployments should use:

* Simple deployment strategy;
* one replica;
* finite container timeout;
* manual shutdown when idle;
* the lowest-cost GPU market capable of running the selected workload.

## Reporting Results

Benchmark results should include:

* dataset composition;
* model and prompt details;
* schema version;
* Nosana workload configuration;
* number of jobs;
* successful and failed jobs;
* compute usage;
* latency;
* cost estimates;
* validation rate;
* human-review outcomes;
* hallucination examples;
* repeatability findings;
* privacy failures;
* known limitations.

Results should not be presented only as a success story.

Failures, corrections, and uncertainty are important project findings.

## Public Benchmark Materials

The public repository may include:

* anonymized structured records;
* redacted example images where authorized;
* schema files;
* benchmark scripts;
* aggregate results;
* selected failed outputs;
* review methodology;
* reproducibility instructions.

Do not publicly include sensitive source evidence.

## Success Criteria

The initial benchmark will be considered successful if:

* the full inference workflow is reproducible;
* most outputs are valid structured JSON;
* costs and latency are documented;
* human corrections are measured;
* hallucinations are identified honestly;
* repeated runs can be compared;
* privacy-sensitive records are handled cautiously;
* the results provide useful guidance for future development.

The benchmark does not require perfect ecological identification.

Its purpose is to determine where decentralized AI is useful, where it is unreliable, and where human judgment remains essential.

## Current Status

This document defines the planned benchmark methodology.

No benchmark results are claimed until corresponding data, scripts, job records, and review outputs are added to the repository.
