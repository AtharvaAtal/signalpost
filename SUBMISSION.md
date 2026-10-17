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

The strict rerun report is `out/smoke-report-strict-002.json`. It records 538
requests for 100 companies, or **5.38 requests per company**. The measured
elapsed time was **99.72 seconds**. The report emitted 100 envelopes and
passed its validation checks. Website terminal states were **93
not_applicable, 4 ambiguous, 2 complete, and 1 blocked_policy**. The two
published website URLs were `http://www.aelektronikk.no/` for organisation
888567232 and `https://www.aiota.no/` for organisation 933787141.

## Limitations

Website discovery needs a search key. Without one, website coverage is low:
the strict 100-company rerun published **2 of 100** website results. The
strict identity rule rejects redirects to another registrable domain without
the target organisation number, parked or expired pages, different-company
pages, and facts without a page evidence snippet. The official run therefore
visits registry-listed websites only and does not claim broader website
coverage.
