# magicsunday/coderabbit

Central [CodeRabbit](https://coderabbit.ai) review configuration for the
`magicsunday` organisation. One file, applied to every repository that does not
carry its own.

## Why this repository exists — and why it is named this

CodeRabbit resolves a repository's settings in this order, highest first:

1. Global overrides (UI)
2. The repository's **own** `.coderabbit.yaml`
3. **This repository's** `.coderabbit.yaml`
4. Repository settings (UI)
5. Organisation settings (UI)
6. CodeRabbit schema defaults

The central file is only read from a repository named exactly **`coderabbit`** —
a `.coderabbit.yaml` in the organisation's `.github` repository governs *that*
repository alone, not the organisation. That mistake is easy to make and silent:
the configuration looks org-wide, reviews keep running, and nothing indicates
they are running on defaults.

**CodeRabbit must be installed on this repository**, or it cannot read the file.

## Consequence for the other repositories

A repository's own `.coderabbit.yaml` **wins** over this one. So a per-repo copy
is not an addition to the central configuration — it replaces it, and then drifts.
Unless a repository genuinely needs different review instructions, it should carry
no `.coderabbit.yaml` at all and inherit from here.

## What the configuration encodes

Beyond the review-mode settings, the `path_instructions` carry the house rules the
linters cannot express — the PHP and JS/TS style conventions, and a set of
correctness patterns that repeatedly reached merged pull requests across these
repositories despite phpstan max, Rector, php-cs-fixer and Biome.

Treat an entry there as evidence-backed: remove one only after checking that the
class it describes is now caught mechanically, and add one only for a defect that
has actually shipped.

## License

MIT — see [LICENSE](LICENSE).
