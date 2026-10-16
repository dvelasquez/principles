# Interface and usability

Open this file when the decision is about what a person sees on a screen: layout, errors, states, formats or accessibility.

## Nielsen's usability heuristics

- **Statement:** Every screen is judged against the ten heuristics. The person sees a named failure reason, in their language, from a closed set; technical detail goes to the server log.
- **Why:** A shared standard lets a reviewing agent judge without personal preference. A technical message does not tell the person what to do; a named reason does, and the log keeps what is needed to debug.
- **Applies when:** the project has an interface for people.
- **Sources:** Jakob Nielsen, *10 Usability Heuristics* (1994).

## Consistency and hierarchy

- **Statement:** The same thing looks and reads the same everywhere. Each screen pattern lives in a shared component and each format in a single formatter. What matters most for the task comes first.
- **Why:** What is copied diverges, and the person stops recognizing the same state in two places; inconsistency forces the person to reinterpret every screen.
- **Applies when:** the project has an interface for people.
- **Sources:** Jakob Nielsen, heuristic 4; IBM Carbon Design System.

## Accessibility as a requirement

- **Statement:** A state is communicated with color plus shape or symbol plus text. Design starts from mobile, respects contrast and allows keyboard navigation.
- **Why:** Information that depends only on color does not reach part of the users.
- **Applies when:** the project has an interface for people.
- **Sources:** Web Content Accessibility Guidelines 2.1, success criterion 1.4.1.

## What exists is not precedent

- **Statement:** An existing screen or pattern is not presumed correct. Only what was improved and accepted against the standard is a reference.
- **Why:** Copying what exists propagates its defects.
- **Applies when:** the project has existing screens or patterns.
- **Sources:** practice.

## Each datum carries its provenance and freshness

- **Statement:** A displayed datum declares where it comes from and when it is from, datum by datum.
- **Why:** In one production system, data of the same record diverged for months, and a single date made a stale datum pass as fresh.
- **Applies when:** the project shows data that comes from other systems or ages.
- **Sources:** practice.

## Design first for the real user's device

- **Statement:** Each screen is designed first for the device its audience uses most.
- **Why:** A design adapted afterwards to the main device comes out worse than one designed from that device.
- **Applies when:** the project has an interface for people. Which device is a fact to find out, not to assume.
- **Sources:** practice.
