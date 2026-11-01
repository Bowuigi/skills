---
name: bow-feature-plan
description: Plan a feature relatively small feature for a project
---

# bow-feature-plan

Plan a relatively small feature (fitting in a single session, though too long to be implemented in one) to implement for a project.

## When to use

This skill should be used when one of the following is true:

- The user invokes it directly (usually the case).
- The user suggests creating a plan for a feature on a TypeScript project.

## Instructions

Go through those steps in order:

## Step 1: Interview

Initiate a grilling session. Load the `grill-me` skill and interview the user as much as needed about the new feature. Make batches of 3-4 questions. Use the `question` tool (or similar) if you have one available.

If any question is better clarified by an experiment, run one in the folder meant for that purpose. On OpenCode, it is `/tmp/opencode/*`; on Pi, it is `/tmp/pi-experiments/*`. If an experiment can't be ran there, do it somewhere on the current project folder but **remember to clean it up ASAP**.

If a feature is marked as "exploratory" (explicitly, by the user), the user only has a rough idea of what they want instead of a full concept. Guide them towards a complete idea. If a feature is exploratory, contradictions may abound so proceed with care.

The goal here is to reach a shared understanding of what the feature _is_ and (if required) _why is it needed_.

Note: You should get project context too, but not _too much_ project context. Don't guess what else the user may answer so much that you go search the GitHub API for open issues (seriously, don't do that unless prompted).

## Step 2: Confirmation

Present everything you understood to the user in a very brief way. The user's attention span is limited and bad agent behaviour (e.g. em dash overuse, "it's not X, it's Y", ignoring the prompt entirely on a non-exploratory feature, "You're absolutely right!" abuse, etc) could result in high efficiency losses due to annoyances, stress or disgust. You think fast, the user doesn't but tends to know better (both are good! Use it at your advantage).

Nested markdown lists work wonders for this.

This step acts as a final barrier before writing the full plan.

At the end, "Confirm to start writing plan." (or similar) should be the prompt to move to the next step.

## Step 3: Plan writing

For this phase, load the `simple-english` and `writing-for-agents` skills.

The plan must have sections "Final goal", "Relevant context", "Methodology", "Plan phases". Each section has a reason to be there:

- **Final goal**: A rough idea of what's being implemented (and why, if provided). It guides the whole process.
- **Relevant context**: A list of resources and facts that could aid understanding for an executor model working on a task. It saves time (and resources) fooling around and implies the user has to interrupt the agents less.
- **Methodology**: This section is pretty much a numbered list of steps for executor agents to follow. The generated plan is meant to be followed in ATDD style, with each phase starting by writing the acceptance tests, then trying to perform the task, then running those tests, and repeating until every criteria is done. After each phase, **the user** carefully reviews every change, modifies anything wrong and then commits. If an agent has been tasked with completing phase N, it must assume previous phases have been completed (write that part), and that it must complete **only one** phase at a time. Following Kent Beck, this technique is known to work both on humans and agents.
- **Plan phases**: What to implement, divided in a set of single-session-doable phases meant to be executed in order. Every phase must have "Phase <n>: <title>" as its heading, for searchability. Each phase contains the following subsections:
  - **Goal of phase <n>**: What the phase is meant to achieve. Be brief and ensure what's written doesn't imply completing next phases, because executor agents may accidentally misunderstand it and implement more phases than necessary (which usually implies discarding the work).
  - **Description of phase <n>**: A technical, declarative-ish description of _what exactly_ is to be implemented,  as a series of short paragraphs. Avoid long code blocks with brittle "replace this file with this code" instructions.
  - **Acceptance criteria of phase <n>**: What counts as the "definition of done". It's a list of brief declarative specifications that actual tests are derived from later. Those are split into two, "agent-tested" and "test-in-code-tested", depending on whether it's more convenient to test it via an agent experiment or a test that goes in the codebase. Agent tests are more flexible but only run once (while implementing), tests in code can be re-run on the feature and help the reviewer _read_ what the agent understands as correct behaviour (specially decisions not written explicitly on the plan). Distinguish both kinds of tests clearly on the criteria, and indicate which criteria must be tested with which method.

The user's prompt for each phase is usually something like "Implement phase <n> of <plan file>" (+ interruptions if something doesn't make sense), so it's your job to fill in the details. Most importantly, inform the executor agents that they can experiment too (and where), just like this skill has done for you.
