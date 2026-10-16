# Boundaries, data and contracts

Open this file when the decision is where a fact is stored, how outside data enters, how a contract changes, or how data is written or migrated.

## Single source of truth, and the boundary follows the data owner

- **Statement:** Each fact is defined in one place and everything else is derived. When another system owns a fact, no parallel copy is kept; at most a cache that declares its origin.
- **Why:** Two descriptions of the same fact end up contradicting each other, and neither says which one is valid. Each copy also invites others to build on something that is not the source.
- **Applies when:** always.
- **Sources:** Andrew Hunt and David Thomas, *The Pragmatic Programmer* (1999); Eric Evans, bounded context.

## Anti-Corruption Layer: contracts speak of capabilities, not providers

- **Statement:** A contract between modules uses domain words. What a provider already operates is not reimplemented; a thin translator with neutral names keeps the provider's vocabulary, identifiers and errors out.
- **Why:** If the provider's vocabulary enters the contract, changing or adding a provider forces a rewrite of the contract.
- **Applies when:** the project consumes data or services from another system.
- **Sources:** Eric Evans, *Domain-Driven Design*, Anti-Corruption Layer.

## Make illegal states unrepresentable, and parse, don't validate, at the boundary

- **Statement:** All data from outside the process becomes a validated type at the boundary. The interior works only with validated data. An absolute invariant is expressed in a form that rejects the wrong write at write time.
- **Why:** Malformed data that crosses the boundary fails far from its cause. What is prevented only by convention ends up happening; what is impossible does not.
- **Applies when:** data enters from outside the process.
- **Sources:** Yaron Minsky, *Effective ML* (2011); Alexis King, *Parse, don't validate* (2019).

## Additive contracts and the Tolerant Reader

- **Statement:** Contracts grow by adding, never by changing meaning. The consumer tolerates unknown values.
- **Why:** A new value from the producer does not break the consumer's screen.
- **Applies when:** the project produces or consumes a contract that another party changes on its own schedule.
- **Sources:** Martin Fowler, *Tolerant Reader*; Jon Postel, robustness principle.

## Hyrum's Law: a published surface is a commitment

- **Statement:** What is published will be used. Remove before launch whatever has no conceptual owner.
- **Why:** Retiring a surface after launch costs far more than not publishing it.
- **Applies when:** the project exposes an interface to third parties. Dormant until then.
- **Sources:** Hyrum Wright, *Hyrum's Law*.

## Configuration lives where its owner changes it

- **Statement:** What varies per deployment lives in the environment, declared in one place. What a person needs to change without releasing a version lives as data, and changing it does not break existing records. Everything else lives in code.
- **Why:** Data is copied between environments, and a secret stored in data travels with the copy. If every adjustment needs a release, the person depends on the technical team for operations.
- **Applies when:** always for environment values; the data part applies when a person needs to adjust a value without a release.
- **Sources:** Adam Wiggins, *The Twelve-Factor App*, factor III.

## State changes go through named transitions, and the condition is checked at write time

- **Statement:** An entity changes state only through named transitions owned by its module. The condition that authorizes a write is checked atomically together with the write. An exceptional case is a new transition, never a flag that skips the flow.
- **Why:** A detour cannot be tested or reasoned about as part of the flow. Between a read and a write, another action may have changed the state.
- **Applies when:** the project owns entities with state, or concurrent writes to the same entity. Dormant until then.
- **Sources:** Finite state machines; time-of-check to time-of-use.

## Data changes are tested against real data and prove their effect

- **Statement:** A migration that transforms data is tested against data in the previous schema. A risky change ships in one atomic step, with a production measurement right before, and every destructive operation proves that it touched rows.
- **Why:** A clean database hides the defects that only appear with existing data. Skipping the audit turns a silent old permission into a silent loss of access.
- **Applies when:** the project owns a database. Dormant until then.
- **Sources:** Scott Ambler and Pramod Sadalage, *Refactoring Databases* (2006).

## Do not overwrite the person's work

- **Statement:** An automatic process does not replace what a person may have corrected. The machine's original proposal is kept next to the human correction.
- **Why:** Losing a human correction destroys work that cannot be recovered. Keeping the original allows undoing and measuring.
- **Applies when:** a person and an automatic process both write the same data. Dormant until then.
- **Sources:** practice.

## The product path before the data patch

- **Statement:** If the administration interface allows the change, the change is made there. A data patch is the last resort.
- **Why:** Two writes competing for the same row leave the result to the order of deployment.
- **Applies when:** the project has an administration interface and its own data. Dormant until then.
- **Sources:** practice.
