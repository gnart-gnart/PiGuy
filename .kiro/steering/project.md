---
inclusion: always
---
# PiGuy — Project Steering

## Project Identity

PiGuy is a Raspberry Pi-based network observability and troubleshooting
assistant built around an existing Pi-hole installation.

The primary goal is to collect, normalize, analyze, persist, and visualize
network/DNS telemetry so that recurring network problems can be investigated
using evidence rather than guesswork.

PiGuy is also a learning project. The implementation should strengthen the
developer's Python, data structures, algorithms, networking, troubleshooting,
SQL, testing, and software-engineering skills.

## Existing Environment

The primary device is a Raspberry Pi 4.

Existing infrastructure includes:

- Pi-hole
- Tailscale VPN
- Network-wide DNS filtering
- DNS query logging
- Raspberry Pi system/network interfaces
- Existing home-network gateway infrastructure

Do not invent hardware, network topology, services, APIs, or telemetry sources
that have not been verified.

## Primary Goals

PiGuy should eventually be capable of:

1. Collecting Pi-hole DNS telemetry.
2. Collecting relevant Raspberry Pi system/network telemetry.
3. Persisting normalized observations in SQL.
4. Detecting anomalies and recurring patterns.
5. Correlating related events.
6. Producing evidence-based incident summaries.
7. Using a local AI model to assist with interpretation and reporting.
8. Providing a remotely accessible dashboard.
9. Operating reliably as a long-running service.
10. Producing useful troubleshooting records that resemble real NOC/IT
   incident investigation.

## Engineering Principles

- Evidence before conclusions.
- Deterministic analysis before AI interpretation.
- Prefer simple implementations before abstractions.
- Do not add dependencies without a concrete reason.
- Do not invent data.
- Do not silently discard errors.
- Fail explicitly and log useful diagnostic information.
- Every externally observable behavior should be testable where practical.
- Configuration belongs outside application logic.
- Secrets must never be committed to source control.

## AI Principles

The local AI is an analysis and reporting assistant, not the source of truth.

The deterministic application layer must provide the evidence supplied to the
AI.

AI-generated conclusions must be distinguishable from directly observed facts.

The AI must not claim that a network problem exists unless supporting evidence
is available.

When evidence is insufficient, the system should explicitly report that
there is insufficient evidence.

## Development Philosophy

PiGuy should remain understandable to one developer.

Avoid unnecessary enterprise architecture, microservices, message brokers,
container orchestration, or complex frameworks unless the project develops a
specific requirement for them.

Start with a modular Python application and evolve the architecture only when
real requirements justify it. 