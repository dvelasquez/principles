# Open conflicts

Open this file when a decision touches two principles that point in different directions. Every entry here is **unresolved**. An agent that hits one of them escalates to the human with the question and both positions. It does not pick a side.

## Conflicts between principles

### Who authorizes changing what a test expects

- **Position A, Never lower the bar of a test:** the expected result changes only if the human accepted the behavior change.
- **Position B, Never lower the bar of a test:** the ticket is the oracle; the agent aligns the assertion with what the ticket orders without asking; weakening the bar needs a human, and in authorization tickets it is forbidden.
- **Status:** unresolved; an agent escalates and does not pick a side.

### Prepare for change only when named, versus convert hard-coded values when touched

- **Position A, You Aren't Gonna Need It, with a cheap seam:** no configuration without a real, named and near second case.
- **Position B, Hard-coded values become configuration when touched:** when a piece is touched, its hard-coded values move to configuration with the current value as default, without a second case. This position is scoped to pieces meant to run in more than one project.
- **Status:** unresolved; an agent escalates and does not pick a side.

### Receipts versus human reading

- **Position A, Receipts by consequence instead of prior permission:** protection comes from reversibility, a visual receipt and later correction; the receipt is triggered by consequence.
- **Position B, Safety does not depend on a human reading:** a process whose safety depends on the operator reading something is already broken; reading concentrates where measured confidence is low.
- **Status:** unresolved; an agent escalates and does not pick a side.

### Operating cost versus smallest surface

- **Position A, Operating cost is a real constraint:** if the managed option costs money, prefer the own option or the one that does not spend paid minutes.
- **Position B, Use the platform, choose boring technology: the smallest new surface wins:** the smallest new surface wins; a self-hosted runner is a surface to operate. In one production agent loop, the self-hosted runner stopped continuous integration three times.
- **Status:** unresolved; an agent escalates and does not pick a side.

## Parameter differences under one principle

### Threshold for sharing logic, under You Aren't Gonna Need It

- **Position A:** a registry or selector only with a second real case.
- **Position B:** logic is not shared until its third real use.
- **Status:** unresolved; an agent escalates and does not pick a side. Both positions agree that a shared abstraction is born with its first consumer.

### Tolerance for scope expansion, under Closed scope

- **Position A:** build exactly what was asked; what adds scope goes to the report.
- **Position B:** a small, mechanical, same-layer expansion proceeds and is noted in the pull request; one that changes a business decision escalates.
- **Status:** unresolved; an agent escalates and does not pick a side.

### What enters the open pull request, under Closed scope

- **Position A:** suggestions that add scope go to the report, not the code.
- **Position B:** follow-up fixes and small adjustments enter the open pull request, in batches.
- **Status:** unresolved; an agent escalates and does not pick a side.
