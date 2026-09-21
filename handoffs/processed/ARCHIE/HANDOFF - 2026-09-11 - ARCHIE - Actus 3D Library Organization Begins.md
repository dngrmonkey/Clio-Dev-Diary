# Chronicle Handoff

Project: ARCHIE
Work Date: 2026-09-11
Session Title: Actus 3D Library Organization Begins
Source Type: Chronicle Handoff
Prepared By: ARCHIE
Public Disclosure Check: Cleared for public repository

## AJ’s Objective

AJ began a structured effort to turn the Actus 3D-print collection into a clean, usable model library.

At the start of the session, the collection was divided broadly between two source groups: **unzipped 3D files** and **zipped 3D files**. The collection included cosplay and fabrication assets such as helmets/headgear, armor, blasters, bladed weapons, figures/models, and other printable items.

AJ wanted ARCHIE to:

- detect duplicate models and packages;
- organize evaluated models into a clean browsing structure;
- distinguish checked/sorted material from material still awaiting review;
- make ZIP-only models usable rather than leaving much of the collection trapped in archives; and
- above all, prevent the loss of any models while the organization process was being validated.

The preservation requirement was explicit: **no model was to be lost as a consequence of deduplication or reorganization.**

## Work Completed

ARCHIE first inspected the existing collection without reorganizing the source material.

A **read-only file inventory/count** established a baseline of **16,882 collection files totaling approximately 248.58 GB**, with no read errors reported during that inventory. This inventory established what files existed, their locations, sizes, and related basic filesystem information; it did **not** mean that all 16,882 files had been content-fingerprinted or verified.

The working organization model established at this stage was:

**Category → Universe/Franchise → Item**

Examples included Headgear, Armor, Blasters & Firearms, Bladed Weapons, Props & Accessories, Figures & Models, Stands & Displays, and practical/tool prints. Within a category, models would be grouped by universe or franchise and then by individual item.

The operating rules established around that structure were preservation-first:

- Original source material remains intact during evaluation.
- Nothing is deleted or overwritten during duplicate analysis.
- Complete model packages remain together, including model parts, instructions, reference images, alternate parts, and creator information where present.
- Distinct creators, versions, or designs are not collapsed merely because they depict the same character or object.
- Full armor kits remain intact rather than having bundled components duplicated into other categories.
- Ambiguous material is held for review rather than classified by guesswork.
- Exact file duplicates are determined by actual content fingerprints rather than filenames alone.
- ZIP archives and extracted folders are compared at the package/content level before being treated as equivalent packages.

A **Tron Ares Helmet** package was selected as the initial validation pilot.

The pilot performed targeted content comparison on two extracted packages and three ZIP archives representing the same helmet. That comparison confirmed that the two extracted packages contained identical required model files and that all three ZIP archives contained the same required model content.

Rather than immediately deleting redundant material, ARCHIE copied the pilot material into the developing organized area and verified the pilot copies against their originals using file fingerprints. The initial pilot retained all comparison copies so AJ could inspect the result.

AJ confirmed that the intended end state was not five copies of the same package. The clean library should contain **one complete usable model package**, while redundant source material remained preserved until consolidation could be performed safely.

The pilot was then refined so that the clean Tron Ares item contained only the two required model parts. Redundant pilot comparison copies were moved out of the browsing library into a holding area, while the original source packages remained unchanged. No source files were deleted.

AJ reviewed the resulting folder and approved the pilot pattern.

## Important Questions and Discussions

A major question was how ZIP archives should participate in the finished library.

AJ noted that many collected models existed only as ZIP archives and therefore were difficult to browse or use directly. The agreed approach was to treat ZIPs as source packages rather than as the desired browsing format.

The handling model established was:

- If a ZIP is verified to match an existing extracted package, the clean library uses the verified extracted package.
- If a ZIP contains a model not already extracted, its contents are to be extracted into staging, verified, and then organized.
- If a ZIP contains additional parts or a materially different version, those differences are preserved.
- Damaged, protected, incomplete, or ambiguous archives are retained for review.
- Archive-to-extracted-package relationships are recorded rather than inferred from filenames.

AJ also raised whether tracking the relationship between retained ZIP archives and their extracted counterparts was unnecessary complexity. The conclusion was that this information was useful because it provided evidence that an archive had been fully accounted for before redundant copies could ever be considered for removal.

Metadata and portability were also discussed.

Finder tags were considered useful for **item-level discovery**, particularly for status, universe, item type, and known creator. Detailed provenance and package information belonged in a separate portable catalog rather than being encoded into a large tag vocabulary.

The pilot therefore established the concept of combining:

- the physical folder hierarchy;
- Finder tags for convenient local discovery; and
- a portable catalog record containing provenance, duplicate relationships, verification status, creator/source information when known, and package notes.

Finder tags were explicitly not treated as the sole metadata system because the library was expected eventually to move beyond one filesystem. Compatibility with future catalog systems was considered, but no later Manyfold architecture or ingestion design was established as part of this September 11 work.

## Decisions and Why They Matter

**Preservation takes priority over deduplication.** A file identified as redundant is not automatically disposable. Duplicate detection establishes relationships first; removal is a separate, later decision.

**Content determines exact duplication, not filenames.** Filename similarities such as numbered copies can identify candidates, but exact file duplication requires content comparison.

**Deduplication operates at both file and package levels.** Identical individual files do not automatically justify removing them when they belong to different complete model packages.

**The clean library uses Category → Universe/Franchise → Item.** This created a simple browsing hierarchy without requiring every useful attribute to become another folder level.

**Complete packages remain coherent.** Instructions, reference material, alternates, and related model components stay with the item rather than being scattered solely for categorical purity.

**ZIP-only models should ultimately become usable extracted packages.** Archives remain source/provenance material during verification rather than becoming the primary browsing interface.

**Uncertainty produces review, not guessing.** Ambiguous identities, classifications, versions, or package relationships remain unresolved until they can be verified.

**Metadata must be portable.** Finder tags provide useful local convenience, but important organizational and provenance information is also recorded independently so it is not dependent on one operating system's metadata.

**No broader destructive reorganization was authorized.** The validated pilot demonstrated the process; it did not constitute permission to collapse or delete the original collection.

## Options Considered or Rejected

A simple filename-based duplicate cleanup was rejected because similarly named packages could contain different versions, creator variants, alternate parts, or incomplete extractions.

Keeping ZIP archives as the primary organized library was rejected because it would leave a substantial portion of the collection difficult to browse and use.

Extracting everything indiscriminately into the permanent library was not adopted. ZIP contents were instead to be evaluated alongside existing extracted packages so unnecessary permanent duplicates would not be created.

Applying metadata only through Finder tags was rejected as insufficiently portable.

Immediate deletion of confirmed duplicates was rejected. Redundant copies were retained while the process and library structure were being validated.

A broader collection-wide sorting operation was **proposed but not executed on September 11** beyond the Tron Ares validation pilot.

## Problems, Surprises, or Course Corrections

The Tron Ares pilot demonstrated that filename duplication could substantially understate the real duplication problem: multiple extracted folders and multiple ZIP archives could all represent the same underlying package.

The first pilot layout deliberately retained redundant copies inside the pilot so verification could be demonstrated safely. Once AJ confirmed the desired end state, that layout was corrected: the browsing folder was reduced to the required model files while the redundant pilot material was retained outside the clean library.

This established an important distinction between a **verification workspace** and the **finished browsing library**.

The subsequent collection-wide operation also demonstrated the distinction between several different forms of evidence:

- the **read-only inventory/count** established the number, size, and locations of files;
- **ZIP directory inspection** established that archives could be read and their directory entries enumerated, but did not by itself verify every archived payload against an extracted package;
- **content fingerprinting** calculated file hashes for exact-content comparison and was still incomplete;
- **duplicate identification** depended on completed content comparisons rather than filename similarity alone; and
- **package verification** required comparing the contents of a specific package or archive against its counterpart, as demonstrated by the Tron Ares pilot.

The collection-wide fingerprinting pass proved significantly slower than the initial inventory and small pilot. Progress monitoring consumed assistant usage, so recurring assistant checks were paused while the local fingerprinting process continued and saved checkpoints.

## Milestones Reached

- Existing zipped and extracted source collections inspected without modifying the originals.
- **Read-only collection inventory/count established at 16,882 files totaling approximately 248.58 GB; content fingerprinting remained in progress.**
- Preservation-first operating rules established.
- Category → Universe/Franchise → Item hierarchy established.
- Exact-content duplicate-detection methodology established.
- ZIP-to-extracted-package comparison methodology established.
- Tron Ares selected and completed as the first organization pilot.
- Targeted comparison confirmed that the two extracted Tron Ares packages and three ZIP archives represented the same required model content.
- Clean-library behavior validated: one usable complete package rather than redundant archive/extracted copies.
- Finder-tag concept tested on the pilot.
- Portable catalog concept tested on the pilot.
- AJ reviewed and approved the resulting pilot pattern.
- Collection-wide content fingerprinting and ZIP directory inspection were initiated; fingerprinting remained incomplete at the September 11 stopping point.

## Current Project State

At the end of the September 11 evidence, **the Tron Ares pilot was the only model package documented as fully processed through the new organization workflow**.

The original source collections remained intact.

The **read-only inventory/count was complete**, establishing **16,882 files totaling approximately 248.58 GB**.

Separately, ZIP directory inspection had identified **339 readable archives**, representing approximately **48.4 GB of uncompressed content**. Archive readability and directory inspection did **not** establish that every archive had been fully content-verified against an extracted package.

The collection-wide **content-fingerprinting scan remained in progress**. At the September 11 stopping point:

- **13,561 of 16,882 files had been fingerprinted**
- **207.61 GB of 248.58 GB had been fingerprinted**
- the scan had reached **83.5% by data size**

The remaining files had been counted by the completed inventory but had **not yet been fingerprinted** at that stopping point.

No additional packages beyond the Tron Ares pilot had been documented as fully verified through the new organization workflow.

## Unresolved Items

The following remained unresolved at the September 11 stopping point:

- Complete the collection-wide content-fingerprinting scan.
- Use completed fingerprints to perform broader exact-duplicate analysis.
- Perform package-level comparisons between ZIP contents and existing extracted packages.
- Identify ZIP-only models requiring safe extraction.
- Identify distinct creator/version packages that must remain separate despite overlapping model content.
- Produce the broader proposed sorting map.
- Identify ambiguous items requiring AJ's classification decisions.
- Expand the validated tagging/catalog pattern beyond the Tron pilot.
- Determine which redundant archives or extracted copies might eventually be eligible for consolidation.
- Establish a verified recovery point before performing broader directory changes.

No September 12 recovery backup, September 14 Headgear checkpoint, September 15 character regrouping, September 16 Manyfold/local-processing exploration, or September 18 architecture work is part of this handoff.

## Stopping Point and Next Action

The September 11 session stopped with the **read-only collection inventory/count complete** but the separate **collection-wide content-fingerprinting scan still running at 83.5% by data size**: **13,561 of 16,882 files and 207.61 GB of 248.58 GB had been fingerprinted**.

AJ authorized continued **recoverable, non-destructive analysis** while away, but imposed a new control before the next organizational stage:

> Before moving files or changing directories, a verified backup recovery point must exist.

Accordingly, the next action from the September 11 state was to allow the existing fingerprinting scan to finish and preserve its results. Once AJ returned, ARCHIE was to review those results, identify decisions or authorizations needed, and **create and verify a recovery point before any broader file or directory changes**.

The recovery point itself had **not yet been created within the September 11 evidence**.

---

**Draft status:** **AJ REVIEW REQUIRED — not approved, committed, published, or submitted to the Clio inbox.**
