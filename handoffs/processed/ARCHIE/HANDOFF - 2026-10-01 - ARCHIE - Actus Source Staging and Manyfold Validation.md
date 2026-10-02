Project: ARCHIE
Work Date: 2026-10-01
Session Title: Actus Source Staging and Manyfold Validation
Source Type: Chronicle Handoff
Prepared By: ARCHIE, consolidating AJ-authorized operational source conversations
Public Disclosure Check: Cleared for public repository

## AJ’s Objective

Secure a verified local hard copy of missing Sean-source packages on Actus while keeping canonical ingestion behind its existing HOLD. In parallel, continue the sacrificial Manyfold/Syncthing validation matrix without involving canonical collections.

## Work Completed

### Stage A source consolidation

AJ authorized Stage A for 134 NEED candidate rows reduced to 129 unique ACQUIRE packages. ARCHIE built an acquisition manifest, checked source and destination conditions, and began transfer into a dedicated Actus staging area. Package contents were to remain intact, with no flattening, internal renaming, replacement, canonical merging, or Manyfold reorganization.

The run stopped at HC-39, Lord Drakkon, because distinct source objects could not be represented losslessly by the existing destination mapping. The verified final checkpoint was:

| Measure | Result |
|---|---:|
| Planned unique packages | 129 |
| Copied and verified complete packages | 27 |
| Partial/failed package | 1: HC-39 |
| Unattempted packages blocked behind the stop | 101 |
| Bytes copied, including partial HC-39 | 19,690,682,226 |

Forty-one HC-39 objects were copied; 17 remained uncopied. Nothing was overwritten or coalesced as an assumed duplicate.

The source inspection correction established that Lord Drakkon has two distinct folders both named STLs. Calling all collisions duplicate filenames within one source folder was inaccurate. The destination audit recorded 33 collision groups across HC-39, HC-111, HC-130, and HC-297. Soldier Boy's duplicate-named 3MF objects had differing recorded sizes. Direct source inspection links were prepared for all collision pairs.

No source datapackage.json exclusions were encountered. The run separately recorded and retained 1,602 macOS-generated sidecars. Verification compared live source-object inventories and sizes, hashes of received source streams, and local rereads. Independent provider payload hashes were unavailable; that limit remained explicit.

AJ then paused the task. No transfer remained running and no automatic restart was scheduled. Completed packages and partial HC-39 were preserved.

### Sacrificial validation

Payload Tests 4–6 each achieved two clean Syncthing-observed repeats for creation, modification, and deletion. The original payload was RTF inside an extra nested folder; that setup anomaly was preserved before plain-text repeats. The extra folder was not cleaned up.

An attempted metadata-deletion test could not run because its prerequisite datapackage.json was absent on the Mac replica. It received no new PASS.

For metadata creation, ARCHIE made a legitimate Manyfold caption change on the existing sacrificial model and verified that the caption persisted. The Mac replica still showed no metadata file during passive observations, prompting diagnosis and storage-path verification. This did not establish server-side creation failure: the metadata exclusion meant the Mac was an insufficient observation point. The Daedalus companion documents that correction and the resolved count discrepancy.

Later, AJ supplied peer-side evidence through Sean's remote-hands session. The coordinating conversation documented the test-library storage mapping and authoritative Manyfold metadata. Supplied authoritative JSON retained the October 1 test caption. This provided strong evidence of server-side metadata generation but did not by itself certify two independently observed controlled creation cycles.

Test 7 Pass 1 then introduced an intentionally fake, plain UTF-8 datapackage.json into the sacrificial JANUS replica. Its marker was STALE_METADATA_ATTACK_PASS_1. Local creation and exact contents were verified. The fake file remained unchanged through watcher observation, a manual JANUS rescan, and a JANUS Syncthing restart. After each phase, Sean's supplied authoritative-file output remained legitimate Manyfold JSON without the attack marker. Ignore rules remained unchanged.

The scoped version-history check returned two AppleDouble sidecar filenames and no actual archived metadata JSON matches. JANUS had no configured versioning or default history directory. This check did not establish restore behavior.

Sean subsequently restarted the peer Syncthing endpoint. Authoritative metadata again retained its legitimate content without the attack marker. AJ reported that the peer-side datapackage conflict search returned no output. The coordinating conversation closed Test 8 Pass 1 as PASS and recorded additional evidence toward Test 10.

## Important Questions and Discussions

The immediate physical goal was a reliable local source copy. Stage A staging was distinct from Stage B canonical ingestion. A certification HOLD on ingestion did not require stopping separately authorized source consolidation.

Metadata ownership stayed with Manyfold. Syncthing synchronized collection payloads while both endpoints excluded **/datapackage.json. The deliberately fake replica file was a test stimulus, not authoritative metadata.

## Decisions and Why They Matter

The transfer stopped rather than lose distinct same-named source objects. Existing staged work stayed usable and auditable.

Validation stopped for the evening with the sacrificial environment preserved. Further testing must begin by reconciling the established ten-test matrix and its two-consecutive-pass requirement. A partial success must not become a claim of full readiness.

## Options Considered or Rejected

No unrestricted 248-operation ingestion run was performed. REPLACE, REPLACE+PRESERVE, ADD, REVIEW, reserved exceptions, HC-34 inclusion, and Wolverine replacement work were excluded from Stage A.

The existing copier must not be rerun unchanged against the partial staging tree. Internal renaming, unverified deduplication, and overwriting were not used to resolve source collisions.

A complete automatic rerun of all validation tests was rejected as the next action. First reconcile existing evidence; then execute only genuinely missing observations.

## Problems, Surprises, or Course Corrections

Source namespaces permitted duplicate folder and file names that the original local mapping could not preserve.

Earlier metadata observations were made on an intentionally excluded replica. Later authoritative peer output corrected the interpretation; it should not be narrated as a proven server failure followed by an unverified repair.

The Test 7 child chat lacked the full checklist and could not give a reliable total remaining count. The coordinating chat supplied the ten-test matrix. Version restoration remains untested, but no additional restoration program was silently adopted.

## Milestones Reached

- A verified 27-package local source copy plus preserved partial work.
- Lossless-mapping blockers documented before further transfer.
- Two clean observed repeats each for payload Tests 4–6.
- Test 7 Pass 1: stale metadata excluded across watcher, rescan, and local restart.
- Test 8 Pass 1: authoritative metadata intact after peer restart.
- Peer-side conflict search supplied with no matching results.

## Resulting Artifacts

- actus-acquisition-stage-a-20261001: Actus_Acquisition_Manifest.json/.csv, Acquisition_Result.json, Still_Missing.csv, Resume_Checkpoint.json, Filename_Collision_Evidence.json, All_Destination_Filename_Collisions.json, Source_Inspection_Links.html, and transfer records.
- Actus staging area: VERONICA Source Consolidation Stage A - 2026-10-01, including its records checkpoint.
- syncthing-continuation-2026-10-01: STATUS.txt, validation-register.json, action records, and observed state evidence.
- archie-sacrificial-validation-20261001: passive-state-evidence.json.
- manyfold-creation-trigger-2026-10-01: validation-register.json, daedalus-handoff.json, and persisted-caption evidence.
- Test 7 and coordinating chats: local test-file verification, authoritative output supplied after each phase, scoped history results, and end-of-evening handoffs.

Earlier saved validation registers are chronological checkpoints. Their blocked Test 7/8 states do not supersede the later peer-assisted Pass 1 evidence.

## Current Project State

Stage A is paused: 27 verified packages, partial HC-39, 101 unattempted packages, and 19.69 GB copied. Canonical collection folders, source repository, and service configuration were not modified by the acquisition run.

| Test | End-of-evening status |
|---|---|
| 1: metadata creation isolation | Strong later authoritative evidence; formal two-pass reconciliation still required |
| 2: metadata update isolation | Pass 1 previously reported; remaining evidence/pass reconciliation pending |
| 3: metadata deletion isolation | Pass 1 previously reported; attempted later deletion had no prerequisite and added no PASS |
| 4: payload creation | Two clean observed passes |
| 5: payload modification | Two clean observed passes |
| 6: payload deletion | Two clean observed passes |
| 7: stale metadata + local restart | Pass 1 PASS; full matrix still uncertified |
| 8: peer restart | Pass 1 PASS; full matrix still uncertified |
| 9: Manyfold rescan | Two earlier acknowledged rescans; complete acceptance evidence needs reconciliation |
| 10: conflict check | Earlier local checks plus later clean scoped peer search; formal completion needs reconciliation |

The fake JANUS metadata remains deliberately in place. No cleanup or restore test occurred. Canonical ingestion remains HOLD.

## Unresolved Items

Resolve collision-preserving destination mappings for HC-39, HC-111, HC-130, and HC-297. Make transfer resumption recognize and verify completed source objects rather than reacquire or overwrite them.

Complete matrix reconciliation and only the missing required passes. Preserve the distinction between Syncthing-observed payload propagation and independent peer filesystem/Manyfold verification.

## Stopping Point and Next Action

For acquisition: load the manifest, missing list, collision evidence, and checkpoint; obtain the required mapping decision; make the copier resume-aware; recheck source access, inventories, capacity, and permissions; then finish partial and remaining packages. Stop before canonical ingestion.

For validation: reconcile all ten tests against accumulated evidence, identify missing acceptance observations, and retain the test artifacts until the planned verification and cleanup are authorized. Contradictory behavior returns to Daedalus.

## Source Conversations and Batch Boundary

- Stage VERONICA acquisitions on Actus.
- Validate Manyfold Syncthing tests.
- Validate sacrificial metadata-delete.
- Validate sacrificial Manyfold sync.
- Verify Manyfold storage path.
- Create VERONICA Test 7 metadata.
- VERONICA — Sean Repository Consolidation & Actus Acquisition — 2026-10-01.

Companion VERONICA and Daedalus handoffs cover analytical reconciliation and technical diagnosis respectively. Their references here explain the sequence; they are not additional transfers or additional test passes.
