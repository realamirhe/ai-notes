# Agent Swarm

## Summary

Agent Swarm is an orchestration approach for work that benefits from multiple focused agents operating under one accountable orchestrator. The orchestrator owns decomposition, dispatch, dependency management, synthesis, verification, and the final answer. Subagents handle bounded pieces of work; they do not replace the orchestrator's judgment or responsibility.

The purpose is not to maximize agent count. A swarm should reduce elapsed time, improve coverage, or add valuable independent scrutiny without creating more coordination cost than value.

## Why this should become a skill

Multi-agent execution is useful only when an agent makes several related decisions consistently: whether parallelism is worthwhile, how work should be divided, which tasks may run concurrently, what context each agent needs, and how outputs should be checked and integrated. Encoding these decisions in a reusable skill provides several benefits:

- **Lower elapsed time:** independent research, implementation, and verification can run concurrently.
- **Sharper focus:** each agent receives a narrow objective and only the context required for it.
- **Better coverage:** separable questions can be explored without forcing one long serial context.
- **Higher confidence:** risky conclusions and cross-cutting changes can receive focused independent review.
- **Clear accountability:** one orchestrator resolves conflicts, evaluates evidence, integrates changes, and communicates the result.
- **Controlled context:** compact briefs and summaries prevent every agent from carrying the entire conversation.
- **Repeatability:** a shared standard makes decomposition, dispatch, verification, and synthesis predictable across tasks.

These benefits appear only when tasks are genuinely separable. Parallelizing tightly coupled work can create duplicated effort, conflicting edits, premature assumptions, and slower integration.

## Recommended activation boundary

The skill should activate when the user explicitly asks for a swarm, subagents, delegation, or parallel agent work. It should not activate for ordinary single-agent tasks merely because multiple tools or steps are involved.

Even after explicit activation, the orchestrator should keep a small or tightly coupled task in the current agent when coordination would cost more than it saves.

## Core behavior

Act as the orchestrator. Own decomposition, dispatch, dependency management, synthesis, verification, and the final answer. Do not merely forward agent outputs.

Preserve these invariants:

- Use the fewest agents that materially reduce elapsed time or improve confidence.
- Dispatch only ready, non-overlapping tasks.
- Respect task dependencies and shared-workspace file ownership.
- Keep scope, authority, permission, and destructive-action decisions with the orchestrator.
- Verify agent claims and integrated changes against primary evidence.
- Stop redundant work and collapse back to one agent when parallelism no longer helps.
- Deliver one final answer containing the outcome, verification, material caveats, and unresolved blockers.

## Choose the operating shape

### One goal with several subtasks

Split the goal into independently verifiable deliverables. Arrange dependent tasks in waves and run only ready, non-overlapping subtasks in parallel.

### Several independent questions

Assign one focused question to each agent and run them concurrently. Synthesize agreements, disagreements, supporting evidence, and uncertainty.

### One small or tightly coupled task

Keep it in the current agent. Do not create a swarm when coordination costs more than the work.

Never manufacture work merely to fill concurrency slots. Parallel agents must not edit the same files or depend on results that do not exist yet.

## Plan the swarm

Before dispatching:

1. Restate the desired outcome and constraints internally.
2. Create the smallest useful task graph: task, owner, dependencies, expected output, and verification.
3. Keep the critical path with the orchestrator when that speeds integration.
4. Delegate self-contained exploration, implementation, testing, or review.
5. Identify shared facts once and pass only the relevant subset to each agent.

Do not ask the user to approve the decomposition unless a missing choice materially changes the result or new authority is required.

## Select model and effort

Choose from models actually available in the environment. Do not assume a model name exists.

- **Fast or inexpensive model, low effort:** factual lookup, inventory, mechanical edits, narrowly specified tests, or formatting.
- **Balanced model, medium effort:** normal implementation, bounded debugging, comparison, or source evaluation.
- **Strongest suitable model, high effort:** ambiguous architecture, cross-cutting diagnosis, security-sensitive reasoning, difficult synthesis, or adjudication of conflicting findings.
- Use **xhigh or above** only when failure is costly and lower effort is unlikely to succeed.

Start at the lowest tier likely to finish correctly in one pass. Escalate a failed or uncertain task instead of assigning every task to the strongest model. Prefer one capable agent over several weaker agents for tightly coupled reasoning.

## Dispatch compact briefs

Give each agent a self-contained brief containing only:

- its concrete objective and boundaries;
- necessary context, files, sources, and prior decisions;
- allowed side effects and explicit prohibitions;
- expected deliverable and verification evidence;
- a request to report blockers and uncertainty plainly.

Use minimal history when the tooling permits it. Point to files instead of pasting large content. Ask agents to return concise findings and avoid repeating the prompt.

For repository edits, assign non-overlapping ownership. Agents share the workspace, so require them to preserve unrelated changes and avoid commits unless the user explicitly requested a commit through the repository's commit workflow.

## Run and steer

Dispatch all ready independent tasks together, up to the available concurrency. While they run, the orchestrator should perform useful integration work such as inspecting shared boundaries or preparing verification.

- Send added context to an active agent instead of spawning a duplicate.
- Reuse an idle agent for a closely related follow-up when useful.
- Stop redundant work once another result resolves it.
- Retry failures only after understanding their cause; narrow the task, add missing context, or escalate model or effort.
- For long jobs, wait efficiently and give the user brief progress updates without narrating unchanged polls.

Subagents must not expand scope or authorize external or destructive actions. The orchestrator remains responsible for permissions and safety.

## Integrate and verify

When results arrive:

1. Check every result against its objective and evidence.
2. Resolve contradictions using primary evidence, direct verification, or a focused adjudication agent.
3. Integrate changes carefully and inspect the combined diff for collisions or duplicated work.
4. Run proportionate end-to-end or targeted verification. Parallelize local checks only when they are independent.
5. Deliver one coherent answer with the outcome, verification, material caveats, and unresolved blockers.

Do not expose raw agent chatter, internal routing, or token accounting unless the user asks. Mention delegation only when it helps explain coverage, confidence, or an unresolved disagreement.

## Efficiency guardrails

- Optimize total turns and rework, not model price alone.
- Avoid duplicate research unless independent confirmation is valuable.
- Avoid reviewer agents for trivial, easily verified work.
- Use a focused reviewer for risky or cross-cutting changes, not automatically for every subtask.
- Preserve discoveries needed by later waves in a compact shared note; do not accumulate full transcripts.
- If only one useful task remains, collapse back to single-agent execution.

## Skill design recommendations

When converting this document into a skill:

- Use a short, discriminating description that mentions explicit swarm, subagent, delegation, or parallel-work requests.
- Keep the entrypoint concise and place this detailed operating standard in a supporting reference if needed.
- Do not make implicit invocation the default unless the project's capability policy permits it.
- Preserve the user's scope and authorization boundaries. Activating the skill must not authorize external writes, destructive actions, new services, or broader work.
- Do not require a fixed number of agents or a fixed decomposition template.
- Avoid scripts or assets unless repeated, deterministic orchestration mechanics demonstrate a real need for them.
- Validate the finished skill's metadata, naming, invocation policy, references, and unfinished placeholders.

## Success criteria

A successful Agent Swarm skill produces a result that is faster or more trustworthy than a sensible single-agent approach while preserving scope and permissions. Work has clear ownership, no conflicting concurrent edits, evidence for important claims, proportionate verification, and one integrated final answer.
