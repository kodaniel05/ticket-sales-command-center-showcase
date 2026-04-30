# Engineering Decisions

## Documentation-Only Public Repository

The most important decision for this showcase is that the public repository is documentation-only. The private project contains application code, client data handling, and release packaging logic that should not be redistributed.

This repository focuses on communicating:

- Product value
- Feature scope
- Architecture
- Data-handling strategy
- Engineering tradeoffs
- Future roadmap

## Static Deployment Model

The private application is packaged as a static site for internal hosting. This reduces operational overhead for end users because they do not need Node.js, a database, or an application server.

Tradeoff: static dashboards deliver data to the browser. The project therefore treats the static artifact and private URL as confidential, even after build-time sanitization.

## Build-Time Data Preparation

Approved ticket-sales exports are processed during packaging rather than fetched from a runtime API. This matches the private hosting model and makes the dashboard easy to hand off to internal IT/admin teams.

The build process is responsible for preparing only the approved data needed by the dashboard.

## Sanitization Before Browser Delivery

Sensitive fields are reduced or anonymized before the browser data bundle is created. This limits exposure in the static artifact while preserving the aggregate analytical value needed for the dashboard.

This is a privacy control, not a public-release guarantee. Browser-delivered data remains inspectable by anyone with access to the private dashboard.

## Client-Side Aggregation

The dashboard computes derived views in the browser from the sanitized bundle. This keeps runtime infrastructure simple and makes filtering responsive.

Computed views include:

- KPI summaries
- Event rankings
- Category breakdowns
- Purchase-location breakdowns
- Timing buckets
- Prior-year comparisons
- Recommendation inputs

## Deterministic Recommendation Rules

The recommendation layer uses deterministic business rules instead of AI-generated text. This was chosen because the product is stakeholder-facing and recommendations should be explainable, consistent, and auditable.

The rules inspect aggregate patterns and return concise operational prompts.

## Separate Client And Admin Modes

The private application distinguishes between normal client use and local/admin exploration. Upload controls are hidden in client mode because browser-only uploads do not persist after refresh.

This avoids presenting an exploratory workflow as a durable production feature.

## Compact Dashboard Layout

The interface prioritizes quick scanning over decorative presentation. The first screen combines:

- Persistent context and year selection
- KPI row
- Event performance chart
- Category and channel breakdowns
- Purchase timing analysis
- Suggestions
- Compact summary table

This supports a realistic stakeholder workflow: scan, compare, diagnose, decide.

## Technology Choices

| Decision | Rationale |
| --- | --- |
| Next.js and React | Strong fit for a polished static dashboard UI |
| TypeScript | Safer data transformations and clearer model boundaries |
| Tailwind CSS | Fast, consistent styling for dense operational UI |
| Recharts | Practical charting library for dashboard views |
| Papa Parse | Mature CSV parsing for browser and build workflows |
| Static hosting | Simple private deployment without runtime infrastructure |

## Public Showcase Constraints

This showcase avoids:

- Copying source files
- Publishing data samples from the private project
- Reproducing proprietary parsing code
- Including build artifacts
- Revealing internal URLs or deployment details
- Naming private client-specific details unless explicitly approved

