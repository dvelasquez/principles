# Architecture and domain

Open this file when the decision is where code lives, what a module exposes, or how a domain concept is modeled.

## Screaming Architecture

- **Statement:** Code is organized by domain capability, not by framework. What changes together lives together. Deleting a peripheral capability breaks no other capability.
- **Why:** A reader learns what the application does from the folder tree. A capability can change or disappear without touching the rest, and a local change stays local instead of becoming global through lateral coupling.
- **Applies when:** always.
- **Sources:** Robert C. Martin, *Screaming Architecture* (2011); Carson Gross, *Locality of Behaviour*.

## Dependency inversion with a single composition root

- **Statement:** Dependencies point inward. The generic does not know the specific. Dependencies between capabilities enter as parameters and are wired in a single place.
- **Why:** Infrastructure that knows the domain can no longer be reused or tested on its own. A single composition root keeps all the wiring visible. Shared code that depends on specific code turns every local change into a global one.
- **Applies when:** the project has more than one capability, or shared code used by several capabilities.
- **Sources:** Robert C. Martin, Dependency Inversion Principle and Acyclic Dependencies Principle; Mark Seemann, *Composition Root*.

## Model the real domain

- **Statement:** Domain concepts are modeled as they are, not as a generic platform for imagined uses.
- **Why:** A generic abstraction fights the concrete fields of the domain and complicates every query.
- **Applies when:** always.
- **Sources:** Eric Evans, *Domain-Driven Design* (2003).

## Ubiquitous Language

- **Statement:** Code, tests, tickets and conversations use the glossary's terms. An avoided synonym is a defect. A concept missing from the glossary is either invented language or a real gap.
- **Why:** One vocabulary keeps two people, or two agents, from meaning different things with the same word.
- **Applies when:** always. When the project has no glossary yet, a missing term is a definition question for the human.
- **Sources:** Eric Evans, *Domain-Driven Design*.

## Deep modules

- **Statement:** A module offers a lot of behavior behind a small interface, and the interface includes invariants, error modes and order of use. If deleting the module makes complexity disappear, the module was only a pass-through.
- **Why:** The caller gets more capability for each thing it learns, and the maintainer concentrates changes and defects in one place.
- **Applies when:** always.
- **Sources:** John Ousterhout, *A Philosophy of Software Design* (2018).

## Humble Object at the entry point

- **Statement:** The code that receives a request only reads, calls and responds. Every decision lives in a named function that is tested in isolation.
- **Why:** A decision hidden in a request handler is hard to test, escapes test coverage, and gets duplicated across routes.
- **Applies when:** the project receives requests, events or commands from outside.
- **Sources:** Gerard Meszaros, *xUnit Test Patterns*; Michael Feathers.

## Discoverability for a maintainer without memory

- **Statement:** Code is linear, explicit and short, written for a reader who remembers nothing. The most discoverable form of an invariant is a schema or a type.
- **Why:** The maintainer is an agent that only reads the repository. For that agent, an implicit rule does not exist. A pattern repeated across files is the least discoverable form.
- **Applies when:** always.
- **Sources:** practice.

## Separation of concerns

- **Statement:** Two different questions do not share a mechanism, even when their answers coincide today.
- **Why:** When two concepts are fused, changing one silently breaks the other. One mechanism for different questions mixes rules that change for different reasons.
- **Applies when:** two questions currently have the same answer, for example "who are you" and "what can you see", or "who may act" and "who must be told".
- **Sources:** Edsger Dijkstra, *On the role of scientific thought* (1974).

## Business logic lives in application code, not in the database

- **Statement:** The database guarantees structure. Business decisions live in code, next to their tests.
- **Why:** Logic inside triggers or views is hard to test and drifts away from the code that does the same thing.
- **Applies when:** the project owns a database. Dormant until then.
- **Sources:** practice.
