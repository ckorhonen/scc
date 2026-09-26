# scc repository guide

This is the Go source-code counter CLI. `main.go`, `cmd/`, and `processor/` contain command execution and counting/language logic; `languages.json` and language fixtures define classification behavior. Preserve generated-data relationships and use the existing fixtures for language changes. `vendor/` and example corpora are not places for unrelated cleanup.

Use Go 1.25.2 as declared in `go.mod`. Build with `go build ./...`; run focused `go test` packages and the existing `go test ./...`/race checks when appropriate to concurrency or counting changes. Format changed Go files with `gofmt`. There is no separate typecheck command (compilation covers Go typing) or general lint script to infer from CodeQL. Inspect benchmark and test-all helpers before running them because they may expand the corpus/work substantially.

For a counting bug, add or use a small synthetic file demonstrating the expected language, lines, comments, and complexity behavior, then check CLI output. A build alone does not establish counting accuracy or performance. Avoid scanning private home directories or downloading large repositories for a focused test, and report benchmark inputs/toolchain with any performance claim.

## Completing work

Carry the authorized change through the relevant checks and repair failures it causes. Make routine, reversible implementation choices using existing patterns; ask only when missing information, a material product decision, or an authorization boundary prevents the next step. Existing authorization remains valid within its scope. If blocked, name the exact action and missing prerequisite, retain concise evidence, and continue independent work.

Choose verification proportional to the change. For instructions or prose, inspect changed paths, links, and local instruction precedence and run `git diff --check -- <changed-paths>`; don't install dependencies or run the application solely for a prose edit. For behavior changes, exercise the affected behavior and applicable checks below, then broaden only for failures or unresolved risk. Report files changed, checks actually run and their results, commands only inspected, and remaining limitations. A build or source inspection alone does not prove runtime behavior. Continue through already-authorized follow-through; stop at explicit review checkpoints or boundaries requiring new authorization.
