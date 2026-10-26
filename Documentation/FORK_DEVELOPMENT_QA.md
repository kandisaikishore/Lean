# Fork Development and QA Notes

This repository is a fork of [QuantConnect/Lean](https://github.com/QuantConnect/Lean), an event-driven algorithmic trading engine. Use the upstream README, CONTRIBUTING.md, and official LEAN documentation as the primary source of truth. Keep fork-specific notes separate from upstream instructions.

## Contribution expectations

The upstream contributor guide requires unit tests for pull requests. Bug fixes should include a test that reproduces the defect; new features should cover expected behavior and relevant edge cases. Follow the repository's C# style conventions and existing project structure.

## Before changing the fork

1. Identify the exact upstream base commit and the purpose of the fork-specific change.
2. Keep changes focused and avoid unrelated upstream files.
3. Review upstream CONTRIBUTING.md and existing test conventions.
4. Do not commit broker credentials, API keys, personal market data, or private account information.
5. Describe any behavior that differs from upstream explicitly.

## Testing strategy

Select tests relevant to the changed component. For algorithm, data, brokerage, order, or portfolio behavior, use deterministic fixtures and simulated/paper environments. Never run a new strategy against a live brokerage account as a substitute for automated tests.

- Add unit tests for the behavior being changed.
- Include regression cases for the original failure.
- Run the relevant .NET build/test commands documented by the repository and CI workflows.
- Run broader regression tests when the change affects shared engine behavior.
- Report unavailable tests, external data requirements, and environmental constraints.

## Trading-system safety

A passing unit test does not establish profitability, regulatory compliance, or live-trading safety. Verify order sizing, risk limits, market-hours behavior, data timing, and brokerage integration separately. Do not include real account credentials or sensitive trading logs in issues or test fixtures.

## Pull-request checklist

- [ ] Explain the upstream behavior and the intended fork-specific difference.
- [ ] Add unit/regression tests.
- [ ] Run relevant build/test checks and state the results.
- [ ] Review for accidental secrets and unrelated changes.
- [ ] Avoid claims of live-trading validation unless that validation was explicitly performed.
