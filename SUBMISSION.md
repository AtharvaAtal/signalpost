# Submission

## Run command

From the repository root, after the setup/download steps in `README.md`, the
single command for a 100-company run is:

```bash
uv run python scripts/run_competition_batch.py \
  --organisations smoke-companies.jsonl \
  --bulk brreg-enheter.csv \
  --profiles-output out/smoke-profiles.jsonl \
  --output out/smoke-envelopes.jsonl \
  --report out/smoke-report.json \
  --run-id smoke-001 \
  --expected-count 100
```

## Models, APIs, licences, and cost

- **Models:** None. The submitted run does not use an LLM or another
  statistical model.
- **APIs:** Brønnøysundregistrene open Enhetsregisteret and
  Regnskapsregisteret APIs, plus the Brønnøysund bulk registry snapshot. The
  website module fetches only the company website listed by the registry.
- **Licences and source rights:** Brønnøysundregistrene data is used under its
  published open-data terms (including NLOD 2.0 for the registry snapshot).
  Website content is fetched as a company-reported, public source and is not
  treated as official proof. No restricted social-platform or search-provider
  data is used by the official run.
- **Expected cost per official run:** USD 0 in third-party API cost. This is
  the configured cost for the submitted modules; infrastructure and local
  execution costs are not estimated here.

## Measured 100-company smoke test

The committed report is [`docs/smoke-report.json`](docs/smoke-report.json).
It records 538 requests for 100 companies, or **5.38 requests per company**.
The run took about **89 seconds** (the report timestamps span about 89
seconds). The report emitted 100 envelopes and passed its validation checks.

## Limitations

Website discovery needs a search key. Without one, website coverage is about
**6%**. The official run therefore visits registry-listed websites only and
does not claim broader website coverage.
