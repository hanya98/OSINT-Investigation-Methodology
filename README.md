# OSINT-Investigation-Methodology
OSINT Investigation Methodology: Reconstructing Adversarial Ecosystems from Fragmented Public Data
# OSINT Investigation Methodology: Reconstructing Adversarial Ecosystems from Fragmented Public Data

## Problem framing

A recurring challenge in threat intelligence work is that the systems worth investigating — fraud
schemes, informal resale markets, deceptive platforms — are, by design, adversarial toward
observation. Evidence is scattered across corporate registries, payment processors, app stores,
review platforms, and complaint forums, each with its own reliability profile, and each partially
adversarial (the entities involved have an incentive to obscure structure). The core question this
methodology addresses: **how do you reconstruct the structure of a harmful ecosystem from
public information that is incomplete, adversarial, and produced by many uncoordinated
sources?**

This writeup describes the general approach, independent of any specific investigation.

## Methodology

### 1. Multi-source triangulation

No single source is treated as authoritative. Findings are corroborated across source types that
have different failure modes:

- **Corporate/registry data** — legal entity structure, officers, filing history. Reliable for "does
  this entity exist and who's behind it," weak on operational behavior.
- **Payment and billing patterns** — merchant names, charge amounts, timing sequences drawn
  from aggregated complaint data. Reveals operational structure that registries don't.
- **Infrastructure data** — domains, hosting, app-store listings. Useful for mapping the technical
  footprint and spotting newly-registered infrastructure that correlates with a change in
  behavior.
- **Review-platform and complaint-forum data** — high volume, self-selected and noisy, but
  useful for detecting a pattern once you know what to look for, and for corroborating a
  transaction pattern seen elsewhere.

A finding only gets weight when at least two independent source types agree on it.

### 2. Dark-pattern taxonomy

Rather than describing findings in ad hoc language, behaviors are classified against an
established framework (drawing on the FTC's negative-option / click-to-cancel guidance and
equivalent UK/EU consumer-protection principles):

- **Sneaking** — material terms (e.g. auto-renewal) not clearly disclosed at the point of
  transaction.
- **Obstruction** — a cancellation or opt-out path that exists nominally but doesn't function.
- **Roach motel** — asymmetric friction: trivial to enter, deliberately hard to exit.
- **Forced continuity** — a trial or low-cost entry point converts into a recurring commitment
  without a clear, informed opt-in step.

Classifying against a named taxonomy rather than free text makes findings comparable across
investigations and easier for a non-specialist reviewer (e.g. a payment processor's trust & safety
team) to act on.

### 3. Trust-signal analysis

A pattern that recurs across otherwise-unrelated investigations: platforms operating in a legal or
ethical grey zone substitute **social trust signals** — reputation scores, testimonials, account
longevity, review volume — for the guarantees a legitimate marketplace would otherwise provide
(escrow, verified identity, enforceable terms). Treating trust signals as infrastructure, rather than
as incidental marketing, helps explain why inflated ratings on one platform (e.g. an app store)
can coexist with a strongly negative pattern on an unsolicited-review platform — the two serve
different functions in the ecosystem rather than simply disagreeing.

### 4. Reproducibility: the evidence matrix

The main methodological gap in fast-turnaround OSINT work is that conclusions often live in an
analyst's head rather than in an auditable structure. The fix under development here is an
explicit evidence matrix:

- Every claim is logged against its supporting source(s), with a source-reliability tier and a
  confidence level (high/medium/low) rather than presented as flat fact.
- Contradictory evidence is logged alongside supporting evidence, not discarded, so a reviewer
  can see what was weighed and why one reading won out.
- The goal is that a second investigator working from the same evidence matrix reaches the
  same conclusions — the test of a reproducible finding rather than a persuasive one.

## Limitations

- Public-data OSINT can establish a strong behavioral pattern; it cannot substitute for legal
  process (subpoenaed records, sworn testimony) when intent or liability needs to be proven
  to an evidentiary standard.
- Review-platform data is self-selected and skews negative; it corroborates a pattern but
  shouldn't be used to estimate its magnitude on its own.
- This document intentionally omits case-specific identifying details (entity names, exact
  figures, source URLs) from any live or client investigation — it describes the method, not a
  finding.

## Why this matters

Fraud and dark-pattern schemes are usually investigated one complaint at a time by whoever
happens to be the victim. A structured, reproducible OSINT methodology lets a single analyst (or
a small team) produce a submission-ready case — for a payment processor, a regulator, or a
consumer-protection body — that stands up to scrutiny even though no single piece of evidence
was, on its own, conclusive.
