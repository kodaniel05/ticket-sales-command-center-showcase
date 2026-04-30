# Future Improvements

## Product Improvements

- Add role-based admin workflows for data upload, validation, and approval.
- Add persistent server-side storage for future-year datasets.
- Add campaign-period analysis to connect marketing activity with ticket-sales lift.
- Add buyer cohort analysis using approved anonymized dimensions.
- Add seat tier, price tier, or package-level analysis if approved by stakeholders.
- Add exportable executive summaries for meetings and sponsor updates.

## Engineering Improvements

- Add a server-side API for admin-only uploads and audit logs.
- Add automated CSV schema validation before packaging.
- Add static build smoke tests to verify the handoff artifact before delivery.
- Add synthetic demo data generation for public screenshots and portfolio demos.
- Add test coverage around edge cases in date parsing and format normalization.
- Add observability for private hosted deployments if a server-backed model is introduced.

## Security And Privacy Improvements

- Add formal redaction checks before screenshots are published.
- Add artifact scanning to detect accidental raw data or secrets.
- Add a release checklist for private handoffs.
- Add stronger environment separation between local/admin and client modes.
- Add authentication and authorization if the dashboard moves beyond static hosting.

## UX Improvements

- Add saved views for common stakeholder questions.
- Add richer empty states and data-quality warnings.
- Add print-friendly and presentation-friendly layouts.
- Add keyboard-accessible chart summaries.
- Add configurable thresholds for recommendation rules.

## Portfolio Improvements

- Replace placeholder screenshots with sanitized visuals.
- Add a short GIF walkthrough using synthetic data.
- Add a diagram image export for non-Mermaid environments.
- Add a concise project summary for recruiter scans.
- Add a synthetic public demo only if it can be built without private logic or data.

