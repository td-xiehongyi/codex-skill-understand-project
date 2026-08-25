# Selective exploration workflow

Use this workflow to gather enough evidence for the selected explanation mode. The goal is a useful mental model, not a complete repository inventory.

## Reconnaissance order

1. Confirm the user's goal, experience level, requested mode, and analysis boundary from the conversation.
2. Inspect project instructions and orientation documents, such as `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `README.md`, `CONTRIBUTING.md`, and focused `docs/` files.
3. Inspect manifests, dependencies, workspaces, build and test configuration, and scripts. Prefer the relevant sections over large lockfile bodies.
4. Build a shallow directory map that identifies applications, packages, services, libraries, tests, assets, and documentation.
5. Identify entry points and module boundaries: UI bootstrap, CLI main, server route, library public API, worker, migration runner, or Tauri command boundary.
6. Locate high-signal feature entry points that match the user's topic or the representative product flow.
7. Trace one or two real call paths from an external action through processing and data access to the result.
8. Cross-check tests and documentation against implementation. Record mismatches instead of silently resolving them in favor of documentation.
9. Sort findings into evidence levels: confirmed, documentation claim, inference, and unknown.
10. Render the explanation using the selected mode and the user's language and experience level.

## High-signal rules by project type

- **Frontend/backend:** start at the app bootstrap and route or component entry point, then follow the API/client call, server handler, service/use-case layer, persistence, and response rendering. Treat generated API clients and UI inventories as secondary until the real call path is found.
- **CLI:** start at the executable entry point and argument parser, then follow command dispatch, validation, side effects, output formatting, and exit/error handling.
- **Library:** start at the public exports and examples/tests, then follow one public API into core types, adapters, and observable results. Distinguish public contracts from internal helpers.
- **Data-oriented project:** start at the dataset/schema/config entry point, then follow loading, transformation, training or query logic, evaluation, and output artifacts. Check whether paths and data are local, generated, or assumed.
- **Tauri:** trace UI action → narrow Tauri command → Rust application service → domain policy → repository/provider/filesystem adapter → command result/event → UI state. Keep frontend access to files, databases, and local model providers separate from Rust-owned boundaries when the repository does so.

## Down-rank or ignore by default

Do not spend early attention on `.git`, `node_modules`, `target`, `dist`, `build`, cache directories, binaries, generated code, unrelated vendor directories, or the full body of large lockfiles. Revisit one of these only when it is directly needed to explain a build failure, generated boundary, dependency choice, or runtime artifact.

## Large-repository stopping rules

- Identify workspace, package, service, and application boundaries first.
- Do not recursively read every file or infer a call path from filenames alone.
- Choose a focused subsystem that answers the user's question; if several are equally plausible, present the choices and ask which one to trace.
- Stop when more files no longer change the mental model, when the representative flow is supported, and when remaining gaps can be stated clearly.

## Internal evidence record

For each major conclusion, keep a compact internal record:

```text
claim: what the explanation says
evidence: file path, symbol, test, command output, or observed runtime result
status: confirmed | documentation claim | inference | unknown
scope: which package, mode, or flow this applies to
caveat: missing verification, conflicting evidence, or boundary
```

Do not expose raw records unless they help the user audit an important claim. Use absolute paths in the final response when linking to local files.
