# Proof of Regeneration — Benchmark Plan

## Purpose

The Proof of Regeneration benchmark will evaluate whether decentralized multimodal inference can support responsible ecological and land-stewardship documentation.

The benchmark is not intended to prove that AI can replace ecological expertise.

It is intended to measure:

* how consistently a model interprets field evidence;
* whether outputs remain grounded in visible evidence;
* whether outputs follow the required structure;
* how often human correction is necessary;
* where the model overstates certainty;
* whether observer notes bias the model;
* how much decentralized inference costs;
* whether repeated jobs produce comparable results;
* whether the system handles privacy and uncertainty responsibly.

Rio Madre in Costa Rica will provide the initial field dataset.

## Core Research Question

**Can decentralized vision-language inference produce ecological and land-stewardship records that are sufficiently structured, cautious, reproducible, and useful for real-world human review?**

## Supporting Questions

The benchmark will also examine:

1. Does a strict evidence-and-uncertainty prompt improve output quality compared with a general prompt?
2. Does adding an observer note improve interpretation or bias the model toward the observer’s assumption?
3. Can the model distinguish visible evidence from contextual claims?
4. Are repeated decentralized jobs materially consistent?
5. Does self-reported confidence correspond to human-review outcomes?
6. What is the effective compute cost per human-approved record?
7. How much reviewer time is required to turn model output into a usable record?

## Benchmark Objectives

The benchmark will assess:

1. Technical reliability
2. Structured-output quality
3. Evidence grounding
4. Ecological interpretation quality
5. Representation of uncertainty
6. Human-review requirements
7. Privacy and sensitivity classification
8. Repeatability across inference runs
9. Runtime and compute cost
10. Operational usefulness

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
| Human-disturbance observations          |           5–10 |
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

## Planned Experiments

## Experiment A — Structured versus Unstructured Prompting

Use the same fixed subset of records with:

### General prompt

A broad ecological-analysis instruction without a strict schema or explicit uncertainty requirements.

### Proof of Regeneration prompt

The structured prompt requiring:

* visible evidence;
* provisional classification;
* alternatives;
* uncertainty;
* review priority;
* location sensitivity;
* follow-up;
* JSON-only output.

Compare:

* valid JSON rate;
* evidence-grounding score;
* hallucinated-feature rate;
* classification overreach;
* uncertainty quality;
* human correction rate;
* follow-up usefulness.

## Experiment B — Input Ablation

For a fixed subset, compare:

### Image only

The model receives the image without the observer note.

### Note only

The model receives the observer note without the image.

### Image plus note

The model receives both.

Measure:

* classification quality;
* evidence grounding;
* confidence;
* uncertainty;
* correction rate;
* contradiction rate;
* observer-note influence.

## Experiment C — Observer-Note Disagreement

Use controlled notes that are:

* broadly correct;
* cautious;
* incomplete;
* incorrectly specific;
* misleading.

Evaluate whether the model:

* challenges the note;
* repeats it without evidence;
* invents confirming features;
* clearly separates image evidence from observer context.

## Experiment D — Repeatability

Select approximately 10 to 20 records.

Process each record multiple times using:

* the same model version;
* the same prompt version;
* the same schema;
* the same inference settings;
* separate Nosana jobs where possible.

Compare:

* classification level;
* visible evidence;
* confidence;
* uncertainty;
* review priority;
* sensitivity classification;
* recommended follow-up.

## Experiment E — Longitudinal Stewardship Record

Test at least one complete sequence:

```text
Baseline condition
        ↓
Documented activity
        ↓
Scheduled follow-up
        ↓
Later evidence
        ↓
Human-reviewed change record
```

Possible examples:

* native-tree planting;
* nursery transfer;
* riverbank vegetation;
* erosion condition;
* agroforestry establishment.

The experiment should demonstrate that activity documentation is not treated as proof of ecological success.

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
2. Remove unnecessary metadata.
3. Assign an anonymized identifier.
4. Generalize or hide sensitive location data.
5. Prepare the original field note.
6. Add curator notes.
7. Assign a primary category.
8. Identify expected uncertainty.
9. Assign a sensitivity level.

### Step 2: Baseline Inference

Process each record using:

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

### Step 5: Review Timing

Record:

* review start time;
* review completion time;
* review duration;
* number of corrected fields;
* correction severity;
* whether expert knowledge was required;
* whether follow-up evidence was requested.

## Technical Metrics

### Inference Success Rate

```text
Successful inference jobs / Total submitted jobs
```

### Schema Validity Rate

```text
Valid first-pass outputs / Total completed outputs
```

### Repair Rate

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

### Estimated Cost per Inference

```text
Total compute cost / Number of completed inferences
```

### Estimated Cost per Approved Record

```text
Total compute cost / Number of human-approved records
```

This metric accounts for failed, rejected, or unusable outputs.

## Evidence-Grounding Metrics

Each visible-evidence statement should be scored:

* `2` — directly visible;
* `1` — plausible but ambiguous;
* `0` — unsupported or invented.

### Evidence-Grounding Score

```text
Total evidence points / Maximum possible evidence points
```

### Hallucinated-Feature Rate

Percentage of outputs containing at least one unsupported visible-evidence claim.

Examples include:

* flowers not visible;
* thorns not visible;
* animal markings not visible;
* water conditions not visible;
* human activity not visible.

## Quality Metrics

### Human Approval Rate

Percentage approved without substantive correction.

### Correction Rate

Percentage approved only after correction.

### Rejection Rate

Percentage judged unsuitable as an ecological or stewardship record.

### Classification Overreach Rate

Percentage assigning a more specific classification than the evidence supports.

### Uncertainty Quality

Rate uncertainty as:

* strong;
* adequate;
* weak;
* misleading.

Review whether the output:

* identifies missing evidence;
* avoids false precision;
* proposes reasonable alternatives;
* recommends meaningful follow-up;
* matches image quality;
* matches classification specificity.

### Follow-Up Usefulness

Rate whether the recommendation would meaningfully improve interpretation.

### Median Review Time

Report the median time required to turn model output into an approved or corrected record.

## Confidence Analysis

Model-generated confidence is not treated as a calibrated probability.

The benchmark will test:

* confidence variation across repeated runs;
* confidence on blurred or incomplete images;
* confidence on incorrect or misleading observer notes;
* confidence for outputs later corrected or rejected;
* correlation between confidence and human-review outcome.

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

Measure range and standard deviation across runs.

### Review-Priority Agreement

Percentage of repeated runs assigning the same review priority.

### Contradiction Rate

Percentage of repeated runs producing materially contradictory interpretations.

## Human Review Outcomes

Use:

* Approved
* Approved with Minor Edits
* Corrected
* Rejected
* Follow-Up Required

## Error Severity

### Low Severity

* awkward wording;
* minor formatting issue;
* slightly excessive caution;
* nonessential omitted detail.

### Medium Severity

* incorrect category;
* unsupported confidence;
* poor follow-up recommendation;
* meaningful hallucination;
* incorrect sensitivity level.

### High Severity

* definitive false species claim;
* invented environmental condition;
* exposure of sensitive location;
* accusation of legal wrongdoing;
* fabricated evidence supporting an environmental claim.

## Compute-Efficiency Plan

Nosana credits should be used in controlled stages:

1. one-image deployment test;
2. small five-record validation batch;
3. prompt and schema refinement;
4. baseline and ablation subset;
5. main benchmark batch;
6. repeatability subset;
7. final demonstration and contingency.

Deployments should use:

* Simple deployment strategy;
* one replica;
* finite container timeout;
* manual shutdown when idle;
* the lowest-cost GPU market capable of running the workload.

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
* median review time;
* hallucination examples;
* evidence-grounding score;
* ablation findings;
* observer-note bias findings;
* repeatability findings;
* privacy failures;
* known limitations.

Results should not be presented only as a success story.

Failures, corrections, and uncertainty are important project findings.

## Success Criteria

The initial benchmark will be considered successful if:

* the full inference workflow is reproducible;
* most outputs are valid structured JSON;
* costs and latency are documented;
* human corrections are measured;
* review time is measured;
* hallucinations are identified honestly;
* repeated runs can be compared;
* observer-note bias is tested;
* privacy-sensitive records are handled cautiously;
* the results provide useful guidance for future development.

The benchmark does not require perfect ecological identification.

Its purpose is to determine where decentralized AI is useful, where it is unreliable, and where human judgment remains essential.

## Current Status

This document defines the planned benchmark methodology.

No benchmark results are claimed until corresponding data, scripts, job records, and review outputs are added to the repository.
