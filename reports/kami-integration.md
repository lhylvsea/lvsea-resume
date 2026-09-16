# Kami 整合报告

## Result

- Target: `lhylvsea/lvsea-resume`
- Source: `tw93/kami`
- Source revision reviewed: `0847a06355b4fd62438c9fac38652dbbffeec7c4`
- Integration mode: semantic adoption, not repository mirroring
- Target contract preserved: one A4 page, 12 allowlisted templates, `raw.data.yaml` → `resume.data.yaml`, official-template copy, PDF/screenshot QA

## Source Boundary

| Field | Record |
|---|---|
| Source type | Public GitHub Agent Skill repository |
| Read | README, root Kami SKILL, resume writing, general writing, design, production, anti-patterns, resume schema, license |
| Not read for adoption | Landing-page, slides, diagram, math, MCP implementation paths and full asset/template inventory |
| High-signal sections | Source and truth pass; Role / Actions / Impact; ownership calibration; missing-data rule; fresh review |
| Observed | Kami's resume contract is two A4 pages and uses a separate document builder |
| Inferred | Its content/evidence methods can strengthen the existing YAML-first one-page workflow |
| User-provided | The target repo and the request to integrate Kami through `$lvsea-zao-skill` |
| Unavailable | Real candidate provider run, recruiter blind review, user outcome telemetry |
| Target runtime | Agent Skills-compatible `SKILL.md` plus the target repo's existing scripts/templates |
| Assumptions | No Kami code, asset, font, dependency, network update check, or two-page template is required for this integration |

## Mechanism Cards

### Claim-level truth pass

- Source evidence: Kami `resume-writing.md` source and truth section.
- Trigger: More than one source or a source with conflicting scope/metrics.
- Decision rule: Extract every visible claim; ask on conflict; do not choose the impressive version.
- Procedure: Mark source status, preserve units and dates, and keep unresolved claims in `ask` / `do-not-claim`.
- Output: Private claim ledger and a resume YAML that contains only supported claims.
- Quality signal: Role, scope, unit, date, and result can be traced to a source or user confirmation.
- Failure mode: A polished line silently merges incompatible sources.

### Role / Actions / Impact

- Source evidence: Kami resume writing contract.
- Trigger: A project or work item is being rewritten.
- Decision rule: Separate position, concrete action, and observable outcome.
- Procedure: Map to `projects[].role` + `projects[].bullets` or `experience[].items[].title` + `body`.
- Output: Compact STAR-like copy that fits an existing one-page template.
- Quality signal: Impact is not a restated process, and rows do not duplicate evidence.
- Failure mode: Generic responsibility language fills a project slot.

### Ownership calibration

- Source evidence: Kami ownership and title guidance.
- Trigger: A resume uses owner-level verbs or role labels.
- Decision rule: Use the lowest truthful ownership level that still describes the contribution.
- Procedure: Confirm direction, module boundary, coordination, or implementation scope before choosing the verb.
- Output: Credible role wording without blanket `主导` claims.
- Quality signal: The candidate can defend the stated scope in an interview.
- Failure mode: Team or platform results are presented as individual ownership.

## Verification Record

### Baseline before integration

- `node scripts/check-template-id.mjs --html examples/demo/resume.html --template basic-a4`: PASS.
- `python -m json.tool schema/resume.schema.json`: PASS.
- The default Windows Chrome path was present but was not in the QA script's discovery list; the first export therefore reported Chrome/Chromium unavailable.
- With the explicit Chrome path, the next run exposed a second pre-existing portability issue: subprocess output was decoded with the wrong Windows code page and the QA process crashed before checking the PDF.

### Post-change gates

- `git diff --check`: PASS.
- `schema/resume.schema.json` parse and Python script compilation: PASS.
- Official template fingerprint check on the demo and a copied `basic-a4` workspace: PASS.
- `scripts/export_and_qa.py` now discovers standard Windows Chrome paths and decodes UTF-8/code-page subprocess output safely; the demo export completed with PDF export, one A4 page, screenshot, semantic layout, forbidden-term, and bottom-whitespace checks passing.
- `pdffonts` and `pdftotext` were not installed, so font-family and text-extraction checks remain warnings rather than evidence.
- Added source boundary, adoption ledger, forward retest cases, and third-party notice were read back from the target worktree.

## Missing Evidence

The integration has static source and package evidence only. It does not prove provider-backed copy quality, recruiter preference, two-page Kami rendering, or improved hiring outcomes.
