---
inclusion: always
---
# PiGuy Architecture

## Architectural Layers

PiGuy should generally follow this flow:

    Data Sources
         ↓
    Collectors
         ↓
    Normalization
         ↓
    Storage
         ↓
    Deterministic Analysis
         ↓
    Correlation / Incident Model
         ↓
    Local AI Interpretation
         ↓
    CLI / Dashboard / Reports

## Collectors

Collectors are responsible only for obtaining data from an external source.

Examples:
- Pi-hole DNS logs
- Raspberry Pi system metrics
- Network interface information
- Tailscale status
- Other network telemetry added later

Collectors should not contain AI logic. Collectors should return structured Python data rather than raw strings whenever practical.

## Analysis

Analysis should be deterministic whenever possible.

Examples:
- DNS failure rate
- Query volume changes
- Repeated SERVFAIL responses
- Repeated NXDOMAIN responses
- Sudden changes in query behavior
- Interface state changes
- Connectivity failures
- Temporal correlation between events

Analysis functions should be small, deterministic, and independently testable.

## Local AI

The AI layer receives structured evidence and produces:
- possible explanations
- investigation summaries
- prioritized observations
- human-readable incident reports

The AI layer must not directly modify telemetry or database records without an explicit application-level operation.

## Database

Use SQL for persistent application data.

Prefer SQLite initially unless a concrete requirement requires another database. Database access should be isolated from collectors and presentation code.

## CLI

The CLI should be useful during development and troubleshooting.
Example conceptual commands:
    piguy collect
    piguy analyze
    piguy diagnose
    piguy report
    piguy status

Exact command names may evolve through specs.

## Dashboard

The dashboard should consume application/database data rather than
duplicating collection or analysis logic. The dashboard is a presentation layer. The dashboard should be hosted on the local network such that a user on the same Wi-Fi network can access it. It should use a very simple and modern front-end Python framework.

## Error Handling

External failures should be represented explicitly.
A collector failure must not silently appear as "zero events."

Distinguish:
- no data
- zero events
- collection failure
- malformed data
- unavailable source
- analysis failure

## Dependency Policy

Prefer the Python standard library where it is reasonable. Third-party dependencies require a concrete benefit. Every dependency should have a documented purpose.