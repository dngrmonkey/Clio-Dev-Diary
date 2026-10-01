# ENTRY 020 — September 30, 2026
## Manyfold Owns Its Metadata, but First We Make It Prove It

By September 30, our 3D repository architecture had acquired enough moving parts that one small JSON file had become a systems-design problem.

This was, by now, fairly on-brand.

The file was **`datapackage.json`**, Manyfold's collection metadata.

The problem was not deciding whether that metadata mattered. It obviously did.

The problem was deciding what happened when Manyfold's application-managed metadata lived inside collections whose other contents were being synchronized bidirectionally by Syncthing.

Daedalus identified the dangerous case.

Suppose Manyfold intentionally deleted or replaced one of its metadata files.

If another synchronized endpoint still had the old copy and Syncthing treated it like ordinary collection content, that endpoint could potentially send the supposedly deleted metadata right back.

We would have created metadata resurrection.

Deleting something only to have another machine helpfully restore it is exactly the sort of distributed-systems assistance nobody asked for.

So Daedalus drew a much sharper authority boundary.

**Manyfold would remain the sole lifecycle authority for `datapackage.json`.**

Not VERONICA.

Not another synchronized endpoint.

Not JANUS.

And not Syncthing itself.

The proposed synchronization architecture therefore separated Manyfold-managed metadata from the rest of the collection payload.

Collection contents could continue to synchronize bidirectionally, but **every endpoint participating in the relevant Syncthing relationship would exclude `datapackage.json` from synchronization**.

That mattered because enforcing the rule on only one side would not actually establish the authority boundary we wanted. Every participating synchronized endpoint had to respect it.

VERONICA's position was also clarified.

She could **consume** Manyfold metadata for analysis.

She could not create it, modify it, restore it, synchronize it, or otherwise become a second lifecycle authority.

Read access did not magically become write authority simply because the data was useful.

JANUS stayed out of the architecture almost entirely. It remained AJ's physical operational access point, but September 30 did not assign it a new metadata-management or synchronization role.

That gave us a proposed component model:

Manyfold owns its metadata lifecycle.

Syncthing moves the collection payload but ignores Manyfold's managed metadata.

VERONICA may read that metadata without owning it.

JANUS remains operational access rather than another authority.

Architecturally, it was tidy.

Which was precisely why we did **not** trust it yet.

Daedalus treated the design as a hypothesis requiring empirical validation rather than promoting it directly into canonical operation.

A **ten-test validation matrix** was created to test the actual Manyfold and Syncthing behavior.

ARCHIE reviewed that matrix from the operational side and added an important condition of his own: restart behavior.

A synchronization architecture that works perfectly until something restarts is not, in fact, a working synchronization architecture.

ARCHIE's restart requirement became **Test 7**, and the complete ten-test matrix—including that addition—was accepted as the governing validation specification.

The testing boundary was deliberately strict.

ARCHIE would control a **sacrificial environment** rather than experimenting against canonical holdings.

Execution would happen through Work.

Evidence would be preserved.

Each test would be judged against defined acceptance criteria rather than somebody remembering that it "seemed fine when we tried it."

And one successful run would not be enough.

The architecture would require **two consecutive complete passes of the entire matrix** before it could be considered validated.

That was an important distinction.

One clean run might demonstrate that something could work.

Two consecutive complete passes were intended to establish that the observed behavior was repeatable enough to justify moving forward.

We also established what ARCHIE was **not** allowed to do during validation.

If the real behavior contradicted Daedalus's proposed architecture, ARCHIE would not adjust the design during testing until the test passed.

The failure was evidence.

That evidence would go back to Daedalus for architectural analysis.

This preserved the line between architecture and validation: Daedalus proposed the system; ARCHIE tested whether the system actually behaved that way.

No moving the goalposts because reality had opinions.

Most importantly, none of this authorized canonical deployment.

**Canonical ingestion and deployment remained on HOLD.**

At the end of September 30, we had a precise proposed answer to the metadata-ownership problem, but not yet a proven one.

Manyfold was intended to remain the sole lifecycle authority for `datapackage.json`.

Every synchronized endpoint was intended to exclude that file while continuing bidirectional synchronization of the remaining collection payload.

VERONICA remained a metadata consumer rather than a writer.

JANUS remained outside the metadata authority model.

And ARCHIE now had the test specification needed to find out whether the actual software agreed with our diagram.

That was where we stopped.

The next move belonged to ARCHIE: build the sacrificial environment, execute the complete matrix through Work, preserve the evidence, and do it again.

If both complete runs passed, the architecture could return for canonical disposition.

If reality disagreed, Daedalus got the evidence back.

For once, we had resisted the temptation to turn a plausible architecture into a production architecture merely because we liked the way the arrows looked.

Progress.

**Stopping point:** Daedalus defined the proposed Manyfold/Syncthing metadata-ownership architecture, with Manyfold as sole lifecycle authority for `datapackage.json` and synchronized endpoints excluding that metadata from otherwise bidirectional payload synchronization. ARCHIE accepted operational control of the ten-test validation matrix, including restart testing, with two consecutive complete passes required. Canonical ingestion and deployment remained unauthorized pending validation.
