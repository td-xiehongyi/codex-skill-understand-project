---
name: understand-project
description: "Evidence-based guided tours of unfamiliar software projects: explain a project's purpose, technology roles, feature flows, file and directory boundaries, and safe starting points for a requested change. Use for project understanding and code-orientation requests; do not use for unrelated implementation, debugging, refactoring, generic technology questions, or documentation generation without project-understanding context."
---

# Understand Project

Help the user build a reliable mental model of the current project from repository evidence. Follow the user's language, preserve exact identifiers and filenames, and keep the default interaction read-only and conversational.

## Mode selection

Choose one mode from the request:

1. **Project overview** — the default when the user asks what the project is, asks for a beginner explanation, or does not name a narrower target.
2. **Full tour** — use when the user asks to understand the whole project, architecture, stack, or how to run it.
3. **Topic trace** — use when the user names a feature, request, module, or runtime path and wants to know how it works end to end.
4. **Change navigation** — use when the user wants to modify or extend something and asks where to start reading. Explain the safe entry points and boundaries; do not implement the change unless separately requested.

Read [references/exploration-workflow.md](references/exploration-workflow.md) for reconnaissance order, project-type heuristics, stopping rules, and evidence recording. Read [references/explanation-guide.md](references/explanation-guide.md) for teaching rules and the output contract for the selected mode.

## Operating boundaries

- Explanation requests are read-only by default. Do not modify source files, install dependencies, start services, or create project documentation unless the user explicitly requests that action.
- Before any write, inspect project instructions, contribution guidance, and same-name files that could be affected. Ask when the requested write would change architecture or scope.
- Use existing read/search/check capabilities when they improve understanding. Do not require Repomix, LSP, MCP, a database, vectors, a knowledge graph, a web UI, or an external model.
- For large repositories, map package, workspace, service, and app boundaries before opening implementation files. Stop when additional files no longer change the mental model; offer focused choices when several subsystems are plausible.
- Never claim that a file was read, a command was run, or a behavior was verified unless it happened in the current task. README and plan statements are documentation claims, not proof of implementation.
- Keep static inspection, automated build/test checks, and real runtime checks visibly separate.

## Response discipline

Start with the observable project goal or user-facing behavior. Explain technologies in this project's context rather than as generic definitions. Include at least one evidence-backed entry point or flow when available, and place absolute clickable file links beside important claims.

Label conclusions as **confirmed**, **documentation claim**, **inference**, or **unknown** when the distinction matters. Avoid file-by-file inventories. For beginners, include what can be ignored for now. End with useful next reading directions or questions; if no mode was specified, offer three focused follow-ups.

Before responding, check that the answer begins with the project goal, contains project-specific technology context, separates evidence levels, states unverified behavior, and gives a practical next step.
