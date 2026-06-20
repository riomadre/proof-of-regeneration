# Sample Data

This directory contains anonymized and synthetic example records used to demonstrate the Proof of Regeneration data structure.

The sample files are intended for:

* schema testing;
* application development;
* documentation;
* interface prototyping;
* validation examples;
* early benchmark preparation.

They are not presented as verified scientific records unless explicitly stated.

## Current Example

### `example-observation.json`

This file demonstrates a complete observation record containing:

* field-observation details;
* generalized location;
* image evidence metadata;
* provisional AI analysis;
* uncertainty;
* human correction;
* publication settings;
* placeholder hashes.

The example describes a compound-leaved plant observed at Rio Madre.

The taxonomic interpretation remains intentionally unresolved because the available evidence is insufficient for a confirmed genus or species identification.

## Synthetic and Placeholder Content

The current example includes synthetic or illustrative values.

These include:

* model name;
* inference timestamps;
* runtime;
* contributor identifiers;
* output hashes;
* image filename;
* review history.

Repeated hash characters such as:

```text
sha256:1111111111111111111111111111111111111111111111111111111111111111
```

are placeholders only.

They are not hashes generated from real files.

## Privacy

Public sample data must not contain:

* exact vulnerable-species coordinates;
* private access routes;
* identifiable neighboring-property details;
* faces without consent;
* vehicle plates;
* email addresses;
* phone numbers;
* personal identification;
* confidential records;
* API keys;
* private storage references;
* unsupported legal allegations.

Locations should be generalized to a habitat zone, landscape area, or site-level description.

## Image Files

Do not add original Rio Madre images to this directory until all of the following are confirmed:

1. The project has the right to publish the image.
2. The image has been reviewed for sensitive content.
3. Unnecessary metadata has been removed.
4. Exact location information is not exposed.
5. The publication status has been approved.
6. The image serves a clear technical or documentation purpose.

A structured sample record may reference a fictional filename without including the corresponding image.

## Future Sample Structure

As development progresses, this directory may contain:

```text
sample-data/
├── README.md
├── example-observation.json
├── example-provenance.json
├── valid/
│   ├── flora-observation.json
│   ├── watershed-condition.json
│   └── restoration-activity.json
└── invalid/
    ├── missing-review.json
    ├── invalid-confidence.json
    └── unsupported-publication-state.json
```

These files should be added only when they support real validation tests or implementation work.

## Valid Samples

Future valid samples should:

* pass the corresponding JSON Schema;
* use anonymized identifiers;
* use generalized locations;
* contain no secrets;
* identify whether values are synthetic or derived from authorized records.

## Invalid Samples

Deliberately invalid samples may be included to test:

* missing required fields;
* malformed hashes;
* confidence values outside the allowed range;
* unsupported categories;
* invalid timestamps;
* incorrect publication settings;
* incomplete review records.

Invalid samples must be clearly labeled so they are not mistaken for usable data.

## Relationship to the Benchmark

The public sample-data directory is not the full Rio Madre benchmark dataset.

The benchmark may include private source images and internal curator notes that cannot be published.

Public benchmark materials may later include:

* redacted records;
* approved images;
* aggregate metrics;
* model outputs;
* validation results;
* human-review outcomes;
* selected failure examples.

## Schema References

Observation records should validate against:

```text
schemas/observation.schema.json
```

Provenance manifests should validate against:

```text
schemas/provenance.schema.json
```

## Current Status

The current sample files are development examples.

They do not imply that live Nosana inference, permanent storage, or automated validation has already been implemented.
