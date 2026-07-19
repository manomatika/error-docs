# manomatika/error-docs

Public, hosted documentation for every error code in the **ManoMatika**
ecosystem (matika + eyerate + ahimsa + manomatika). Live at:

**https://manomatika.github.io/error-docs**

## This repo is GENERATED — do not edit by hand

Every file in `errors/` (and `.nojekyll`) is produced from the private,
product-authority repo [`manomatika/manomatika`](https://github.com/manomatika/manomatika)
by two scripts there:

1. `scripts/gen_error_docs.py` — generates one localized (en/es) Markdown page
   per error code, plus a per-locale index, from the merged error-code
   registry snapshot (`manifests/<version>-error-registry.yaml`).
2. `scripts/publish_error_docs.py` — transforms that Markdown into the static
   HTML tree checked into this repo, ready for GitHub Pages.

At each ManoMatika release, that pipeline re-runs and republishes this repo's
`errors/` tree from the release's registry snapshot. Any hand-edit made here
will be silently overwritten at the next republish — file changes against
`manomatika/manomatika` instead.

## URL scheme

Every error code has a stable, derived URL (never stored — see
`error/docs_url.py` in `manomatika/manomatika`):

```
https://manomatika.github.io/error-docs/errors/CODE            <- English (default)
https://manomatika.github.io/error-docs/errors/es/CODE         <- Spanish
https://manomatika.github.io/error-docs/errors/                <- English index
https://manomatika.github.io/error-docs/errors/es/              <- Spanish index
```

`CODE` is the canonical, uppercase error code (e.g. `MATIKA-LNCH-001`) as
declared in the origin's own `error-codes.yaml`.

## Why a separate public repo

`manomatika/manomatika` is private (product authority — recipes, audit log,
release tooling); GitHub Pages with public visibility from a private repo
needs a paid plan. This dedicated repo hosts **only** the generated site,
never any source code, so the error-code docs stay freely reachable by anyone
who hits an error, at zero hosting cost.
