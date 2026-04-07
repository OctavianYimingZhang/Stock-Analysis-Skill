# Changelog

All notable changes to this project will be documented in this file.

## [1.1.0] - 2026-04-07

### Added
- **§9 Technical Structure Assessment** — three-layer technical analysis appendix (Murphy trend + Wyckoff volume-price + Nison candlestick) isolated from the fundamental body
- `references/technical-analysis-framework.md` — detailed methodology reference for the three-layer framework
- `evals/cases/18-technical-structure-gate.yaml` — regression test for §9 isolation and structure
- Data center/power sector router (`PJM`, `ERCOT`, `NERC`, `DOE`) in source-policy.md
- Satellite/space communications sector router (`FCC`, `ITU`, `FAA`) in source-policy.md
- Technical data source policy for §9 in source-policy.md
- `technical_context` defaults with archetype skip rules in angle-library.yaml
- `CHANGELOG.md`, `CODE_OF_CONDUCT.md`
- GitHub Actions CI workflow (`.github/workflows/validate.yml`)

### Changed
- §8 quality gates now confine technical analysis ban to the fundamental body (§1-§7) instead of a blanket ban
- Red flag `technical_analysis` renamed to `technical_analysis_in_fundamental_body` across all 26 report entries
- Expanded `README.md` with repository structure, archetype table, quick start, and badges
- Expanded `CONTRIBUTING.md` with branching strategy, local validation, and YAML style guide
- Expanded `.github/pull_request_template.md` with structured sections
- Updated `evals/README.md` with §9 coverage area

## [1.0.0] - 2026-04-05

### Added
- Initial release with gate-driven fundamental analysis
- 10 archetypes with archetype-specific mandatory sections
- Three mandatory gating tables (commercial evidence, capacity/milestone, regulatory/qualification/legal)
- Semantic claim gates for `moat`, `platform`, `data_flywheel`, `network_effect`
- Four-tier source hierarchy with global market routers and sector routers
- 17 eval cases covering archetype routing, commercial layering, capacity gating, semantic claim downgrades, source routing, and valuation blocking
- Angle library covering 26 companies and industry themes
- Proprietary data handling and terminal-data gap blocking
