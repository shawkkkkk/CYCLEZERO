# Security

CYCLE ZERO is an experimental autonomous software system.

## Reporting a vulnerability

Please do not publicly disclose a vulnerability that could expose credentials, private runtime configuration, administrative controls, user data, or production infrastructure before the operator has had a reasonable opportunity to investigate it.

Open a minimal GitHub issue only if the report contains no sensitive exploitation details. For sensitive reports, contact the project operator privately through the project's public contact channel.

## Secrets

Never commit:

- API keys
- database credentials
- session secrets
- admin passwords
- OAuth tokens
- deployment credentials
- private production configuration

All production secrets must be provided through the deployment environment.

## Generated content

AI-generated files and messages are untrusted input. Production code should treat them as data, not executable authority.

Generated content must not be allowed to:

- access environment secrets
- change deployment credentials
- bypass admin authentication
- execute unrestricted host commands
- expose private server configuration
- silently expand its own external permissions

## Research and external services

External research and social integrations should be bounded, rate-limited, and isolated from privileged configuration.

## Disclosure

This project is an experiment. Generated beliefs, interpretations, and statements are not endorsements or factual claims by the project operator.
