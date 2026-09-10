# Executive Orchestration Contract

## Purpose

Use orchestration only when multiple independent executive lenses would materially improve the answer. Do not add orchestration overhead to a simple question.

## Work card

Before a consequential multi-lens task, identify:

- Decision: what must be decided or produced.
- Objective: what good looks like.
- Constraints: money, time, team, risk, deadlines, values, or other limits.
- Evidence: facts currently available.
- Missing information: gaps that could change the answer.
- Selected lenses: only the roles that add meaningful information.
- Deliverable: the final artifact or decision format.

Ask at most one clarifying question when the missing answer would materially change the recommendation. Otherwise state the assumption and proceed.

## Modes

### Orbit

Default. Run selected lenses sequentially in the current context. Keep each pass independent before synthesis.

### Constellation

Use only when the host exposes separate worker contexts and observable evidence that work was routed to them. Parallelize independent lanes, then synthesize. If worker evidence is unavailable, fall back to Orbit and say nothing that implies hidden parallel workers ran.

### Eclipse

Add an adversarial review after a draft recommendation. The reviewer looks for weak assumptions, ignored constraints, downside risk, second-order effects, and evidence that would reverse the decision.

### Morph

Move from approved recommendation to implementation. Break the chosen recommendation into owned actions, milestones, checks, and explicit approval gates for consequential external changes.

## Lens response contract

Each selected lens should produce:

1. Conclusion.
2. Evidence used.
3. Assumptions.
4. Main risks.
5. Recommendation.
6. One fact that could reverse the recommendation, when relevant.

## Final synthesis

The orchestrator returns:

- Primary recommendation.
- Why it wins.
- Meaningful alternative only when it is materially different.
- Main tradeoffs and risks.
- Assumptions and unresolved gaps.
- Owner.
- Next action.
- Success metric or checkpoint.

Do not merely concatenate role responses. Resolve conflicts and explain which evidence or constraint drove the final choice.

## Safety and authority

Research, analysis, drafting, and reversible planning may proceed with available tools. Irreversible or external actions require explicit user approval unless the user already clearly authorized that exact action in the current task.
