# Agent team

For Mona's Project Pulse dashboard, I will use a four-agent custom team defined under `.github/agents/` and orchestrated with GitHub Copilot CLI in a Codespace.

## Custom agent roster

- **Orchestrator**
	- **Target model:** Claude Opus 4.7 (copilot)
	- **Responsibility:** Coordinates the full workflow end-to-end, delegates work to specialist agents, sequences parallel vs. sequential phases, and verifies that the final integrated result is coherent.
	- **Definition path:** `.github/agents/orchestrator.agent.md`

- **Planner**
	- **Target model:** Claude Opus 4.7 (copilot)
	- **Responsibility:** Researches repository and requirements, identifies risks and dependencies, and produces an ordered implementation plan with file ownership and validation expectations.
	- **Definition path:** `.github/agents/planner.agent.md`

- **Coder**
	- **Target model:** GPT-5.5 (copilot)
	- **Responsibility:** Implements application logic and code changes, fixes defects, keeps behavior deterministic and testable, and supports runnable app setup when assigned.
	- **Definition path:** `.github/agents/coder.agent.md`

- **Designer**
	- **Target model:** Gemini 3.1 Pro (copilot)
	- **Responsibility:** Owns UI/UX quality for the dashboard, including visual clarity, accessibility, hierarchy, responsive behavior, and polished Project Pulse presentation.
	- **Definition path:** `.github/agents/designer.agent.md`

## Orchestration note

All coordination is performed in GitHub Copilot CLI running inside a Codespace, with the Orchestrator delegating scoped tasks to Planner, Coder, and Designer while preserving clear ownership and minimizing file conflicts.

## How the team will work together to build Project Pulse

1. The Orchestrator receives the dashboard request and defines the delivery phases.
1. The Planner researches repository constraints and returns an implementation plan with step ordering, file ownership, dependencies, and validation expectations.
1. The Orchestrator converts that plan into executable assignments and delegates non-overlapping work in parallel where safe.
1. The Designer produces the dashboard UX/UI direction and visual treatment for Project Pulse.
1. The Coder implements application logic and any required runnable setup based on the planned scope.
1. The Orchestrator sequences any overlapping file work, integrates results, verifies that the output is coherent, and reports completion.
