# Sources & provenance — CCP-Assure grounded example

All grounding below is from public sources. Verify exact citations before
external publication; confidence levels are recorded per item in `evidence.json`.

## SPARTA technique taxonomy (technique_library.json)

- **SPARTA — Space Attack Research and Tactic Analysis**, The Aerospace
  Corporation. Technique IDs (EX-0001 Replay, EX-0009 Exploit Code Flaws,
  EX-0012 Modify On-Board Values + subsystem sub-techniques, EX-0013 Flooding,
  EX-0014 Spoofing + PNT sub-technique, EX-0016 Jamming, EX-0017 Kinetic
  Physical Attack, EX-0005 Exploit Hardware and Firmware Corruption, and the
  Initial Access / Impact tactics) are from the public SPARTA matrix.
  Primary: https://sparta.aerospace.org/ and https://aerospace.org/SPARTA
  Transcribed via a secondary SPARTA matrix guide; **cross-check against the
  authoritative SPARTA STIX export before flipping `sparta_verified` to true.**
- NIST 800-53 Rev 5 control identifiers are real NIST controls; their assignment
  to techniques here is **engineering judgment (indicative)**, not SPARTA's
  official control crosswalk.
- ESA SPACE-SHIELD: **not integrated** (`SS-NOT-MAPPED`).

## Incident & vulnerability evidence (evidence.json)

- **ViaSat / KA-SAT incident**, 24 Feb 2022 — "AcidRain" wiper delivered via the
  ground/management network disabled tens of thousands of Surfbeam2 modems
  across Europe. ViaSat public statement (Mar 2022); SentinelLabs "AcidRain"
  analysis; EU/US/UK attribution (May 2022). Grounds the denial-of-service and
  ground-segment vectors (PUB-dos).
- **Hack-A-Sat** (DARPA / US Space Force CTF, 2020–2023) — public challenges and
  write-ups demonstrating flight-software and ground-system exploitation,
  including NASA cFS-style stacks. Grounds code-flaw and fault-injection
  evidence (PUB-cfs-parser, HW-glitch01).
- **GNSS/GPS spoofing** — well-documented (UT Austin spoofing demonstrations;
  observed maritime/aviation spoofing incl. Black Sea anomalies, 2016+).
  Grounds PNT spoofing evidence (PUB-gnss-spoof).
- **ASAT / kinetic** — destructive anti-satellite tests are real (2007 CN, 2021
  RU debris-generating tests). Co-orbital denial of *this* mission is modeled and
  **gated out** of the default threat model (ASSUMPTION-kinetic).
- **TT&C command authentication weakness** — recognized class; many legacy
  spacecraft lack authenticated commanding (motivates CCSDS SDLS). Grounds
  replay/forgery evidence (PUB-cmd-auth).

## How to certify (move from "real ids" to "verified")

1. Download the SPARTA STIX 2.1 bundle from sparta.aerospace.org (free).
   *(Note: this coding sandbox's network is allowlisted and may block that host;
   attach the file to the build instead.)*
2. Run `report/sparta.py build_map_from_stix(<bundle>)` and confirm each
   technique id in `technique_library.json` resolves to the expected name.
3. Flip `sparta_verified: true` only for ids that resolve, and replace the
   indicative NIST controls with SPARTA's own countermeasure→control crosswalk.
