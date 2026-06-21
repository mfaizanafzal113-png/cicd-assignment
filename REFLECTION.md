# Reflection

The lint stage protects against inconsistent formatting and obvious style issues. The test stage protects against actual functional regressions before they reach anyone else. The deploy stage is the step that actually ships the code, so it has to come last.

Order matters because each stage gates the next — if deploy ran before test, a broken commit could go straight to production before anyone noticed. Gating deploy behind test with needs: test means a failed test run physically blocks deploy from running at all.

One thing I'd add to make this closer to production is a staging environment between test and deploy, plus a Python version matrix so "passes on my machine" becomes "passes on every version we support."
