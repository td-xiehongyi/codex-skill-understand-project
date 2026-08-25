# Teaching and output guide

## Teaching rules

- Begin with observable behavior or the problem the project solves.
- Explain each technology through its role in this project: what boundary it owns, what data it receives, and what result it produces.
- Use the narrative `user action → entry point → processing → data → result` for at least one representative flow whenever the repository exposes one.
- Avoid a file-by-file inventory. Group files by responsibility and show only the files that support the explanation.
- For beginners, include a short “can ignore for now” section when build internals, generated code, or secondary features would distract from the main flow.
- Preserve exact filenames, symbols, command names, route names, and identifiers.
- Put absolute clickable file links next to important claims, for example `[main.rs](C:\\project\\src-tauri\\src\\main.rs:12)`.
- Separate static inspection, automated build/test checks, and real runtime checks. Do not turn a green static or browser check into a desktop or production claim.

## Project overview output

Include:

1. One-sentence purpose.
2. The problem and intended users.
3. Confirmed capabilities, with evidence levels where useful.
4. A grouped project map.
5. Technology roles in this project.
6. One representative flow.
7. A practical reading order.
8. Limits, inferences, and unknowns.
9. Three next directions.

If the request did not specify a mode, use this shape and offer focused follow-ups for a full tour, a topic trace, or change navigation.

## Full tour output

Add module relationships, entry points, data and state flow, build/test/run information, and a learning order. State which checks were actually run and which runtime behavior remains unverified. Keep the tour bounded by the repository's major application or package boundaries.

## Topic trace output

State the scope, external entry point, key processing steps, cross-module handoffs, side effects and results, and unverified links. Use one concrete call path rather than describing every related file. If the topic is ambiguous, name the plausible boundaries and ask the user to choose before reading broadly.

## Change navigation output

Identify:

- the first file or symbol to read;
- adjacent layers and the direction of the call/data flow;
- current behavior tests and checks;
- safety, API, or ownership boundaries not to bypass;
- remaining unknowns and the smallest useful next investigation.

This mode is orientation only. It must not implement the requested change. If the user later explicitly asks for implementation, treat that as a separate request with its own scope and authorization.

## Final quality check

Before sending any mode's response, verify that:

- the opening describes the observable project goal;
- technology is explained in project context;
- an evidence-backed entry point or flow is included when available;
- facts, documentation claims, inferences, and unknowns are separated;
- the answer is not a file-by-file inventory;
- unverified behavior is explicitly stated;
- the user receives a useful next reading direction or question.
