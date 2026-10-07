# CCP-Assure demo

A public static design-time cyber-assurance demonstrator for an illustrative cFS-style reference satellite.

- `index.html` is the interactive spacecraft/system view, ranked attack graph, and step-through simulation.
- `assurance-review.html` is the companion evidence/report view.
- `examples/grounded/SOURCES.md` records the supplied grounding and citation limitations.

The current implementation is the C09 design-time analysis slice supporting C03 G05 ground analytics and G07 assurance records. Select an attack path and advance its techniques to see modeled state changes. Toggle attacker starting facts to re-search. The authenticated-commanding + anti-replay switch removes the modeled replay and forged-command techniques to show a design what-if; this is an explicit assumption and does not simulate cryptography.

This is not an operational digital twin. It has no live telemetry, spacecraft connection, onboard agents, or recovery control. Attack paths are the cheapest routes found in the hand-authored technique library. Costs are not probabilities. SPARTA identifiers remain marked unverified; NIST control associations are indicative; SPACE-SHIELD is unmapped. Confirm exact citations before presenting the supplied evidence as authoritative.

All browser behavior and data are embedded locally. No application server or runtime network connection is used.
