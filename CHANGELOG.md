# Changelog

All notable changes to Amadeus NDC Fare Rules & Amenities AI Switch are documented here. The format follows [Keep a Changelog](https://keepachangelog.com/) and the project uses [Semantic Versioning](https://semver.org/).

## [1.0.0] - 2026-10-03

Initial open-source release, built for Amadeus NDC content.

### Added
- **Amenities API**: `POST /api/v1/amenities/summary` de-duplicates, classifies, shortens and translates fare-family benefit texts (per-item, per-language Redis → Postgres cache; literal `summarize=false` mode) and `POST /api/v1/amenities/fare-names` turns fare-family codes into friendly labels.
- Playground tabs for amenities and fare names, prompt editor entries for the new prompts, amenities series in usage charts, amenities cache maintenance.
- Fare-rules **summary** endpoint with desktop (table) and mobile (compact sections) layouts, multilingual output and Redis → Postgres → LLM caching by content digest.
- Fare-rules **chat** endpoint (Server-Sent Events and single-response variants) with segment-aware and date-aware reasoning over multi-segment itineraries.
- Six LLM providers behind one interface: OpenAI, Azure AI (Azure OpenAI), Anthropic Claude, Google Gemini, Groq, AWS Bedrock — configurable and testable from the admin UI, credentials encrypted at rest.
- Admin UI: overview dashboard, prompt editor (validated placeholders, live preview, reset to default), usage analytics (tokens, latency, cache hit rate, per feature/model/key), API key management, datastore management (bundled or your own Postgres/Redis with live switching and config carry-over), playground, account settings.
- Docker Compose stack (app + Postgres 16 + Redis 7) that boots with zero configuration; default admin user seeded on first start.
- Production hardening: API-key auth with hashed keys, session cookies with CSRF guard, sliding-window rate limiting, uniform error envelope, request ids, security headers, health/readiness probes.
