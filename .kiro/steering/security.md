---
inclusion: always
---
# Security Requirements

PiGuy operates on a real home network and must be treated as infrastructure software.

## Secrets

Never commit:
- passwords
- API keys
- authentication tokens
- private keys
- Tailscale credentials
- database credentials

Use environment variables or appropriate local secret storage.

## Network Access

Do not expose PiGuy's dashboard, API, database, or administrative interfaces to the public Internet unless an explicit future requirement calls for it and the security architecture has been reviewed. Prefer the existing trusted Tailscale access path for remote administration.

## Least Privilege

PiGuy should run with the minimum permissions necessary.

Do not require root privileges unless a specific collector genuinely needs them.

Document any privileged operation.

## Data

Collect only telemetry necessary for the project's stated functionality.

Avoid unnecessarily storing sensitive payloads or personally identifying information.

## AI

Do not send private network information to external AI services. The intended AI architecture is local AI. AI prompts should contain only the evidence required for the task.

## Validation

Treat log files and external command output as untrusted input.

Validate and sanitize data before:
- database insertion
- shell execution
- HTML rendering
- report generation
- AI prompt construction

Never construct shell commands from untrusted strings without appropriate validation.