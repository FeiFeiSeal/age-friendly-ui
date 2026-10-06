# Age-Friendly UI

An Agent Skill for designing, reviewing, and incrementally improving
web applications and administrative interfaces for older adults.

It focuses on clear information, familiar interactions, reduced memory
load, predictable behavior, and recovery from mistakes.

The goal goes beyond accessibility checks: help users understand the
interface, find and activate controls, recognize what happened, and
know what to do next.

## What it can do

- **Screenshot / UI Review** — Review visible hierarchy, readability,
  controls, and cognitive load in screenshots or mockups.
- **UI Specification Review** — Identify unclear interaction rules,
  missing feedback states, and gaps in error recovery.
- **Frontend Code Review** — Review semantics, forms, keyboard access,
  focus, states, and interaction risks, with concrete code suggestions.
- **Age-friendly Redesign Recommendations** — Improve an existing
  interface while preserving familiar navigation and workflows.

## Requirements and recommendations

Findings distinguish between:

- **WCAG Requirement** — A finding tied to a specific WCAG 2.2
  Success Criterion, including its level and applicable conditions.
- **Age-friendly Recommendation** — A usability recommendation
  informed by older users’ needs, rather than a mandatory WCAG threshold.

For example, an approximately 18px body-text size is this skill's heuristic starting
point to validate with target users, not a WCAG requirement or a universal
research finding.

Issues are prioritized as **HIGH**, **MEDIUM**, or **LOW**.
Severity describes review priority; it is separate from WCAG
conformance levels.

## Usage

Install the complete `age-friendly-ui` folder in your agent's skills
directory, keeping its references and examples together.

For Codex, use `$CODEX_HOME/skills/`, or `~/.codex/skills/` when
`CODEX_HOME` is not set.

For other Agent Skills-compatible tools, use their documented skill directory
and keep the entire package together. `agents/openai.yaml` is Codex-specific
UI metadata; the core instructions are in [SKILL.md](SKILL.md).

Example prompt:

> Use $age-friendly-ui to review this admin interface for older adults.
> Preserve the existing navigation and distinguish confirmed issues
> from risks that need further verification.

Each finding includes:

- Issue
- Severity
- Type
- Evidence
- WCAG finding status (for WCAG findings)
- Why it matters
- Recommendation
- Reference

## Design approach

Age-friendly design is not a blanket increase in font size, button
size, border weight, or color saturation.

This skill prioritizes:

Understand → Find → Activate → Recognize the result →
Know the next step → Recover from mistakes

Recommendations consider the task and context, without assuming
that all older adults have the same abilities or experience.

## Sources

- [W3C WAI: Older Users](https://www.w3.org/WAI/older-users/)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [W3C: Making Content Usable for People with Cognitive and Learning Disabilities](https://www.w3.org/TR/coga-usable/)

WCAG Success Criteria provide the normative requirements.
WAI resources and supplemental guidance inform the design recommendations.

## Status and limitations

**v0.1.1 — Review workflow refinements**

The README is in English; skill instructions, references, and examples
are primarily in Traditional Chinese.

The skill includes four review modes and illustrative examples for
screenshots, redesigns, specifications, and frontend code.

Screenshot reviews cannot confirm keyboard behavior, accessible
semantics, actual click targets, or unshown interaction states.
Unverified findings are explicitly identified.

This is not a complete WCAG audit or conformance certification.
The initial release has not yet been validated through usability
testing with older adults.


## Attribution and independence

Age-Friendly UI is an independent project. It is not affiliated with,
sponsored by, or endorsed by W3C or WAI. It is not an official W3C
publication, an authorized translation, or a certification tool.

The skill contains project-authored guidance and summaries informed by
W3C materials. The original documents remain authoritative; third-party
material remains subject to its applicable terms and is not relicensed
by this project.

See [Third-party notices](THIRD_PARTY_NOTICES.md) for sources, copyright
attribution, document status, license boundaries, and bundled W3C license texts.

## License

Original contributions that the project is entitled to license are available
under the [MIT License](LICENSE), copyright (c) 2026 FeiFeiSeal.

W3C and other third-party material is excluded from that MIT grant and remains
subject to its own terms. See [Third-party notices](THIRD_PARTY_NOTICES.md)
for attribution and scope. Preserve the applicable third-party notices and
license texts when redistributing the corresponding material.
