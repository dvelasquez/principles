# Testing and verification

Open this file when the decision is what to test, how to test it, what to do with a failing test, or how to debug.

## Test behavior through the public interface; mock only at the system's boundaries

- **Statement:** Tests depend on stable contracts, not on volatile details. Only external services, time and randomness are mocked. Expected values come from an independent source.
- **Why:** A test tied to the implementation or the presentation breaks when refactoring although the behavior is the same. A tautological test passes by construction and can never contradict the code.
- **Applies when:** always.
- **Sources:** Kent Beck, *Test-Driven Development*; Steve Freeman and Nat Pryce, *Growing Object-Oriented Software, Guided by Tests*.

## Determinism in the gate, realism outside it

- **Statement:** Tests that block a change are deterministic. Realism is a periodic signal that never blocks, and what it finds becomes a permanent test.
- **Why:** Clean test data hides real defects, but a non-deterministic gate becomes slow and flaky. In one production system, provider mocks hid that remote commands never worked.
- **Applies when:** the project has tests that could run against real or non-deterministic sources.
- **Sources:** practice.

## Never lower the bar of a test

- **Statement:** When a test fails, fix the code or the test setup. What the test demands is not weakened.
- **Why:** A test edited to match the code stops protecting, and "green" then hides a regression.
- **Applies when:** a test fails. Who may change an expected value is an open conflict, see `open-conflicts.md`.
- **Sources:** practice.

## A test must be able to fail

- **Statement:** Every test covers at least one failure case. An assertion that passes with any implementation is a tautology.
- **Why:** A test that was never red does not prove it measures anything. An audit of one production agent loop found assertions that always passed and mocks that made negative assertions pass vacuously.
- **Applies when:** always.
- **Sources:** Richard DeMillo and Richard Lipton, mutation testing (1978); Kent Beck, *Test-Driven Development by Example*.

## Hermetic, self-sufficient tests

- **Statement:** Each test creates its data in its own space and cleans it up. It never depends on shared mutable state.
- **Why:** Tests that share state fail depending on run order and cannot run in parallel.
- **Applies when:** tests touch persistent or shared state.
- **Sources:** practice.

## Pin the behavior before changing a mechanism that works

- **Statement:** Before a structural change, name the test that pins the observable behavior. That test is not edited during the change.
- **Why:** A test that stays green and unmodified is the proof that the change preserved behavior.
- **Applies when:** a structural change touches working code.
- **Sources:** Michael Feathers, *Working Effectively with Legacy Code*, characterization tests.

## First a feedback loop, then the hypothesis

- **Statement:** For a hard defect, first build a fast, deterministic signal that turns red with that exact defect; then form falsifiable hypotheses. Without a signal, stop and ask for evidence.
- **Why:** Jumping straight to a hypothesis leads to fixing the wrong defect.
- **Applies when:** a defect is not reproduced yet.
- **Sources:** Karl Popper, falsifiability.

## Shift left: the cheapest feedback loop first

- **Statement:** What can be verified locally is verified before pushing. Continuous integration confirms; it does not debug.
- **Why:** Iterating against continuous integration spent time and minutes on failures that local checks could find.
- **Applies when:** always.
- **Sources:** practice.

## The release gate tests the interaction and admits no partial pass

- **Statement:** Release verification targets what the release adds over its tickets: the interaction between them. A single red row blocks.
- **Why:** Each ticket was validated in an environment where the other tickets were absent.
- **Applies when:** several tickets ship together in one release. Dormant until then.
- **Sources:** practice.
