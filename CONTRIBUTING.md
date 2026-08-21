# Contributing

Contributions, testing reports and improvement suggestions are welcome.

## Bug reports

Please open a GitHub Issue and provide enough information to reproduce the problem. Useful information includes:

- Title ID / Content ID
- PKG type: base, patch/update, DLC
- Official PKG or Fake PKG
- APP_VER and VERSION
- SYSTEM_VER
- Exact PS4PKGViewer error
- Whether List Contents succeeds or fails
- Relevant `%TEMP%\PS4PKGViewer_ChayahFallback.log` output
- Reproduction steps

Do not attach copyrighted game PKG files to issues.

## Feature requests

Open a GitHub Issue describing:

- What you would like to improve
- Why it would be useful
- Expected behavior
- Any compatibility considerations

## Pull requests

Keep changes focused and document what was changed and how it was tested.

Changes affecting package parsing, PFS crypto behavior, embedded wrapper behavior or firmware formatting should include regression testing against both previously working PKGs and the package that motivated the change.
