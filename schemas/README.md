# Schemas

This directory contains the structured data definitions used by Proof of Regeneration.

The schemas are intended to make ecological observations, AI outputs, human review, provenance, and publication state consistent and machine-verifiable.

## Current Schemas

### `observation.schema.json`

Defines the structure of a field observation or stewardship activity.

It includes:

* record identity;
* observation details;
* generalized and private location handling;
* image evidence;
* provisional AI analysis;
* inference metadata;
* human review;
* correction history;
* publication controls;
* timestamps.

The schema is designed to support multiple record types, including:

* ecological observations;
* restoration activities;
* agroforestry activities;
* watershed conditions;
* landscape conditions;
* human-disturbance observations;
* follow-up records.

### `provenance.schema.json`

Defines the audit trail linking:

* source evidence;
* field-note hashes;
* image hashes;
* inference provider;
* Nosana job metadata;
* model and prompt versions;
* validation results;
* human corrections;
* publication decisions;
* integrity hashes;
* optional permanent storage;
* audit events.

The provenance manifest is intended to preserve how a final public or private record was produced.

## Schema Version

The current schema version is:

```text
0.1.0
```

This is an early development version.

The schemas may change as the local prototype, first Nosana workload, and benchmark reveal practical requirements.

Breaking changes should result in a new schema version.

## Validation

Schema files use:

```text
JSON Schema Draft 2020-12
```

Future application code should validate records before they are accepted as complete.

Validation should check:

* required fields;
* allowed values;
* date and time formats;
* hash formats;
* record identifiers;
* confidence ranges;
* location sensitivity;
* publication state;
* review state.

Invalid data should not be silently accepted or discarded.

## Human Review

Schema validation does not confirm that an ecological interpretation is correct.

A record may be structurally valid while still containing:

* an incorrect classification;
* hallucinated visual evidence;
* inadequate uncertainty;
* an unsafe publication setting;
* an unsupported legal conclusion.

Human review remains required.

## Hashes

The current schemas use SHA-256 values formatted as:

```text
sha256:<64 lowercase hexadecimal characters>
```

Example:

```text
sha256:1111111111111111111111111111111111111111111111111111111111111111
```

Repeated placeholder characters may appear in sample data.

They must not be represented as hashes of real files.

## Location Privacy

The observation schema supports separate handling for:

* private coordinates;
* generalized public zones;
* rounded coordinates;
* site-only disclosure;
* hidden locations.

Exact location data should not be public by default.

## Publication States

Supported publication states include:

* private;
* restricted;
* public;
* archived;
* rejected.

Publication settings should be reviewed independently from ecological interpretation.

A scientifically useful record may still be unsuitable for public release.

## Corrections

Both schemas preserve correction history.

The original AI output should remain available even when a human reviewer changes:

* classification;
* evidence statements;
* confidence;
* uncertainty;
* sensitivity;
* publication state.

Corrections must not silently replace the original result.

## Relationship Between Schemas

A typical completed record will use both schemas:

```text
Observation record
        ↓
Source evidence and AI output
        ↓
Human review
        ↓
Final observation state
        ↓
Provenance manifest
```

The observation record describes the ecological or stewardship content.

The provenance manifest describes how that record was created, processed, reviewed, and published.

## Sample Data

Example records are available in:

```text
sample-data/
```

The current example is synthetic and uses placeholder hashes.

It is intended to demonstrate structure only.

## Planned Development

Future schema work may include:

* separate activity schemas;
* benchmark result schemas;
* contributor-consent fields;
* digital signatures;
* richer follow-up relationships;
* external vocabulary references;
* migration documentation;
* automated validation tests.

These additions should be made only when supported by working implementation needs.

## Current Status

These schemas are design artifacts for the early prototype.

They do not imply that every field, validation rule, or workflow is already implemented in software.
