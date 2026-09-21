# ENTRY 011 - AJ's Development Chronicle - September 11, 2026 - The Library Stops Being a Pile of Files

**Entry:** 011  
**Work Date:** 2026-09-11  
**Generated:** 2026-09-20, America/Los_Angeles  
**Projects Covered:** ARCHIE  
**Subjects Covered:** Actus 3D library, preservation-first organization, duplicate analysis, Tron Ares pilot  
**Source Handoffs:** `HANDOFF - 2026-09-11 - ARCHIE - Actus 3D Library Organization Begins.md`  
**Status:** Approved Chronicle Entry

By September 11, ARCHIE had moved from managing individual collection decisions to confronting the collection itself.

Actus contained two broad source populations—unzipped files and ZIP archives—and a lot of accumulated history inside them. Helmets, armor, weapons, figures, props, and other printable models were there, but "there" was doing a great deal of work. AJ wanted a library that could actually be browsed and trusted without sacrificing models in the process.

So the first rule was the one that mattered most: **do not lose anything while figuring this out.**

We began read-only. The initial inventory counted **16,882 files totaling about 248.58 GB**, with no read errors during that pass. That told us what existed and where; it did not magically mean every file had already been fingerprinted or verified.

For the clean library, AJ and ARCHIE settled on **Category → Universe/Franchise → Item**. Categories could cover Headgear, Armor, blasters, bladed weapons, props, figures, displays, practical prints, and similar groups. The hierarchy was intentionally simple. Useful metadata did not all need to become another folder.

The preservation rules around it were less simple, because real 3D model collections are rarely polite.

Complete packages had to stay complete. Instructions, images, alternate parts, creator information, and related files belonged with the model. Two files with similar names were not duplicates merely because Finder thought so. Distinct creators and versions remained distinct. Full armor kits stayed intact instead of being cannibalized for individual categories. And when we did not know what something was, it went to review instead of receiving an imaginative new identity.

Exact duplication required content fingerprints.

The first test was a **Tron Ares Helmet** package. Two extracted packages and three ZIP archives appeared to represent the same helmet. Targeted comparison confirmed that they contained the same required model content.

We still did not delete anything.

Instead, the pilot copied material into the developing organized area and verified those copies against the originals. The first version intentionally retained the comparison copies so AJ could inspect what the process was doing. Once AJ confirmed that the desired end state was one usable package rather than five representations of the same thing, the clean Tron Ares folder was reduced to the two required model parts. The redundant pilot copies moved to a holding area. The originals remained untouched.

That distinction—**verification workspace versus finished browsing library**—was important. So was the treatment of ZIP files. ZIPs were source packages, not the desired browsing experience. A ZIP matching an extracted package could be accounted for without becoming another permanent copy. A ZIP-only model would eventually need safe extraction and verification. Additional parts or materially different versions had to survive.

Finder tags could help with convenient local discovery, but AJ did not want the library's meaning trapped in one operating system. Provenance, duplicate relationships, creator information, and verification state therefore also needed a portable catalog.

Then we scaled the analysis up.

The collection-wide fingerprinting pass turned out to be much slower than the initial inventory—because hashing a quarter-terabyte collection is, inconveniently, actual work. By the September 11 stopping point, **13,561 of 16,882 files** and **207.61 GB of 248.58 GB** had been fingerprinted, reaching **83.5% by data size**. Separately, **339 readable ZIP archives** had been inventoried, but that did not mean their payloads had all been matched to extracted packages.

The Tron Ares pilot remained the only package documented as fully processed through the new workflow.

Before AJ would allow broader file or directory changes, he added one more gate: **a verified recovery point had to exist first.**

So September 11 ended with the method proven on one helmet, the larger scan still running, and the originals intact.

We finally had a plan for turning the pile into a library.

Before touching the pile, though, we were going to make very sure we could put it back.
