# CreatorBoost

CreatorBoost is a Next.js workspace for creators that combines channel analytics, video planning, SEO research, campaign planning, Google Ads campaign management, forecasting, and reporting in one application.

**Live product:** https://kgameradda.com/

> CreatorBoost is an independent application and is not affiliated with or endorsed by Google.

## Product scope

CreatorBoost is designed as an end-to-end creator marketing workspace. The Google Ads module is intended to support an advertiser through a campaign lifecycle rather than provide keyword research alone.

### Google Ads capabilities

- Google OAuth 2.0 connection
- Google Ads account/customer configuration
- Campaign listing and refresh
- Campaign search and status summaries
- Campaign creation workflow
- Campaign budget configuration
- Location and language targeting
- Ad group creation
- Keyword and negative-keyword planning
- Responsive Search Ad fields
- Paused-first campaign deployment for user review
- Campaign enable/pause/remove controls
- Campaign performance metrics
- Forecasting workflow

### Creator workspace modules

- Dashboard
- YouTube channel connection and analytics
- Videos
- Discovery
- SEO Studio
- Content Ideas
- Analytics
- Google Ads Campaign Planner
- Google Ads Campaign Manager

## Application routes

| Route | Purpose |
| --- | --- |
| `/` | Public product landing page |
| `/dashboard` | Creator dashboard |
| `/ads-planner` | Campaign planning and keyword workflow |
| `/ads` | Google Ads campaign management |
| `/analytics` | Analytics workspace |
| `/videos` | Video management |
| `/seo` | SEO workspace |
| `/privacy.html` | Privacy Policy |
| `/terms.html` | Terms of Service |
| `/contact.html` | Contact page |
| `/google-api.html` | Google API disclosure |

## Google Ads API routes

The server-side API layer includes routes for:

- Google Ads account information
- Campaign creation
- Campaign status changes
- Forecasting
- SEO/keyword integration where configured

OAuth tokens are handled server-side. The browser does not receive the Google Ads developer token or OAuth client secret.

## Technology

- Next.js 15
- React 19
- TypeScript
- Google OAuth 2.0
- Google Ads REST API
- YouTube / YouTube Analytics APIs
- Lucide React

## Local development

### 1. Install dependencies

```bash
npm install
```

### 2. Create environment configuration

Copy `.env.example` to `.env.local` and replace the placeholders with your own credentials.

```bash
cp .env.example .env.local
```

Required server-side configuration:

```text
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
GOOGLE_REDIRECT_URI=
SESSION_SECRET=
GOOGLE_ADS_DEVELOPER_TOKEN=
GOOGLE_ADS_CUSTOMER_ID=
GOOGLE_ADS_LOGIN_CUSTOMER_ID=
GOOGLE_ADS_LANGUAGE_ID=1000
GOOGLE_ADS_GEO_TARGET_ID=2840
GOOGLE_ADS_API_VERSION=v25
```

For Google Ads API calls made through a manager account, `GOOGLE_ADS_LOGIN_CUSTOMER_ID` should be the manager customer ID. The client account being managed belongs in `GOOGLE_ADS_CUSTOMER_ID`.

### 3. Start the application

```bash
npm run dev
```

Open `http://localhost:3000`.

## Google Ads development and testing

Use Google Ads test accounts while developing campaign creation and management. Do not use a production account for destructive tests.

CreatorBoost creates new campaign structures paused so the advertiser can review the configuration before activation.

A Google Ads developer token is required for API requests. Production-account access depends on the access level assigned to that token.

## Security

**Never commit secrets.** The following must remain outside Git:

- `.env.local`
- Google OAuth client secrets
- Google Ads developer tokens
- OAuth access tokens
- OAuth refresh tokens
- session secrets
- private keys
- database credentials

See [SECURITY.md](SECURITY.md) for the repository security policy.

Google's Google Ads API documentation explicitly recommends treating OAuth credentials and developer tokens like passwords and not committing them to public repositories.

## Google review / compliance materials

The deployed application includes public policy and disclosure pages:

- Privacy Policy: https://kgameradda.com/privacy.html
- Terms: https://kgameradda.com/terms.html
- Contact: https://kgameradda.com/contact.html
- Google API Disclosure: https://kgameradda.com/google-api.html

The `docs/` directory contains implementation notes for the current campaign manager and forecasting modules.

## Repository status

This repository is prepared as a public source repository for the CreatorBoost application. Credentials and deployment secrets are intentionally excluded.
