# Agents, Workflows, and MCP — Explainer

## Workflow vs. Agent

Anthropic's engineering post draws one specific architectural line, and it's not about how "smart" or autonomous something *feels* — it's about who decides the sequence of steps.

**A workflow is a system where the code decides the path.** An engineer writes the steps in advance — do this, then that, then check this — and the LLM fills in each step, but it doesn't get to change the order or skip a step. My FL-04 automation workflow (Gather → Synthesize → Draft → Review & Format) is exactly this: four fixed prompts, run in a fixed order I wrote in advance, with me pasting the output of one step into the next. The LLM never decided to add a fifth step, skip Synthesize, or go back and re-gather more sources on its own — I decided that structure before running it once, and it doesn't change run to run. In Anthropic's own vocabulary, this is specifically the **prompt chaining** pattern: a task decomposed into a fixed sequence of LLM calls, each one processing the previous one's output.

**An agent is a system where the model decides the path.** Instead of a person hard-coding "step 1, then step 2," the model is given tools and a goal, and it decides — turn by turn — what to check, what to call, when it has enough information, and when it's done. It gets real feedback from its environment (a tool result, a file it just read, an error message) and uses that feedback to decide its *next* move, not just to fill in a pre-written slot. That open-endedness is exactly what my pipeline doesn't have: nothing in FL-04 reads a result and decides to change course.

**Classifying FL-04:** it's a workflow, specifically prompt chaining — not an agent. The clearest tell is that I am the orchestrator. I'm the one deciding when Gather is "done enough" to move to Synthesize, and I'm the one pasting the handoff between steps. A true agent version of this same idea would decide those things itself.

## What MCP Is

MCP (Model Context Protocol) is a standard way for an AI application to connect to things outside the chat window — local files, live services, other tools — without every one of those connections needing custom, one-off code. Anthropic's own framing is the clearest: think of it like a USB-C port. Before USB-C, every device needed its own specific cable; MCP does the same thing for AI applications and outside tools — one shared connector format instead of a different wire for every pairing.

MCP defines three primitives, and each one answers a different question about *who's in control*:

- **Tools** are actions the model can decide to call on its own — think "create a GitHub issue" or "run a search." The model chooses when to use them based on what it's trying to do.
- **Resources** are read-only data the *application* decides to hand to the model — a file's contents, a database schema — without the model having to ask for it first.
- **Prompts** are reusable templates a *person* explicitly triggers, like a saved slash-command for a recurring task.

The pattern across all three: tools are model-controlled, resources are application-controlled, and prompts are user-controlled. That distinction is the same "who's deciding" question from the workflow/agent split, just applied one level down, at the level of a single capability instead of a whole pipeline.

## What FL-04 Would Need to Become an Agent

Right now, every "decision" in my pipeline is actually a decision I already made and hard-coded: which sources to gather, when Synthesize has enough material, when the Draft is good enough to move to Review. To become an agent rather than a workflow, the model itself would need real tools it could decide to call, and the judgment calls I'm currently making by hand would need to move to the model, checked against real feedback instead of my own read-through.

Concretely, one upgrade: give the pipeline an actual **search tool** (rather than me pasting in articles I already found) and let the model decide, on its own, when it has "enough" sources on a topic — searching again if the first pass turns up thin or conflicting coverage, and stopping once it judges the picture is solid. That's the single biggest gap between what I built and a real agent: right now, *I* am the one deciding "is this enough to move to Synthesize?" An agent version would make that call itself, using the actual quality of what it found — not a number of searches I pre-decided — as its stopping signal.
