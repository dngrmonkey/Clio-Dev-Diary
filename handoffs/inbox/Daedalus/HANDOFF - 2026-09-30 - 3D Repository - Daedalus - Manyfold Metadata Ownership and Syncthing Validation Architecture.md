# Chronicle Handoff

Project: 3D Model Repository Workflow
Work Date: 2026-09-30
Session Title: Manyfold Metadata Ownership and Syncthing Validation Architecture
Source Type: Chronicle Handoff
Prepared By: Daedalus
Public Disclosure Check: Cleared for public repository

## AJ's Objective

Define a safe synchronization architecture for Manyfold-managed collection metadata while preserving bidirectional synchronization of collection payloads, then hand the proposed architecture to ARCHIE for empirical validation before canonical use.

## Work Completed

Daedalus established the component boundary for Manyfold, Syncthing, VERONICA, and JANUS around Manyfold's `datapackage.json` metadata.

Manyfold remains the sole lifecycle authority for `datapackage.json`. The architecture does not permit VERONICA or another synchronized endpoint to become a competing writer of Manyfold-managed metadata.

The proposed Syncthing strategy excludes `datapackage.json` from synchronization at every participating synchronized endpoint while leaving the remainder of the collection payload available for bidirectional synchronization. The purpose of the exclusion is to prevent a synchronized endpoint from restoring metadata that Manyfold intentionally deleted or replaced.

The resulting interface treats Manyfold-managed metadata as authoritative application state. VERONICA may consume that metadata for analysis through the defined interface, but it must not directly create, modify, restore, or synchronize Manyfold-managed `datapackage.json` files.

JANUS remains outside this architecture except as AJ's physical operational access point. It is not assigned metadata authority or a new synchronization role by this design.

The architecture was deliberately left pending empirical validation rather than promoted directly into canonical operation.

Daedalus produced a ten-test validation matrix covering the proposed synchronization and metadata-lifecycle behavior. ARCHIE added a restart-specific validation requirement as Test 7. The complete matrix, including that addition, was accepted as the validation specification.

ARCHIE accepted responsibility for controlling the sacrificial environment, executing the tests through Work, preserving evidence, and reporting results against the acceptance criteria.

The validation specification requires two consecutive complete passes before the proposed architecture can be treated as validated.

If execution reveals behavior inconsistent with the proposed architecture, ARCHIE is to return the evidence to Daedalus for architectural analysis rather than modifying the architecture during the test.

## Important Questions and Discussions

The central risk was metadata resurrection: if `datapackage.json` were synchronized like an ordinary collection payload, another endpoint could potentially reintroduce a file that Manyfold intentionally deleted. The architecture therefore separates Manyfold lifecycle metadata from the bidirectionally synchronized payload.

The discussion also clarified that read access to metadata does not imply write authority. VERONICA's analytical use of Manyfold metadata must not create a second lifecycle authority.

The architecture was treated as a hypothesis requiring controlled validation. The sacrificial test environment is intended to determine whether actual Syncthing and Manyfold behavior matches the proposed component model, including behavior across restart conditions.

## Decisions and Why They Matter

Manyfold is the sole lifecycle authority for `datapackage.json`.

Every endpoint participating in the relevant Syncthing relationship must enforce the `datapackage.json` exclusion. Collection payloads may otherwise remain bidirectionally synchronized.

VERONICA remains a consumer of Manyfold metadata and does not become a writer of Manyfold-managed metadata.

JANUS remains outside the metadata and synchronization architecture except as AJ's physical operational access point.

The ten-test matrix, including ARCHIE's restart addition, is the governing validation specification.

Validation requires two consecutive complete passes.

Canonical ingestion or deployment of this architecture remains HOLD / unauthorized until validation succeeds.

Unexpected test behavior is evidence for Daedalus review, not authorization for ARCHIE to alter the architecture during validation.

## Current State / Next Step

ARCHIE owns execution of the sacrificial validation matrix and evidence preservation.

Daedalus awaits the validation results. If the matrix passes twice consecutively, the architecture can return for canonicalization. If any test contradicts the proposed behavior, the evidence returns to Daedalus for architectural analysis before further deployment.
