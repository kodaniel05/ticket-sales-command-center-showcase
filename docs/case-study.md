# Case Study: Ticket Sales Command Center

## Background

Ticket Sales Command Center is a private analytics dashboard for event-ticketing performance. The project was built around a common operational challenge: ticketing data exists, but it is often locked in CSV exports, year-specific formats, and manual reporting workflows that make trend analysis slow.

The dashboard brings those exports into a focused command-center interface where stakeholders can evaluate sales performance, buyer behavior, channel mix, and practical recommendations from one place.

## Motivation

The motivation was to replace spreadsheet-heavy reporting with a tool that felt purpose-built for event operations. Instead of asking stakeholders to inspect raw exports, the dashboard gives them a compact view of the metrics they actually need: total tickets, revenue, orders, average ticket price, event rankings, audience categories, sales channels, and purchase timing.

The project also needed to respect privacy and client constraints. The production application is private, and this public showcase intentionally documents the work without distributing the source code or data.

## Problem

The core problem was not just visualization. The harder problem was making operational data usable:

- Historical CSVs may not share an identical column layout.
- Raw fields need to be normalized before meaningful comparison.
- Stakeholders need both high-level KPIs and drill-down context.
- Sensitive buyer and sales data must not be exposed publicly.
- The final deliverable needs to run in a controlled private environment.

## Solution

The solution is a private static analytics dashboard with a build-time data preparation flow. Approved CSV exports are processed during packaging, sanitized, bundled into the private static build, and served internally. In the browser, the dashboard computes aggregate views and presents them through a polished React interface.

The result is a lightweight deployment model: internal users can access the dashboard through private hosting without installing Node.js, connecting to a database, or running a custom backend.

## Main Features

- Multi-year sales analysis with all-years and individual-year views.
- Executive KPI strip for sales, revenue, orders, price, segment, channel, and timing.
- Event performance ranking by ticket volume and revenue.
- Audience category and purchase-location breakdowns.
- Purchase timing views by hour, weekday, and days before event.
- Year-over-year context for single-year analysis.
- Deterministic suggestion engine for operational recommendations.
- Admin-oriented CSV upload mode for local exploration and future-year testing.
- Private static packaging workflow for internal handoff.

## Design Decisions

The interface was designed as an operational dashboard rather than a marketing page. The layout prioritizes density, quick scanning, and repeated use:

- A sticky header keeps the year filter available at all times.
- KPI cards provide immediate context before detailed charts.
- The main grid groups performance, breakdown, timing, and suggestions together.
- A compact summary table gives stakeholders a text-based fallback to chart views.
- Visual emphasis is reserved for decisions and comparisons, not decoration.

## Technical Decisions

The application uses Next.js, React, TypeScript, Tailwind CSS, Recharts, and Papa Parse. That stack made sense because the product needed a responsive dashboard UI, typed data transformations, charting primitives, and robust CSV ingestion without requiring a complex backend.

Key technical choices included:

- **Static delivery:** Reduces hosting complexity for private client environments.
- **Build-time bundling:** Keeps raw CSV files out of the public web directory.
- **Sanitization before browser delivery:** Reduces exposure risk in the static artifact.
- **Client-side aggregation:** Keeps runtime infrastructure simple while making year switching fast.
- **Deterministic recommendations:** Makes suggestion output explainable and repeatable.
- **Separation of client and admin modes:** Keeps upload workflows out of normal private client use.

## Challenges

The main engineering challenges were around data quality, privacy boundaries, and product clarity.

Historical ticket exports were not perfectly uniform, so the private application needed normalization logic that could interpret approved source files consistently. The dashboard also had to avoid creating a false sense of security: static sites still deliver data to the browser, so the build artifact and internal URL need to remain private.

Another challenge was making the dashboard useful without overwhelming users. The final layout balances executive-level metrics with enough operational detail to support real decisions.

## Lessons Learned

- A small static dashboard can still require serious privacy and handoff discipline.
- Public portfolio material for private projects should describe outcomes, architecture, and tradeoffs without exposing reusable implementation.
- Deterministic recommendation logic can be more appropriate than AI for stakeholder analytics when trust and repeatability matter.
- Sanitization is not the same as public release; browser-delivered data must still be treated as private.
- The best dashboards help users decide what to do next, not just what happened.

## Impact

The project turns raw ticket-sales exports into a repeatable analysis workflow. It reduces manual spreadsheet work, improves visibility into season-over-season performance, and gives stakeholders a clearer way to discuss event demand, channel strategy, audience mix, and purchase timing.

From an engineering perspective, the project demonstrates full-product thinking: data preparation, privacy constraints, UI design, deployment model, stakeholder workflows, and maintainable documentation.

## Future Roadmap

- Persistent server-side admin uploads with access control.
- Expanded validation for future ticketing export formats.
- Additional trend views for campaign windows and buyer cohorts.
- Synthetic demo dataset for public portfolio walkthroughs.
- Exportable executive reports for meetings and sponsor conversations.
- Automated smoke tests for packaging and static build integrity.

