# ENTRY 021 — October 1, 2026
## We Finally Download Some Files, and One of Them Immediately Proves the Point

October began with two jobs that had been deliberately separated from each other.

VERONICA still had unfinished analytical work in Batch 001.

ARCHIE, meanwhile, had permission to begin consolidating missing Sean/Yosh source packages onto ACTUS—but only into staging.

Canonical ingestion was still behind the HOLD.

That distinction was about to earn its keep.

### VERONICA Cleans Up the Evidence

VERONICA started by returning to the remaining Batch 001 exceptions rather than rerunning all 297 candidates.

The first attempt ran into HTTP 403 failures while retrieving recorded previews.

That was an access failure, not evidence that the previews did not exist, and we did not allow a transport problem to quietly become a collection decision.

Once AJ corrected the authenticated retrieval method, VERONICA recovered **16 previews covering 14 active candidates**.

Eleven of them became **VARIANT → ADD** proposals:

HC-16, HC-51, HC-87, HC-92, HC-102, HC-103, HC-105, HC-144, HC-180, HC-280, and HC-298.

HC-97, HC-128, and HC-129 remained REVIEW.

That reduced the active exception population substantially, but consolidation uncovered another issue.

Eight Gundam records that we had already resolved were missing their final values from the reconstructed state.

This was not permission to reconsider them.

It was a recovery problem.

VERONICA went back to the authoritative prior evidence and recovered the decisions we had already made:

**HC-14, HC-30, HC-42, HC-59, HC-75, HC-90, HC-98, and HC-114 remained NEED / NO-MATCH / ACQUIRE.**

The earlier normalization of the generic **Gundam Helmet** holding to **RX-78-2 Gundam Helmet** remained intact.

No new visual judgment was substituted for the old decisions.

That mattered. A reconstruction process that silently re-decides history is not reconstruction.

VERONICA then reconciled all **297 candidates** and reviewed all **18 recorded duplicate groups**.

Twelve groups turned out to be repeated references to shared source objects.

Five redundant ACQUIRE proposals could therefore be suppressed without losing candidate provenance:

- HC-17 → HC-33
- HC-18 → HC-28
- HC-19 → HC-58
- HC-20 → HC-80
- HC-124 → HC-221

Other apparent duplicates did not receive the same treatment.

Six separate-folder groups had matching model manifests, but we did not have byte-hash verification proving they were identical. They stayed separate.

Same-looking evidence was not promoted into stronger evidence merely because merging them would have made the spreadsheet tidier.

By the end of reconciliation, every candidate was still accounted for:

- **NEED: 134**
- **HAVE: 138**
- **VARIANT: 16**
- **REVIEW: 9**

The resulting planning set contained **253 candidate payload proposals**, reduced to **248 unique eventual operations** after the five duplicate suppressions.

Those numbers were planning state, not authorization to execute 248 collection changes.

The proposal mix included ACQUIRE, ADD, REPLACE, REPLACE+PRESERVE, NO ACTION, and held/review cases. Wolverine replacement collisions remained held, HC-34 still required an inclusion decision, and unresolved identities and preservation mappings stayed unresolved.

VERONICA had made the plan better.

She had not made uncertainty disappear.

### Stage A Actually Starts Moving Data

With the analytical state reconciled, ARCHIE could act on the safest portion.

AJ authorized **Stage A source consolidation** for the **134 NEED candidate rows**, which became **129 unique ACQUIRE packages** after duplicate suppression.

This was not canonical ingestion.

The goal was much simpler: secure a verified local copy of the missing source packages on ACTUS while preserving their source structure.

No flattening.

No internal renaming.

No replacement.

No merging into canonical collections.

No Manyfold reorganization.

For the first time in this sequence, packages actually started moving.

Twenty-seven complete packages made it into the ACTUS staging area and were verified.

Then package 28 demonstrated exactly why we had staged first.

**HC-39 — Lord Drakkon** contained source objects that the existing destination mapping could not represent losslessly.

The transfer stopped.

Not after trying to invent names.

Not after overwriting one file with another.

Not after assuming two things with the same name must be duplicates.

It stopped.

Inspection showed that Lord Drakkon contained **two distinct folders both named `STLs`**.

The broader audit identified **33 collision groups across HC-39, HC-111, HC-130, and HC-297**. Soldier Boy even had duplicate-named 3MF objects with different recorded sizes.

The source namespace was capable of representing things our initial local mapping was not.

Classic file-management problem: the source was perfectly happy being weird until we tried to preserve it faithfully.

At the stop point:

- **129** unique packages had been planned.
- **27** were copied and verified complete.
- **HC-39** was partial.
- **101** packages remained unattempted behind the stop.
- About **19.69 GB** had been copied, including the partial HC-39 payload.

Forty-one HC-39 objects had copied successfully.

Seventeen had not.

Nothing was overwritten or coalesced merely to get the run across the finish line.

AJ paused the transfer, and ARCHIE preserved both the completed packages and the partial checkpoint.

The copier would need a collision-preserving mapping strategy and resume awareness before it could safely continue.

### Meanwhile, the Metadata Tests Get More Interesting

The sacrificial Manyfold/Syncthing validation continued separately.

Payload Tests **4, 5, and 6**—creation, modification, and deletion—each achieved **two clean Syncthing-observed repeats**.

That was useful progress.

Metadata testing was less straightforward.

An attempted deletion test could not proceed because the expected `datapackage.json` was not present on the Mac replica.

Then ARCHIE made a legitimate caption change on the sacrificial Manyfold model.

The caption persisted in Manyfold.

The replica still showed no metadata file.

For a moment, this looked like Manyfold might not be generating the metadata we expected.

Daedalus was brought in to diagnose it.

And Daedalus found that we were looking in the wrong place to answer the question.

The Mac replica was intentionally configured to exclude Manyfold's `datapackage.json`.

Its failure to contain that file therefore could not establish that the authoritative server had failed to create it.

We had successfully implemented an exclusion boundary and then briefly used the excluded side of that boundary to ask whether the excluded thing existed.

There are easier ways to manufacture mysteries.

Daedalus traced the Manyfold write path far enough to establish another important detail: saving a changed model scheduled an **UpdateDatapackageJob**, and promotion into library storage involved a separate **FilePromoteJob**.

An empty current job dashboard did not prove that the historical write had succeeded or failed.

It only proved there was no currently visible backlog.

Daedalus therefore refused to call this a Manyfold creation defect.

At that diagnostic checkpoint, the correct conclusion was narrower:

**the replica lacked the file, and we did not yet have authoritative server-side evidence.**

The proposed recovery—if authoritative inspection eventually proved the file genuinely absent—was a single model-scoped invocation of Manyfold's existing write mechanism followed by observation of the relevant jobs and storage.

But that recovery was never executed.

Because later in the evening, AJ obtained authoritative peer-side evidence through Sean's remote-hands session.

The actual Manyfold metadata existed.

And it contained the October 1 test caption.

That superseded the earlier uncertainty and removed the reason to regenerate anything.

Daedalus had prevented an observation problem from becoming an unnecessary repair.

### Then We Try to Resurrect the Metadata on Purpose

With authoritative observation available, ARCHIE moved into the restart/resurrection portion of the validation matrix.

For **Test 7 Pass 1**, an intentionally fake plain-text `datapackage.json` was created on the sacrificial JANUS replica.

Its marker was:

**STALE_METADATA_ATTACK_PASS_1**

This was exactly the failure mode the September 30 architecture was designed to prevent: stale replica metadata attempting to intrude on Manyfold's authoritative state.

The fake file was verified locally.

Then ARCHIE watched what happened.

It remained local through watcher observation.

It remained local after a manual JANUS rescan.

It remained local after restarting JANUS Syncthing.

After each phase, the authoritative Manyfold metadata remained legitimate and did **not** acquire the attack marker.

Sean then restarted the peer Syncthing endpoint.

The authoritative metadata still retained the legitimate Manyfold content.

A peer-side conflict search returned no matching conflict output.

ARCHIE closed **Test 7 Pass 1** as PASS and **Test 8 Pass 1** as PASS.

There was also evidence relevant to the conflict checks.

But we did not turn that into a declaration that the whole architecture was certified.

The September 30 rule still applied:

**the complete validation matrix requires two consecutive complete passes.**

Some tests had two clean observations.

Some had one.

Some accumulated evidence that still needed formal reconciliation against the acceptance criteria.

Metadata creation had strong later authoritative evidence, but not yet two independently observed controlled creation cycles.

The deletion attempt had added no new pass because its prerequisite was missing.

Version restoration had not been tested.

The fake JANUS metadata remained deliberately in place.

And canonical ingestion remained on HOLD.

That restraint mattered because October 1 had produced a lot of good news.

VERONICA had reconciled all 297 candidate records without throwing away prior decisions.

The acquisition plan had become more deterministic.

Twenty-seven source packages now existed as verified local staged copies.

The transfer system had exposed a real namespace problem before it could damage anything.

Payload synchronization behaved correctly across repeated tests.

The stale-metadata attack failed to contaminate authoritative metadata through local restart, peer restart, or rescan.

And an apparent Manyfold metadata failure turned out to be an observation-boundary problem rather than a demonstrated application defect.

That is a productive day.

It is not the same thing as a finished system.

So we stopped with both major workstreams deliberately incomplete.

For acquisition, ARCHIE needed a lossless mapping for the collision cases and a resume-aware copier before touching the remaining packages.

For infrastructure, ARCHIE needed to reconcile all accumulated evidence against the original ten-test matrix and execute only the observations still genuinely missing.

And after all of that, canonical ingestion would still require AJ's authorization.

We had finally started moving real data.

The first troublesome package immediately reminded us why we had spent so much time designing the guardrails.

Annoying.

Also rather satisfying.

**Stopping point:** VERONICA reconciled all 297 Batch 001 candidates and produced a preserved, non-executable planning state with 248 unique eventual operations. ARCHIE began Stage A source consolidation and verified 27 complete packages before stopping safely at HC-39 when the existing destination mapping could not losslessly represent the source namespace. In the sacrificial environment, payload Tests 4–6 achieved two clean observed passes, stale-metadata Test 7 Pass 1 and peer-restart Test 8 Pass 1 passed, and authoritative peer evidence corrected an apparent Manyfold metadata-creation problem that Daedalus had already narrowed to an observation-boundary issue. The full ten-test matrix remained uncertified, Stage A remained paused, and canonical ingestion remained on HOLD.
