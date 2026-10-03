# Factory Operations Manual

## 1. Purpose
This repository is the operational shell for a BAND Desktop multi-agent factory. The human's job is to set up seats, load the mandates, and give the agents a precise mission. The agents are expected to produce the actual implementation work in `stage-1/` and validate it before sign-off.

## 2. Repository structure

band-dots/
├── README.md
├── FACTORY.md
├── DISPATCH_PROMPT.md
├── band-room-export-placeholder.md
├── .gitignore
├── mandates/
│   ├── architect.md
│   ├── coder.md
│   └── reviewer.md
├── stage-1/
│   ├── README.md
│   ├── Dockerfile
│   └── .gitkeep
└── ...

## 3. Seat setup

Use three BAND seats with these roles:
- Architect
- Coder
- Reviewer

Seat rules:
- Each seat receives only its mandate file from `mandates/`.
- The seats are not allowed to invent extra responsibilities.
- The Architect owns system shape and constraints.
- The Coder owns implementation and local verification.
- The Reviewer owns validation, adversarial review, and sign-off.

## 4. Design rationale

The factory is intentionally simple:
- One repo with a strict staging area.
- One generic set of mandates for reproducible work.
- One fenced area for implementation (`stage-1/`).
- One prompt file for the work release.

This keeps the operating model low-noise and makes it easier to recover when an agent writes poor or incomplete work.

## 5. Measured costs

Record the following after each major milestone:
- token usage or model usage
- time spent per agent
- number of iterations before acceptance
- number of failed build or test cycles
- code review findings and reopened issues

Suggested practice:
- Minute-level estimates for each seat
- Simple totals at the end of each work block
- A final summary of cost and quality before stage sign-off

## 6. Bad work detection and recovery

The factory is designed to catch weak output early.

Signals of bad work:
- Implementation ignores architecture constraints
- Code builds but does not satisfy the intended behavior
- Tests are missing or non-diagnostic
- The agent claims success without validation evidence
- The output drifts into scope creep or unnecessary complexity

Recovery rules:
1. Stop the current run.
2. Ask the Architect to restate the constraints.
3. Return the task to the Coder with a short, concrete correction brief.
4. Have the Reviewer inspect the result against the acceptance criteria.
5. Only proceed when the output is validated and explainable.

## 7. Working practice for this repo

- Keep the human-generated instructions in the repo root.
- Keep the generically safe mandates in `mandates/`.
- Keep all implementation artifacts in `stage-1/`.
- Do not mix architecture documents, code, and room exports in the same folder.
- Treat the room export as a record of the actual session, not a source of truth for the application code.

## 8. Exit criteria for Stage 1

Stage 1 is considered complete only if:
- the code is in `stage-1/`
- the Docker setup exists there
- the implementation is validated locally
- the reviewer has recorded findings and final sign-off
- any open issues are visible and not hidden
