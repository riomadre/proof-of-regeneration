# Proof of Regeneration — Threat Model

## Purpose

This document identifies foreseeable technical, ecological, evidentiary, privacy, and governance risks affecting Proof of Regeneration.

The purpose of the threat model is not to claim that every risk has already been solved.

It is intended to:

* guide prototype design;
* inform testing;
* prevent misleading environmental claims;
* protect sensitive ecological information;
* distinguish data integrity from factual truth;
* define which failures require human escalation.

## System Context

Proof of Regeneration is intended to create structured, human-reviewed records from:

* field photographs;
* observer notes;
* dates and generalized locations;
* ecological or stewardship categories;
* decentralized multimodal inference;
* human corrections;
* provenance manifests;
* follow-up observations.

The system may eventually be used by:

* conservation properties;
* regenerative farms;
* agritourism operators;
* retreat centers;
* researchers;
* land stewards;
* educational programs;
* restoration partners.

## Protected Assets

The system should protect:

### Ecological information

* exact locations of vulnerable species;
* nests and dens;
* breeding sites;
* rare plants;
* wildlife movement routes;
* sensitive habitats.

### Source evidence

* original photographs;
* field notes;
* timestamps;
* private coordinates;
* environmental records;
* restoration documentation.

### Personal information

* contributor identities;
* reviewer identities;
* faces;
* contact information;
* private correspondence;
* access information.

### Record integrity

* original AI output;
* human corrections;
* review history;
* publication status;
* provenance hashes;
* follow-up relationships.

### System credentials

* Nosana credentials;
* storage credentials;
* database credentials;
* signing keys;
* API tokens.

### Project credibility

* accuracy of public claims;
* transparent limitations;
* separation of activity from outcome;
* honest reporting of model failures.

## Trust Boundaries

The system contains several distinct trust boundaries:

1. Between the field event and the submitted evidence
2. Between the contributor and the application
3. Between private storage and public records
4. Between the application and the inference provider
5. Between model output and human review
6. Between reviewed records and public publication
7. Between current records and permanent storage
8. Between recorded integrity and ecological truth

Crossing any boundary may introduce error, manipulation, or information exposure.

## Threat Actors

Potential threat actors include:

### Accidental contributor

A well-intentioned user who:

* submits incorrect notes;
* exposes sensitive coordinates;
* uploads the wrong image;
* misunderstands an ecological condition;
* overstates an outcome.

### Careless reviewer

A reviewer who:

* approves an unsupported interpretation;
* overlooks sensitive details;
* publishes exact locations;
* fails to document corrections.

### Malicious contributor

A person who intentionally submits:

* altered photographs;
* misleading descriptions;
* duplicated evidence;
* false timestamps;
* false restoration claims;
* evidence from another property.

### External attacker

A person attempting to:

* steal credentials;
* access private records;
* alter public records;
* replace evidence;
* manipulate publication settings;
* obtain sensitive ecological locations.

### Misaligned project operator

An operator who may use the system to:

* exaggerate environmental benefits;
* publish selective evidence;
* hide failed activities;
* present funded activity as completed work;
* present completed work as verified ecological success.

### Model or infrastructure failure

A non-human failure source including:

* hallucinated model output;
* inconsistent inference;
* incorrect model version;
* unavailable container;
* failed job;
* compromised dependency;
* output truncation;
* data leakage through logs.

## Threat Categories

## 1. False Field Evidence

### Threat

A photograph may not represent the claimed:

* location;
* time;
* activity;
* property;
* ecological condition.

A valid hash proves file integrity after hashing, not field authenticity.

### Possible controls

* preserve original metadata privately where appropriate;
* record contributor identity or contributor class;
* allow reviewer attestation;
* link related records over time;
* flag externally supplied evidence;
* require multiple images for higher-risk claims;
* record whether location or time was independently verified;
* avoid calling source evidence “verified” without qualification.

### Residual limitation

The prototype may not be able to independently prove where or when an image was captured.

## 2. Altered or Synthetic Images

### Threat

A contributor may submit:

* edited photographs;
* composites;
* screenshots;
* AI-generated images;
* images with removed context.

### Possible controls

* preserve the submitted file hash;
* record file type and metadata status;
* inspect images manually;
* require source-file declarations;
* flag suspicious or inconsistent images;
* retain publication authority with a human reviewer;
* add future authenticity tooling only when technically justified.

### Residual limitation

Image-forensics tooling cannot guarantee authenticity.

## 3. Misleading Observer Notes

### Threat

The observer note may contain:

* incorrect identification;
* causal assumptions;
* legal conclusions;
* exaggerated impact;
* leading language that biases the model.

### Possible controls

* separate observer note from visible-evidence output;
* test image-only, note-only, and image-plus-note conditions;
* flag disagreement between image and note;
* preserve the original note;
* require the model to describe visible evidence separately;
* measure observer-note influence in the benchmark.

## 4. Model Hallucination

### Threat

The model may invent:

* flowers;
* fruit;
* thorns;
* animal markings;
* water conditions;
* erosion;
* smoke;
* machinery;
* restoration activity;
* legal or causal explanations.

### Possible controls

* strict structured prompting;
* evidence-grounding review;
* human approval;
* hallucination metrics;
* difficult control cases;
* preserved raw output;
* explicit uncertainty requirements;
* rejection of unsupported records.

## 5. Classification Overreach

### Threat

The model may provide species-level or causal certainty unsupported by the available evidence.

### Possible controls

* classification-level field;
* preference for broader categories;
* explicit unresolved option;
* human correction;
* overreach metrics;
* follow-up recommendations;
* expert review for sensitive or consequential records.

## 6. Misleading Confidence

### Threat

A self-reported confidence score may appear scientifically calibrated when it is not.

### Possible controls

* label confidence as a model-generated comparative signal;
* never present it as a verified probability;
* compare confidence with human-review outcomes;
* measure variation across repeated runs;
* avoid using confidence alone to automate publication.

## 7. Sensitive-Location Exposure

### Threat

A record may expose:

* nests;
* dens;
* rare species;
* vulnerable plants;
* private trails;
* access routes;
* neighboring-property details.

Exposure may occur through:

* visible coordinates;
* image metadata;
* filenames;
* observer notes;
* model output;
* public maps;
* logs.

### Possible controls

* private coordinates by default;
* generalized public zones;
* metadata removal;
* sensitivity review;
* redacted public records;
* no public map for critical records;
* explicit publication approval.

## 8. Personal-Data Exposure

### Threat

Photographs or notes may contain:

* faces;
* names;
* license plates;
* phone numbers;
* email addresses;
* private conversations;
* identifying property details.

### Possible controls

* pre-publication review;
* redaction;
* private storage;
* minimum necessary data;
* restricted records;
* consent requirements;
* no public contributor identity by default.

## 9. Unsupported Legal or Responsibility Claims

### Threat

The model or contributor may imply:

* illegality;
* ownership;
* responsibility;
* intent;
* negligence;
* environmental liability.

### Possible controls

* legal-claim warning field;
* elevated review priority;
* factual visible-condition language;
* private status by default for contentious records;
* prohibit automated blame assignment;
* require legal review before consequential publication.

## 10. Activity Presented as Outcome

### Threat

A project may present:

* tree planting as tree survival;
* payment as restoration;
* participation as biodiversity gain;
* one photograph as long-term success;
* a completed task as a verified ecological outcome.

### Possible controls

* separate activity and outcome record types;
* require follow-up records;
* preserve baseline conditions;
* use longitudinal records;
* prohibit unsupported success language;
* show status such as `activity_documented`, `follow_up_pending`, or `outcome_unresolved`.

## 11. Duplicate or Reused Evidence

### Threat

The same photograph may be reused for:

* multiple activities;
* multiple sponsors;
* multiple properties;
* repeated environmental claims.

### Possible controls

* image hashes;
* duplicate detection;
* related-record checks;
* audit events;
* reviewer warnings;
* public disclosure of linked evidence where appropriate.

### Residual limitation

A visually modified copy may evade simple hash matching.

## 12. Record Tampering

### Threat

A person may alter:

* model output;
* corrections;
* review status;
* publication state;
* timestamps;
* follow-up links.

### Possible controls

* immutable audit events where practical;
* deterministic record hashing;
* version history;
* reviewer identity;
* signed manifests in later versions;
* separate original and reviewed outputs;
* restricted administrative permissions.

## 13. Provenance Overstatement

### Threat

Users may assume that a hash or manifest proves the ecological claim is true.

### Required distinction

Provenance may support:

* integrity verification;
* version comparison;
* record linkage;
* model and prompt traceability.

It does not independently prove:

* field authenticity;
* scientific correctness;
* contributor honesty;
* ecological outcome;
* legal compliance.

Public interfaces must communicate this distinction.

## 14. Nosana Job or Container Risk

### Threat

A workload may:

* use the wrong model;
* run an altered container;
* expose inputs in logs;
* fail midway;
* return truncated output;
* consume excessive credits;
* use an unverified dependency.

### Possible controls

* record container image and digest;
* record model version;
* preserve job identifier;
* use approved low-sensitivity inputs initially;
* use finite timeouts;
* stop idle deployments;
* inspect logs before using sensitive records;
* pin dependencies where practical;
* validate every returned output.

## 15. Credential Exposure

### Threat

Secrets may be committed to GitHub, included in logs, or placed in public job definitions.

### Possible controls

* `.env.example` with placeholders only;
* environment variables;
* secret-management systems;
* repository scanning;
* credential rotation;
* least-privilege access;
* no secrets inside sample records.

## 16. Permanent-Storage Error

### Threat

Sensitive or incorrect information may be permanently published.

### Possible controls

* permanent storage disabled by default;
* separate explicit approval;
* public-record review;
* redaction before storage;
* hash-only publication where appropriate;
* prohibition on permanent storage for contentious evidence;
* documented reviewer identity.

### Residual limitation

Permanent publication may not be practically reversible.

## 17. Selective Reporting

### Threat

An operator may publish successes while hiding:

* failed plantings;
* rejected AI outputs;
* unsuccessful restoration;
* model errors;
* missing follow-ups.

### Possible controls

* benchmark reporting requirements;
* audit history;
* follow-up status;
* aggregate success and failure metrics;
* documented exclusions;
* transparent methodology;
* publication of representative failure cases.

## 18. Reviewer Conflict of Interest

### Threat

The reviewer may be the same person responsible for the activity or claim.

### Possible controls

* record reviewer role;
* disclose self-review;
* require independent review for high-impact claims;
* distinguish operational approval from scientific validation;
* allow external expert review later.

## 19. Data Loss or Service Failure

### Threat

Private images, records, or audit history may become unavailable.

### Possible controls

* backups;
* exportable JSON;
* portable schemas;
* local copies of critical records;
* storage-status monitoring;
* no dependence on one public interface;
* documented recovery procedures.

## Risk Levels

Threats may be classified as:

### Low

Limited impact, easy correction, no sensitive exposure.

### Medium

Meaningful record-quality issue or limited private-data risk.

### High

Serious ecological, legal, privacy, financial, or credibility impact.

### Critical

Exposure of highly sensitive ecological information, credentials, permanent harmful publication, or major record tampering.

## Required Human Escalation

Human escalation should be mandatory for:

* legal or responsibility claims;
* vulnerable-species locations;
* neighboring-property observations;
* high-confidence species claims from weak evidence;
* permanent-storage approval;
* suspected altered evidence;
* duplicate sponsor or activity evidence;
* high-severity model hallucinations;
* publication of identifiable people;
* verified-outcome claims.

## Prototype Priorities

The initial prototype should prioritize controls for:

1. sensitive-location protection;
2. preserved original AI output;
3. human correction history;
4. evidence-grounding review;
5. no automated publication;
6. no automated legal conclusions;
7. duplicate file detection by hash;
8. explicit activity-versus-outcome status;
9. credential protection;
10. permanent storage disabled by default.

## Known Limitations

The initial prototype may not independently verify:

* photograph origin;
* timestamp authenticity;
* contributor honesty;
* scientific identification;
* legal ownership;
* ecological causation;
* model-weight integrity;
* long-term environmental outcomes.

These limitations should be disclosed rather than obscured.

## Current Status

This threat model guides design and benchmark development.

It does not claim that every mitigation has already been implemented or independently audited.
