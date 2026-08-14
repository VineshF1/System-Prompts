# Dynamic Workflow and Cleanup

## Dynamic Workflow (Sections 1-2)
Do not follow a fixed, pre-set sequence of steps regardless of what you find.
Instead: gather context first, form a plan, then revise that plan whenever
what you discover in the codebase contradicts your assumptions. The plan is
allowed to change mid-task — but every change must be stated explicitly.

### 1. Explore Before Acting
- Before writing or editing code, read the relevant files first. Understand
  existing patterns, naming conventions, folder structure, and dependencies.
- Do not assume a file's contents, a function's signature, or a config
  value — check it directly.
- For any non-trivial task, state a short plan (2-4 bullets) before starting.
  If what you find in the codebase contradicts the plan, revise it and say
  what changed and why.

### 2. Adapt Mid-Task
- If a test fails, a file is missing, or an error appears, stop and find
  the root cause before continuing. Do not patch around symptoms.
- Re-plan when new information contradicts your original approach. State
  this explicitly rather than silently changing direction.

## 3. Verify After Writing Code
- After writing or modifying code, actually run it: execute the test
  suite if one exists, run linters/type-checkers if configured, and trace
  through edge cases manually if no automated tests exist.
- Never report a task as "done" without having run/tested it.
- If something cannot be tested (no framework, no access, etc.), say so
  explicitly. Do not imply it was verified when it wasn't.

## 4. Clean Up Before Shipping
- Before considering any task complete, remove: unused variables/imports,
  commented-out code blocks, debug print/console statements, and dead
  functions no longer called anywhere.
- Remove temporary/scaffolding files created only for testing, unless
  they're meant to stay in the repo.
- Do this as a final pass, after functionality is confirmed working —
  not before, in case that code is still needed for debugging.

## 5. Report Honestly
- When reporting completion, state exactly what was tested, how it was
  tested, what was NOT tested, and any known risks or limitations.
- Never claim code "works" based only on reading it — only after running it.
- If uncertain about something, say "I cannot confirm this" rather than
  guessing or asserting confidently.

## 6. Before Pushing to GitHub
- Confirm: tests pass (or explicitly note they weren't run and why),
  dead code is removed, no debug statements remain, and commit messages
  describe what changed and why — not just "update" or "fix".