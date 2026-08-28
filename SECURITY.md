# Security Policy

## Scope

CreatorBoost handles Google OAuth credentials and Google Ads API credentials. Protecting those credentials is a core deployment requirement.

## Never commit secrets

Do not commit or publish:

- Google OAuth client secrets
- Google Ads developer tokens
- OAuth access tokens
- OAuth refresh tokens
- `SESSION_SECRET`
- service-account keys
- private keys or certificates
- database passwords or connection strings

Use environment variables or a production secret manager.

## If a credential is exposed

1. Revoke or rotate the affected credential immediately.
2. Remove the secret from the repository and Git history where appropriate.
3. Update the production deployment with the replacement credential.
4. Review API and OAuth activity for unexpected use.

Google recommends treating OAuth credentials and Google Ads developer tokens as passwords. See the official Google Ads API credential-security documentation before deploying the application.

## Reporting a vulnerability

For security issues affecting the deployed CreatorBoost service, contact the application operator through the contact address published on the live site:

https://kgameradda.com/contact.html
