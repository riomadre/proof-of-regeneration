# Proof of Regeneration — Privacy and Ethics

## Purpose

Proof of Regeneration is intended to help land stewards create transparent, human-reviewed records of ecological observations, restoration activities, regenerative land use, and future visitor-supported stewardship.

The system must protect sensitive ecological, personal, legal, and location data while making public claims more accountable.

Rio Madre in Costa Rica will serve as the first real-world test site.

## Core Principle

Technology must support field knowledge and stewardship rather than replace them.

AI-generated output is provisional. It must not be treated as confirmed ecological evidence without human review.

## Human Review

Every AI-generated result should be:

* approved;
* corrected;
* rejected; or
* marked for follow-up.

The system must preserve:

* the original field note;
* the original AI output;
* the reviewer’s changes;
* the final reviewed record;
* the review status;
* the review timestamp.

Human corrections must not silently overwrite the original model response.

## Representation of Uncertainty

The system must clearly distinguish between:

* confirmed information;
* provisional interpretation;
* low-confidence classification;
* unresolved identification;
* missing evidence;
* conflicting evidence.

Preferred language includes:

* provisionally identified;
* appears consistent with;
* likely;
* possible;
* unresolved from available evidence;
* further observation required.

The system should avoid false precision, especially for species-level identification from limited photographs.

## Sensitive Ecological Information

Exact locations should not be public by default.

Sensitive examples include:

* nests;
* dens;
* breeding areas;
* rare plants;
* threatened species;
* vulnerable habitat;
* wildlife movement routes;
* private access points.

Public records should use generalized locations such as:

* habitat zone;
* watershed area;
* rounded coordinates;
* landscape sector;
* hidden location.

## Personal Privacy

The system should not publish unnecessary personal information.

Public records must avoid exposing:

* full names without consent;
* faces without consent;
* phone numbers;
* email addresses;
* personal identification;
* vehicle plates;
* private correspondence;
* precise residential locations.

Images should be reviewed before publication for identifiable people or private information.

## Neighboring Properties and Legal Sensitivity

Records involving neighboring properties, land clearing, burning, river works, access disputes, or other potentially contentious matters require careful handling.

The system may describe visible conditions such as:

* cleared vegetation;
* exposed soil;
* smoke or burn evidence;
* raised earth;
* altered drainage;
* sediment;
* construction activity.

The system must not use AI to determine:

* legal responsibility;
* regulatory violations;
* ownership;
* intent;
* criminal conduct;
* environmental liability.

Potentially contentious records should remain private or restricted unless publication has been reviewed for accuracy, necessity, and legal risk.

## No Automated Accusations

AI output must never identify a person or organization as responsible for environmental harm based only on photographs, location, or contextual assumptions.

The system should separate:

* observed condition;
* human interpretation;
* legal conclusion.

Only the first should be generated automatically.

## Data Ownership and Contributor Control

Source data should remain under the control of the land steward or contributor who has the right to submit it.

Contributors should understand:

* what will be stored;
* what may be processed by AI;
* what may become public;
* what may remain private;
* whether a record may be retained after publication;
* how corrections may be requested.

The project should not claim ownership over third-party knowledge, images, or field records without permission.

## Indigenous and Local Knowledge

Local and traditional ecological knowledge should not be extracted, republished, or commercialized without appropriate consent and attribution.

The system should avoid presenting community knowledge as AI-generated knowledge.

Where local expertise contributes to identification or interpretation, that contribution should be acknowledged when permission is given.

## AI Limitations

The system must communicate that vision-language models may:

* hallucinate visible features;
* overstate confidence;
* confuse similar species;
* infer details not present in the image;
* produce inconsistent outputs;
* miss privacy risks;
* misinterpret land conditions.

AI output should assist review, not replace expert judgment.

## Publication Levels

Suggested publication states:

### Private

Visible only to authorized project users.

Used for:

* sensitive evidence;
* exact coordinates;
* private field notes;
* legal or neighboring-property matters;
* unreviewed submissions.

### Restricted

Visible only to approved collaborators or researchers.

Used for:

* sensitive ecological records;
* detailed location data;
* records requiring controlled access.

### Public

Visible to general users after review and redaction.

May include:

* approved images;
* generalized location;
* reviewed description;
* uncertainty;
* provenance details;
* follow-up status.

### Rejected

Retained for audit or evaluation but not treated as a valid ecological record.

## Permanent Storage

Permanent decentralized storage should only be used for approved, non-sensitive information.

Do not permanently publish:

* exact vulnerable-species locations;
* identifiable private individuals;
* personal data;
* legal allegations;
* unredacted neighboring-property records;
* private access information;
* confidential project files.

Where appropriate, a public record may store only a hash or redacted manifest rather than the full source evidence.

## Data Minimization

Collect only the information needed for the ecological or stewardship purpose.

Avoid collecting unnecessary:

* personal details;
* precise location data;
* device metadata;
* contact information;
* background imagery;
* ownership information.

Image metadata should be removed or reviewed before publication.

## Security

Never commit or expose:

* API keys;
* access tokens;
* passwords;
* storage credentials;
* private database URLs;
* personal identification;
* private legal documents;
* exact sensitive coordinates.

Credentials must be stored in environment variables or secure secret-management systems.

## Corrections and Record History

Public ecological records may change as new evidence becomes available.

Corrections should:

* preserve the prior version;
* identify what changed;
* record the date;
* identify the reviewer where appropriate;
* explain the basis for the correction.

The system should not present corrected records as if the earlier interpretation never existed.

## Environmental Claims

Proof of Regeneration should not automatically claim:

* biodiversity gain;
* ecosystem restoration;
* carbon benefit;
* habitat improvement;
* community benefit;
* legal compliance.

Such claims require:

* a defined baseline;
* appropriate evidence;
* clear methods;
* follow-up observations;
* human review;
* transparent limitations.

A photograph of an activity does not by itself prove a successful environmental outcome.

## Visitor and Sponsor Records

Future visitor-supported or sponsor-supported activities should distinguish between:

* funds received;
* activity completed;
* evidence recorded;
* follow-up completed;
* outcome verified.

The system should not imply that payment alone proves ecological benefit.

## Benchmark Ethics

The benchmark dataset should use:

* authorized Rio Madre images;
* anonymized identifiers;
* generalized locations;
* redacted sensitive content;
* documented human review.

Difficult or failed model outputs should be reported honestly.

Benchmark images must not be selected only to make the model appear successful.

## Project Commitments

Proof of Regeneration will aim to:

* preserve uncertainty;
* prioritize human review;
* protect sensitive locations;
* minimize personal data;
* avoid automated legal conclusions;
* preserve correction history;
* report failures;
* distinguish activity from outcome;
* keep source data under responsible stewardship;
* use technology in service of land and community.

## Current Status

These principles guide project design and development.

They do not imply that all privacy, storage, review, or publication features are already implemented.
