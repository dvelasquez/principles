# principles

A set of development principles, packaged as an Agent Skill. Agents load them when a ticket, the code and the project's rules leave a decision unanswered. If the principles give an obvious answer, the agent proceeds; if not, it escalates.

The 72 principles were extracted from real projects, then consolidated and checked for sources. Each principle cites its reference in the literature, or "practice" when it comes from repeated practice in those projects.

## Install

```bash
pnpm dlx skills@1.7.2 add dvelasquez/principles
```

## What stays in each project

This repository holds only principles: statement, why, when it applies, and sources. Each project keeps its own:

- **State**: which principles are active or dormant for that project.
- **Rules**: script-checkable consequences of the principles, enforced by the project's own checks.
- **Examples**: the concrete questions and answers for that project's domain.

## How a principle enters

A candidate becomes a principle only if it:

1. Needs judgment to apply. If a script can decide compliance on any code, it is a rule and belongs in a project.
2. Is general: no tools, libraries, files or thresholds.
3. Has a verifiable source: repeated practice in a real project, or a reference in the literature.
4. Produces at least one script-checkable rule.
5. Decides at least one real question that a ticket leaves unanswered.

Unresolved contradictions between principles live in `skills/development-principles/references/open-conflicts.md` until a human decides them.

## License

[MIT](LICENSE)
