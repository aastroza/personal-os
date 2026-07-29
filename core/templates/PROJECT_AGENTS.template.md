# Project Agent Instructions

## Purpose

{{What this repository owns and when an agent should work here.}}

## Sources of truth

{{List only verified existing sources, ordered by authority.}}

More specific nested `AGENTS.md` files apply to their subtrees and take precedence when instructions conflict.

## Commands

{{Include only commands verified from repository evidence. Omit unknown commands and omit this section if none are verified.}}

## Git workflow

- Preserve unrelated user changes.
- Do not commit directly to the default branch unless explicitly requested.
- Inspect the full status and diff before staging.
- Stage only the intended files and run the smallest relevant validation.
- Push, open or merge a pull request, deploy, and release only when explicitly requested.

## Safety gates

- Never commit secrets, credentials, private keys, or private PersonalOS content.
- {{Repository-specific actions or files that require approval.}}

## Local conventions

{{Naming, style, testing, generated-file, or data-handling rules that are specific to this repository.}}
