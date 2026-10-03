# Stage 1 Workspace

This folder is the staging area for the implementation that the BAND Desktop agents will generate.

Expected contents after the work begins:
- application source files
- environment or config files
- test files
- Docker configuration
- validation notes or run scripts

Rules:
- Keep all implementation output in this folder.
- The human should not hand-write the final app logic here.
- The agents are expected to create, test, and verify the implementation before approval.
- The Dockerfile should live here when the runtime configuration is produced.

This folder is intentionally minimal at the start so that the agents can build the project in a clean, controlled environment.
