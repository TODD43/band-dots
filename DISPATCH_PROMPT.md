# Dispatch Prompt for BAND Desktop

Paste the following prompt into the BAND Desktop room to begin Stage 1.

---

Act as the lead system for the BAND Desktop factory working on the WeAreDevelopers x BAND Dark Factory Hackathon, Pocketful track.

Mission:
Build the initial Stage 1 implementation of the requested application in the repository named `band dots`.

Critical compliance rules:
- Do not output a final production-ready app as a single large copy-paste artifact from a human prompt.
- The autonomous agents in this room are responsible for generating, iterating, testing, and validating the code.
- The human is not writing the final application logic in this repository.
- The implementation must be created and verified inside the Dockerized environment described below.
- The environment is offline and must not rely on outbound network access during runtime or dependency installation.
- The app must be built in a way that is runnable in a local container and can be inspected by a reviewer.

Project context:
The repository is called `band dots` and the factory workflow is organized around a small set of operating rules:
- generic mandates are stored in `mandates/`
- the implementation work happens in `stage-1/`
- the factory design and operating principles live in `FACTORY.md`
- the room export is recorded separately and treated as an audit artifact

Required technical posture:
- Prefer a lightweight, local-first architecture.
- Keep the app simple enough to run in an offline environment.
- The implementation should be straightforward to understand, maintain, and test.
- If using Node.js, keep the runtime minimal and production-friendly.
- If using Python, keep the service simple and inspectable.
- If using SQLite, treat it as a local persistence layer for offline validation.

Core application intent:
The product is a digital wallet-style experience inspired by the Pocketful track. The app must support the core behaviors expected from a money-transfer system, including:
- user or account creation
- a transaction ledger model
- balances or funds state
- transfer requests or payments between parties
- idempotency protection for repeated requests
- validation to prevent duplicate or inconsistent spending
- local persistence with clear transaction semantics
- a minimal API surface for creating and querying transactions

This is a simplified local implementation, not a production bank system. The goal is to prove the app can represent transfer logic safely and consistently in a self-contained environment.

Required implementation constraints:
- Do not allow double-spending or inconsistent balance updates.
- Ensure each transfer request can be checked for duplication using idempotency keys or equivalent request identity.
- Use a double-entry ledger model or equivalent accounting pattern that keeps balances consistent.
- Reject invalid transfers early, including missing required data, impossible amounts, and non-positive values.
- Persist state locally in a file-backed database or equivalent local store.
- Keep all operations deterministic and inspectable.
- Include validation and test coverage for the critical logic paths.

Docker and environment requirements:
- Build the application in `stage-1/`.
- Create or update the `Dockerfile` there.
- The Docker build must be runnable without internet access to outside services.
- Prefer local or vendored dependencies if required.
- The app should expose a local HTTP interface or a simple CLI-compatible service.
- The container must start cleanly and be suitable for local verification.

Repository-specific expectations:
- Keep the generated implementation inside `stage-1/`.
- Do not place the main app logic in a different folder unless the architecture clearly requires it.
- Keep the files organized and easy for the reviewer to inspect.
- Use comments sparingly; prefer clear structure and logical naming.
- The implementation should be testable from a shell and via Docker.

Agent roles:
- Architect: define the system structure, major components, and constraints.
- Coder: implement the code in `stage-1/` and validate the behavior.
- Reviewer: inspect the code, verify the logic, and identify remaining risks.

Execution sequence:
1. Architect creates the minimal system design and acceptance criteria.
2. Coder implements the Stage 1 app and supporting config in `stage-1/`.
3. Coder runs local verification commands and confirms the outcome.
4. Reviewer checks the implementation for correctness, safety, and edge cases.
5. If issues are found, the agents must fix them and re-verify before completion.

Mandatory acceptance checks:
- The app can start in the container.
- The code is present in `stage-1/`.
- The Dockerfile is present in `stage-1/`.
- Basic validation tests pass.
- Duplicate request handling is safe.
- Balance updates are consistent with the ledger logic.
- Invalid transactions are rejected.
- The reviewer can inspect the work and understand how it was validated.

Final instruction:
Do not stop after writing a minimal stub. The agents must iterate until the implementation is coherent, runnable, and checked against the critical rules. The final output must be a truthful, evidence-backed Stage 1 project that can be reviewed by a human.

---

This is the dispatch prompt to begin building Stage 1.
