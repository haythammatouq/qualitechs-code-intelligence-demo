# Qualitechs Code Intelligence Demo

مشروع وهمي لتجربة مقارنة الكود، كشف التغييرات والمخاطر، وتوليد حالات الاختبار. لا يحتوي على أي بيانات أو مفاتيح حقيقية. حذف الحسابات محاكاة داخل قاموس Python فقط.

Synthetic, standard-library-only Python fixtures for Code Intelligence. No server, network calls, real accounts, or credentials.

## Branches

- `main`: working reference implementation; tests must pass.
- `baseline`: original known-good snapshot.
- `regression-demo`: deliberately removes an authorization guard and changes percentage-discount arithmetic into an incorrect absolute subtraction. Failing tests on this branch are intentional demonstration evidence, not a production release.

## Run locally

```bash
python -m unittest discover -s tests -v
```

## Test Code Intelligence

GitHub monitoring: add this repository URL and choose `regression-demo`. A monitor saves the current commit as its initial baseline; only later commits become new changes. For an immediate historical diff, use GitHub Compare for `baseline...regression-demo`.

Upload comparison: use `examples/before.py` as the old file and `examples/after.py` as the new file. These are intentional versions of the same synthetic component. Compare identical files as well to verify the unchanged outcome.

Expected review: removed authorization should produce a critical review signal and P0 suggested tests; the pricing change should produce financial regression cases. Suggested test cases are not runtime evidence. The unittest output provides actual measured pass/fail results.

## Verified results

- `baseline`:12 tests pass.
- `main`:15 tests pass, including a small receipt-formatting feature.
- `regression-demo`:6 tests intentionally fail and6 pass. Four failures catch incorrect discount arithmetic; two catch missing authorization. No real account is affected.

Public comparison: https://github.com/haythammatouq/qualitechs-code-intelligence-demo/compare/baseline...regression-demo

For upload testing, download `examples/before.py` and `examples/after.py` from `main`. The latter is an intentionally incorrect fixture, not the implementation used by the passing main test suite.
