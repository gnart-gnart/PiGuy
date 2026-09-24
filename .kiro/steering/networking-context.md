---
inclusion: always
---
# Networking Context

PiGuy is primarily a networking/observability project.

## Core Concepts

The implementation and documentation should use correct terminology for:
- DNS
- DHCP
- IP addressing
- IPv4/IPv6
- TCP/UDP
- ICMP
- routing
- NAT/PAT
- interfaces
- ports
- sockets
- latency
- packet loss
- availability
- connectivity
- VPNs
- DNS response codes

## Pi-hole

Pi-hole is an important telemetry source. PiGuy should treat Pi-hole data as evidence about DNS behavior, not as a complete representation of the entire network.

A DNS anomaly does not automatically prove that the underlying network is broken.

## Tailscale

Tailscale provides remote access to the environment.

PiGuy should distinguish:
- local network connectivity
- DNS availability
- Internet connectivity
- Tailscale connectivity
- application availability

These are separate failure domains.

## Troubleshooting Method

Network investigations should generally follow:
1. Define the symptom.
2. Establish the time window.
3. Identify affected resources.
4. Collect observable evidence.
5. Check basic connectivity.
6. Check DNS behavior.
7. Check routing/interface state.
8. Correlate events.
9. Form hypotheses.
10. Test hypotheses against available evidence.
11. Document the conclusion and remaining uncertainty.

Never jump directly from one log entry to a root-cause claim.

## Incident Language

Prefer:
"Evidence suggests..."
"Observed..."
"During the affected window..."
"One possible explanation is..."
"Insufficient evidence to determine..."

Avoid unsupported statements such as:
"The router caused the outage."
unless the available evidence actually establishes that conclusion.