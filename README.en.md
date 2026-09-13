# evidence-grounded-academic-writing

[中文](README.md)

A Codex skill for evidence-grounded academic writing in Chinese and English. It supports drafting, translation, polishing, and review while keeping claims verifiable, claim strength accurate, terminology stable, and prose appropriate to the target venue. It does not turn “sounding human” into invented facts, changed findings, or optimisation for an AI-detector score.

## Usage

This skill is manual-only. Invoke it explicitly when needed:

```text
$evidence-grounded-academic-writing
```

Then specify the language, task mode, evidence scope, and target journal or other publication requirements. Other agents can load `SKILL.md` and the applicable reference files manually; their automatic discovery and invocation behaviour has not been verified.

Example:

```text
Use $evidence-grounded-academic-writing to polish the discussion below.
Preserve numerical values, citation markers, and claim strength.
Flag missing evidence and return only the revised prose. Material: …
```

## Four modes

- **Drafting**: use only author-supplied or verified material; do not fill gaps with invented objects, data, results, or references.
- **Translation**: preserve negation, modality, attribution, causal strength, tense, scope, and terminology; flag ambiguity instead of silently resolving it.
- **Polishing**: improve clarity, coherence, and venue-appropriate register while protecting source meaning, evidence boundaries, and citation information.
- **Review**: report problems and recommendations concerning claims, evidence, citations, logic, and style; by default, do not rewrite the source.

All modes apply semantic locks, source-aware citation checks, author-control boundaries, and applicable AI-assistance disclosure requirements. When key support is missing, keep a placeholder such as `[author input needed]` or `[to verify]` rather than presenting an unknown as fact.

## Installation

The recommended installation is to clone the public repository into the Codex skills directory:

```bash
git clone https://github.com/xinanli2001-cell/evidence-grounded-academic-writing \
  ~/.codex/skills/evidence-grounded-academic-writing
```

If the destination already exists, do not overwrite it. Clone to a temporary directory, compare the files, and merge reviewed updates manually; alternatively, keep the existing directory and copy only the files you have reviewed. Before and after installation, check that `SKILL.md`, `references/`, and `agents/openai.yaml` are complete.

## File layout

```text
evidence-grounded-academic-writing/
├── SKILL.md
├── README.md
├── README.en.md
├── agents/
│   └── openai.yaml
└── references/
    ├── chinese-academic-style.md
    └── english-academic-style.md
```

`SKILL.md` defines the core principles, four modes, evidence and semantic boundaries, and delivery rules. Chinese tasks use `references/chinese-academic-style.md`; English tasks use `references/english-academic-style.md`; bilingual tasks use both. `agents/openai.yaml` supplies the Codex display name, default prompt, and manual-invocation policy.

## Style boundaries

The “roughly 30% conversational, 70% academic” guidance in the reference files is a preference about reading impression, not an empirical measure, word quota, or acceptance criterion. The style files are editable. Explicit requirements from a journal, conference, school, or publisher—and the author’s supplied examples and materials—take priority within their applicable scope.

This skill does not claim to identify AI authorship, lower or pass any AI detector, or use detector scores as evidence of quality. Authors must still verify facts, citations, disclosures, authorship, ethics, licensing, and venue requirements before submission.

## Sources and attribution

This package distils the author’s Chinese and English academic-writing preferences, evidence-checking boundaries, and Codex-assisted development practice. It also draws on expression-related ideas from [Humanizer](https://github.com/blader/humanizer). This attribution does not imply official affiliation, co-maintainership, or behavioural-efficacy endorsement. Third-party source and licence details are listed in [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md).

The project is released under the MIT License; the full licence text is in [`LICENSE`](LICENSE). Structural validation does not establish writing quality; users should review the actual revisions.

## Contributing

Small, inspectable improvements are welcome. First describe the problem, affected language, and intended boundary, then submit a focused patch. New rules should have an observable rationale; do not treat a single word, punctuation mark, or sentence form as evidence of authorship, and do not add unverified references, data, institutional relationships, or efficacy claims. When editing style guidance, check the related reference file and preserve the manual-only, evidence-first policy.

Before contributing, confirm that only necessary files changed and that no private paths, private manuscript examples, or unpublished material entered the repository. Release, submission, and licence changes are handled separately by the maintainers.
