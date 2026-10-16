# Security, access and failure

Open this file when the decision involves who can see or do something, personal data, or what happens when a dependency fails or is slow.

## Fail closed

- **Statement:** Without explicit authorization or a recognizable verdict, the system delivers nothing. It never falls back to stale data, a default value or an inferred permission.
- **Why:** A fallback that grants access when information is missing grants it silently. A visible loss of access can be debugged; silent access on a frozen state cannot.
- **Applies when:** always.
- **Sources:** Jerome Saltzer and Michael Schroeder, fail-safe defaults, *The Protection of Information in Computer Systems* (1975).

## Complete mediation through a single point of trust

- **Statement:** Every access and every write goes through the same engine on the server, whatever the actor. There is no parallel path, no shortcut from the client and no surface that is public by omission.
- **Why:** With a single door, validation and controls live in one place. A second path drifts from the first and reimplements isolation with defects; an actor that skips the control becomes a back door.
- **Applies when:** the project has users, integrations or background processes that read or write.
- **Sources:** Jerome Saltzer and Michael Schroeder (1975).

## Least privilege

- **Statement:** Each credential or surface receives less than its holder could do, and starts read-only. Widening is deliberate.
- **Why:** A read-only surface removes the consequence of abuse entirely, instead of mitigating it.
- **Applies when:** the project issues or uses credentials.
- **Sources:** Jerome Saltzer and Michael Schroeder (1975).

## Authority is data, not code

- **Statement:** Roles and permissions are stored as data. Code asks for a permission, never for a role name.
- **Why:** A role written in code forces a new release to change who can do what.
- **Applies when:** one person can do something another person cannot. Dormant until then.
- **Sources:** Permission-based access control.

## Tenant isolation as an invariant tested against

- **Statement:** Isolation between clients lives in one place that cannot be forgotten, and is tested with cases designed to break it.
- **Why:** In one production system, authorization concentrated 13 of 38 defects, 8 of them high risk, with leaks between clients.
- **Applies when:** the project holds data of more than one client, organization or account.
- **Sources:** practice.

## Defense in depth, without an escape hatch

- **Statement:** A critical control is made of pieces that cover each other's gaps. There is no special bypass.
- **Why:** A local check does not cover what comes from outside the machine, and an exception flag becomes routine under pressure.
- **Applies when:** a control is critical.
- **Sources:** practice.

## Security asymmetry: what restricts resolves itself, what widens is asked

- **Statement:** When two sources diverge, the divergence that restricts access is resolved automatically. The one that widens access is escalated.
- **Why:** Nobody can tell an intentional manual permission from a regression.
- **Applies when:** a change widens or restricts who can see or do something.
- **Sources:** practice.

## Privacy by design

- **Statement:** Personal data is removed before anything is logged. Realism tests use anonymized copies. Real credentials are never stored for automation.
- **Why:** A log or a copy with personal data is a leak waiting to happen.
- **Applies when:** the project handles personal data.
- **Sources:** Ann Cavoukian, *Privacy by Design* (2009).

## Graceful degradation

- **Statement:** What is auxiliary never blocks the main task. Parallel operations handle each failure separately. Without configuration for an optional service, the feature is not offered and the application keeps running.
- **Why:** The person's work is not lost because a supporting service is down, and a secondary dependency does not take the screen down.
- **Applies when:** the project depends on auxiliary services.
- **Sources:** practice.

## Fail loudly, never hang

- **Statement:** Every external call has a time limit, and running out produces a named error. No error is swallowed. A check that is green when its work failed is worse than no check.
- **Why:** A hang leaves no trace and can only be waited on. A named error can be retried or escalated.
- **Applies when:** the project calls anything outside its process.
- **Sources:** Jim Shore, *Fail Fast*, IEEE Software (2004).

## Wait for a condition, never for a time

- **Statement:** A race is resolved by waiting for an observable condition with a declared limit. A fixed pause does not resolve a race.
- **Why:** A fixed pause fails intermittently and hides the cause. In one production agent loop's retrospective, the fixed wait was the fix that recurred.
- **Applies when:** two things happen concurrently.
- **Sources:** practice.
