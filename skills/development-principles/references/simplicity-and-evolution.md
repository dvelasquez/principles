# Simplicity and evolution

Open this file when the decision is whether to add a dependency, an abstraction, configuration or structure, or how to defer work.

## Rule of Least Power

- **Statement:** Use the least powerful mechanism that solves the problem, both to build and to verify.
- **Why:** A weaker tool has fewer ways to fail, less security surface and less to maintain. A rule written only in prose is forgotten, especially by an agent with no memory between sessions.
- **Applies when:** always.
- **Sources:** Tim Berners-Lee and Noah Mendelsohn, *The Rule of Least Power*, W3C Technical Architecture Group (2006).

## Use the platform, choose boring technology: the smallest new surface wins

- **Statement:** Do not install a dependency for something the platform or an installed dependency already solves. Prefer one more route inside what exists over a new service, domain, container or dependency.
- **Why:** Every dependency and every new surface is something more to operate, secure and maintain, plus an exit cost. A small team cannot pay for complexity it does not use.
- **Applies when:** always.
- **Sources:** Dan McKinley, *Choose Boring Technology* (2015).

## You Aren't Gonna Need It, with a cheap seam

- **Statement:** Build for the case that exists. A shared abstraction, a seam or a configuration value is born only when the variation is real, concrete and near. If the change and its arrival cannot be named, preparing for it is speculation. A piece that already runs in more than one project has its second case: when it is touched for any reason, its hard-coded values move to configuration, with a default equal to the current value.
- **Why:** Speculative infrastructure costs today and rarely pays. A premature abstraction fixes the wrong shape and hides defects that the first future user pays for. Preparation for a named change pays without discussion, and moving values when a shared piece is touched stops portability debt from growing without a large project.
- **Applies when:** always. The threshold for "real" is an open parameter difference, see `open-conflicts.md`.
- **Sources:** Kent Beck and Ron Jeffries, Extreme Programming; Martin Fowler, *Refactoring* (rule of three); Michael Feathers, seams; Robert C. Martin, the Boy Scout Rule; *The Twelve-Factor App*, configuration.

## Cheap and reversible first, structural later

- **Statement:** First make the cheapest reversible move that measures how much of the problem is structural. Apply the structural change only if the cheap move does not close the gap.
- **Why:** A structural change demands coordination and migration. The cheap move delivers data.
- **Applies when:** a change looks structural.
- **Sources:** Jeff Bezos, two-way doors, letter to shareholders (2015).

## Delete rather than defer

- **Statement:** No pending note in the code, no commented-out block, no workaround without a date. Deferred work goes to the backlog with a verifiable reopening condition.
- **Why:** A "temporary" workaround is code that is maintained forever.
- **Applies when:** always.
- **Sources:** practice.

## Fix the class of defect at the root and remove the patch

- **Statement:** Fix the cause. Once the cause is fixed, delete the guard that only covered the symptom. A flaky test is investigated, not retried.
- **Why:** A patch on the symptom leaves the cause alive, and the cause produces new defects of the same family.
- **Applies when:** always.
- **Sources:** Taiichi Ohno, five whys, Toyota Production System.

## Operating cost is a real constraint

- **Statement:** Money and paid continuous-integration minutes count as a constraint when choosing between options.
- **Why:** In one production agent loop, the only two real reversals in 901 commits were caused by cost.
- **Applies when:** an option has a recurring cost. Conflicts with the smallest-new-surface principle, see `open-conflicts.md`.
- **Sources:** practice.
