# Proof of Regeneration — Darwin Core Mapping

## Purpose

This document describes how selected Proof of Regeneration observation fields may map to Darwin Core terms for biodiversity-data exchange.

Proof of Regeneration is not intended to replace Darwin Core.

The project has additional requirements involving:

* AI-assisted interpretation;
* human correction;
* provenance;
* evidence grounding;
* privacy sensitivity;
* restoration activity;
* publication controls;
* longitudinal outcomes.

These concepts do not always have direct Darwin Core equivalents.

The mapping is therefore intended as an interoperability and export layer.

## Mapping Principles

1. Use established Darwin Core terms where the meanings genuinely align.
2. Do not force AI, provenance, or restoration fields into unrelated biodiversity terms.
3. Preserve the original Proof of Regeneration record.
4. Treat the Darwin Core representation as an export or derived view.
5. Generalize sensitive location fields before public export.
6. Do not export provisional classifications as confirmed identifications without clear qualification.
7. Record unmapped project-specific information in extensions or separate linked records where possible.

## Conceptual Difference

Darwin Core primarily supports the exchange of biodiversity information concerning:

* occurrences;
* organisms;
* events;
* locations;
* identifications;
* taxa;
* geological context;
* measurements;
* media;
* record-level metadata.

Proof of Regeneration additionally records:

* model-generated interpretation;
* uncertainty;
* confidence;
* human-review status;
* correction history;
* provenance hashes;
* inference metadata;
* privacy classification;
* restoration activity;
* funding or program references;
* follow-up outcome status.

Not every Proof of Regeneration record is a biological occurrence.

Examples that may not map cleanly to a standard occurrence include:

* tree-planting activity;
* erosion condition;
* altered drainage;
* restoration work;
* human disturbance;
* visitor-supported stewardship.

## Core Observation Mapping

| Proof of Regeneration field  | Darwin Core term                              | Mapping note                                                                     |
| ---------------------------- | --------------------------------------------- | -------------------------------------------------------------------------------- |
| `record_id`                  | `dwc:occurrenceID`                            | Appropriate when the record represents an organism occurrence.                   |
| `record_id`                  | `dwc:eventID`                                 | May be more appropriate for sampling, restoration, or field events.              |
| `parent_record_id`           | `dwc:parentEventID`                           | Useful where a follow-up record belongs to a broader event hierarchy.            |
| `observation.observed_at`    | `dwc:eventDate`                               | ISO 8601 date or date-time of the observation event.                             |
| `observation.field_note`     | `dwc:eventRemarks` or `dwc:occurrenceRemarks` | Select according to whether the note describes the event or organism occurrence. |
| `observation.contributor_id` | `dwc:recordedByID`                            | Prefer an authorized stable identifier where available.                          |
| authorized contributor name  | `dwc:recordedBy`                              | Should not be exported publicly without permission.                              |
| `observation.habitat`        | `dwc:habitat`                                 | General habitat description.                                                     |
| `location.site`              | `dwc:locality`                                | General site or locality description.                                            |
| original location wording    | `dwc:verbatimLocality`                        | Only when safe and appropriate to preserve.                                      |
| private latitude             | `dwc:decimalLatitude`                         | Must not be included in public exports for sensitive records.                    |
| private longitude            | `dwc:decimalLongitude`                        | Must not be included in public exports for sensitive records.                    |
| coordinate accuracy          | `dwc:coordinateUncertaintyInMeters`           | Represents spatial uncertainty, not privacy masking by itself.                   |
| coordinate reference system  | `dwc:geodeticDatum`                           | Should be recorded when coordinates are exported.                                |
| location review status       | `dwc:georeferenceVerificationStatus`          | May describe georeference review, not ecological verification.                   |
| public generalized zone      | `dwc:locality`                                | Use a safe generalized locality for public records.                              |
| field image reference        | `dwc:associatedMedia`                         | Public or authorized media reference only.                                       |
| related observation IDs      | `dwc:associatedOccurrences`                   | May link related organism-occurrence records.                                    |
| related taxon information    | `dwc:associatedTaxa`                          | Use only when relevant and properly formatted.                                   |

## Taxonomic Mapping

| Proof of Regeneration field | Darwin Core term                       | Mapping note                                                                                                                        |
| --------------------------- | -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| reviewed scientific name    | `dwc:scientificName`                   | Use the reviewed interpretation, not unreviewed AI output.                                                                          |
| reviewed taxon identifier   | `dwc:taxonID`                          | Use when a reliable taxon identifier is available.                                                                                  |
| taxonomic rank              | `dwc:taxonRank`                        | Examples include species, genus, or family.                                                                                         |
| reviewed kingdom            | `dwc:kingdom`                          | Optional derived taxonomic field.                                                                                                   |
| reviewed phylum             | `dwc:phylum`                           | Optional derived taxonomic field.                                                                                                   |
| reviewed class              | `dwc:class`                            | Optional derived taxonomic field.                                                                                                   |
| reviewed order              | `dwc:order`                            | Optional derived taxonomic field.                                                                                                   |
| reviewed family             | `dwc:family`                           | Optional derived taxonomic field.                                                                                                   |
| reviewed genus              | `dwc:genus`                            | Use only when the reviewed evidence supports genus level.                                                                           |
| reviewed specific epithet   | `dwc:specificEpithet`                  | Use only for sufficiently supported species-level records.                                                                          |
| identification date         | `dwc:dateIdentified`                   | Date of the reviewed identification.                                                                                                |
| reviewer identity           | `dwc:identifiedByID`                   | Use an authorized identifier where appropriate.                                                                                     |
| reviewer name               | `dwc:identifiedBy`                     | Public disclosure requires consent.                                                                                                 |
| identification notes        | `dwc:identificationRemarks`            | May record unresolved status, limitations, or review notes.                                                                         |
| confidence or qualification | `dwc:identificationQualifier`          | May hold a conventional qualifier such as `cf.` or `aff.`; do not insert arbitrary numeric confidence without a defined convention. |
| identification verification | `dwc:identificationVerificationStatus` | May describe identification-review status when used consistently.                                                                   |

## Occurrence Mapping

| Proof of Regeneration field | Darwin Core term           | Mapping note                                        |
| --------------------------- | -------------------------- | --------------------------------------------------- |
| organism observed           | `dwc:occurrenceStatus`     | Normally `present` for a documented occurrence.     |
| count                       | `dwc:individualCount`      | Use only when a defensible count is available.      |
| organism quantity           | `dwc:organismQuantity`     | May be used with a corresponding quantity type.     |
| quantity method             | `dwc:organismQuantityType` | Example: individuals or percentage cover.           |
| life stage                  | `dwc:lifeStage`            | Use when visible or reliably known.                 |
| sex                         | `dwc:sex`                  | Use only when supported.                            |
| behavior                    | `dwc:behavior`             | Use only when directly observed.                    |
| vitality or condition       | `dwc:vitality`             | May be relevant for planted or monitored organisms. |
| occurrence notes            | `dwc:occurrenceRemarks`    | Suitable for reviewed occurrence-specific comments. |

## Evidence and Media Mapping

| Proof of Regeneration field | Darwin Core term           | Mapping note                                                                                                 |
| --------------------------- | -------------------------- | ------------------------------------------------------------------------------------------------------------ |
| public image URL            | `dwc:associatedMedia`      | Do not export private or temporary signed URLs.                                                              |
| public record URL           | `dwc:occurrenceDetails`    | May link to a public occurrence record page.                                                                 |
| related source or report    | `dwc:associatedReferences` | Use for public documentation references.                                                                     |
| evidence type               | `dwc:basisOfRecord`        | A human observation may map to `HumanObservation`; use controlled values appropriate to the exported record. |
| catalog or local reference  | `dwc:catalogNumber`        | Optional local reference, distinct from a globally unique occurrence identifier.                             |

## Record-Level Mapping

| Proof of Regeneration field | Darwin Core or Dublin Core term           | Mapping note                                                        |
| --------------------------- | ----------------------------------------- | ------------------------------------------------------------------- |
| record language             | `dcterms:language`                        | Language of the exported record.                                    |
| rights statement            | `dcterms:rights`                          | Rights or usage statement.                                          |
| license                     | `dcterms:license`                         | Public license for the exported record or media.                    |
| institution or project      | `dwc:institutionCode`                     | May use a stable project or institutional code if formally defined. |
| collection or dataset       | `dwc:collectionCode` or `dwc:datasetName` | Use consistently for Rio Madre or a future project dataset.         |
| dataset identifier          | `dwc:datasetID`                           | Stable identifier for the exported dataset.                         |
| record creator              | `dcterms:creator`                         | May identify the organization creating the derived export.          |
| record modified date        | `dcterms:modified`                        | Date the exported Darwin Core record was last modified.             |

## Proof of Regeneration Fields Without Direct Darwin Core Equivalents

The following fields should remain project-specific or be represented through a documented extension.

### AI inference metadata

* inference provider;
* Nosana job identifier;
* deployment identifier;
* model name;
* model version;
* container image;
* container digest;
* prompt version;
* inference parameters;
* runtime;
* estimated cost.

### AI interpretation quality

* model-generated confidence;
* uncertainty assessment;
* human-review priority;
* evidence-grounding score;
* hallucinated-feature findings;
* observer-note influence;
* repeated-run disagreement.

### Provenance

* source-image hash;
* note hash;
* input-bundle hash;
* raw-output hash;
* reviewed-output hash;
* manifest hash;
* digital signature;
* correction history;
* audit events.

### Privacy and publication

* location sensitivity;
* public precision;
* image visibility;
* publication status;
* permanent-storage approval;
* redaction note.

### Stewardship and restoration

* restoration activity type;
* program or funding reference;
* responsible party;
* baseline record;
* scheduled follow-up;
* activity-completion status;
* outcome-verification status.

These fields should not be placed inside unrelated Darwin Core terms merely to make the export appear complete.

## Provisional AI Output

Unreviewed AI classifications should not be exported as confirmed Darwin Core taxonomic identifications.

Possible approaches include:

### Exclude from biodiversity export

Export only records that have completed human review.

### Export as project-specific extension

Retain the AI output in a linked Proof of Regeneration extension or provenance record.

### Include in remarks with explicit status

Where necessary, use a clearly labeled remarks field stating that the interpretation is provisional and machine-generated.

The preferred initial approach is to export only the human-reviewed interpretation as Darwin Core taxonomic content.

## Sensitive Location Export

Proof of Regeneration distinguishes between:

* private exact coordinates;
* public rounded coordinates;
* generalized zones;
* site-level location;
* hidden location.

A public Darwin Core export should follow the record’s approved public precision.

### Exact

Export coordinates only for non-sensitive, approved records.

### Rounded

Export deliberately reduced coordinate precision and document coordinate uncertainty.

### Zone

Export a generalized locality and omit exact coordinates.

### Site only

Export `Rio Madre, Costa Rica` or another approved site description.

### Hidden

Omit coordinates and use only a safe locality description where appropriate.

Coordinate uncertainty should describe the spatial precision of the exported coordinate.

It should not be used as the only mechanism for concealing sensitive information.

## Follow-Up Records

Follow-up observations may be represented through:

* a shared `eventID`;
* a `parentEventID`;
* related occurrence identifiers;
* project-specific parent-record links;
* a separate longitudinal activity record.

An individual planted tree may produce several occurrence records over time.

Example:

```text
Planting event
    ↓
Initial organism occurrence
    ↓
Three-month observation
    ↓
Six-month observation
    ↓
One-year observation
```

Each observation should retain its own date, evidence, review, and provenance.

## Restoration Activities

A restoration activity is not always a Darwin Core occurrence.

Possible representations include:

### Event record

Use an event-oriented export for:

* planting day;
* monitoring visit;
* habitat survey;
* restoration inspection.

### Occurrence records

Use occurrence records for organisms observed during the event.

### Project-specific activity record

Retain the stewardship action, funding, responsible party, and outcome status in Proof of Regeneration.

The project should not misrepresent an activity as a biodiversity occurrence merely to fit the standard.

## Example Export Mapping

A reviewed flora observation might produce:

```json
{
  "occurrenceID": "rm-2026-0001",
  "basisOfRecord": "HumanObservation",
  "eventDate": "2026-05-23T09:30:00-06:00",
  "locality": "Regenerating forest edge, Rio Madre, Costa Rica",
  "habitat": "Humid regenerating forest edge",
  "occurrenceStatus": "present",
  "scientificName": null,
  "taxonRank": null,
  "identificationRemarks": "Compound-leaved plant appearing consistent with a Mimosa or related legume; identification remains unresolved from available evidence.",
  "occurrenceRemarks": "Additional photographs of stem, flowers, fruit, and leaf response are required.",
  "associatedMedia": null
}
```

This example intentionally leaves the scientific name unresolved.

A broad but cautious reviewed interpretation is preferable to unsupported taxonomic precision.

## Recommended Export Profile

The initial Darwin Core export should be limited to reviewed biological-occurrence records.

Minimum recommended fields:

* `occurrenceID`;
* `basisOfRecord`;
* `eventDate`;
* `recordedByID` where authorized;
* `locality`;
* `habitat`;
* `occurrenceStatus`;
* `scientificName` where supported;
* `taxonRank` where supported;
* `identificationRemarks`;
* `occurrenceRemarks`;
* `associatedMedia` where public;
* `datasetName`;
* `datasetID`;
* `dcterms:license`;
* `dcterms:modified`.

## Future Implementation

Future development may include:

* a Darwin Core export function;
* a field-mapping configuration;
* validation of required export fields;
* controlled vocabulary checks;
* public and restricted export profiles;
* integration tests;
* sample Darwin Core CSV output;
* documentation of project-specific extensions.

## Current Status

This document is a preliminary interoperability mapping.

It does not claim that a Darwin Core export function has already been implemented or validated by TDWG, GBIF, or another external organization.
