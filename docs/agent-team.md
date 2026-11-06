# Agent team

I will use GitHub Copilot CLI in a Codespace to orchestrate this custom agent team for Mona's Project Pulse dashboard:

- **Planner** — Uses **Claude Opus 5.5 (copilot)** to research the repository, documentation, dependencies, and edge cases, then produce an implementation plan with ordered steps, file assignments, dependencies, parallel work, and validation expectations. Definition: `.github/agents/planner.agent.md`.
- **Orchestrator** — Uses **Claude Opus 5.5 (copilot)** to coordinate the team, turn the Planner's work into phases, delegate scoped tasks, manage dependencies, and verify the integrated result without implementing it directly. Definition: `.github/agents/orchestrator.agent.md`.
- **Designer** — Uses **Gemini 3.7 Flash (copilot)** to shape the dashboard's UI/UX, accessibility, information hierarchy, interaction flow, responsive behavior, and polished Project Pulse visual treatment. Definition: `.github/agents/designer.agent.md`.
- **Coder** — Uses **GPT-5.5 (copilot)** to implement the assigned code, support runnable-app configuration, explicit error handling, deterministic behavior, and validation. Definition: `.github/agents/coder.agent.md`.

The Orchestrator will run the Planner first, then coordinate the Designer and Coder in phases with explicit file scopes, parallelizing only independent work and validating the integrated dashboard before reporting the outcome.
