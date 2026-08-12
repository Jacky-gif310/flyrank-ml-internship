# Agent Design Specification  
## Weekly AI/SEO Research Scout

**Author: Jackline Mutheu**

---

# 1. Agent Job To Be Done

The Weekly AI/SEO Research Scout is a personal research agent that produces my weekly AI and SEO industry brief.

This agent is an evolution of my FL-04 automation workflow. The previous workflow followed a fixed sequence where I manually decided each step: gather sources, summarize information, draft content, review, and rewrite.

The agent upgrade adds decision-making ability. Instead of me deciding exactly how many sources to collect, the agent determines when it has enough evidence by evaluating source coverage, agreement, disagreement, and information quality.

The goal is to help me create evidence-based research briefs faster while keeping human judgment involved.

**User:** Me, Jackline Mutheu.

**Frequency:** Once per week.

**Time required:** Approximately 10–15 minutes for review and approval.

---

# 2. Workflow vs Agent Difference

My FL-04 pipeline is a workflow because the steps are predetermined:

1. Gather information.
2. Summarize sources.
3. Draft the brief.
4. Review the draft.
5. Rewrite the final version.

Each step happens because I designed the sequence.

The Weekly AI/SEO Research Scout becomes an agent because it can make decisions during the process.

For example:
- It decides when it has collected enough sources.
- It evaluates whether sources agree or conflict.
- It determines when information is too weak to report confidently.
- It chooses when to stop researching based on evidence quality.

The human remains responsible for final approval.

---

# 3. Tools and Data Needed

| Tool/Data | Purpose | Access Plan |
|---|---|---|
| Web search capability | Find current AI and SEO industry sources | Use available Claude search capabilities where available |
| Claude Project instructions | Maintain my writing style and research standards | Existing project containing my Voice Card and identity guidelines |
| Research notes and previous briefs | Maintain consistency across reports | Upload manually when needed |

## Deliberately excluded:

- Email access
- Calendar access
- Automatic publishing tools

The agent only creates drafts. It does not send, publish, or communicate externally.

---

# 4. Agent Instructions

You are my Weekly AI/SEO Research Scout.

Your responsibility is to research current AI and SEO topics and create a trustworthy weekly industry brief.

Follow these rules:

1. Search for reliable sources related to the selected topic.

2. Continue gathering information until:
- major viewpoints are covered,
- repeated information appears,
- conflicts between sources are understood,
- or the maximum search limit is reached.

3. Clearly separate:
- confirmed information,
- uncertain claims,
- disagreements between sources.

4. Never invent:
- sources,
- statistics,
- quotes,
- research findings.

5. Write using my communication style:
- practical,
- clear,
- evidence-based,
- honest about uncertainty.

6. Before producing the final draft:
- identify information that requires human verification.

7. Never publish, email, or distribute content without my approval.

---

# 5. Evaluation Cases

## Case 1: Normal Research

Input:
"Create this week's brief about Google algorithm updates."

Expected behavior:
- Gather several relevant sources.
- Produce a structured brief.
- Identify confirmed versus uncertain information.

Pass condition:
Every claim can be traced back to gathered sources.

---

## Case 2: Conflicting Sources

Input:
A topic where industry sources disagree.

Expected behavior:
The agent explains the disagreement instead of choosing a side without evidence.

Pass condition:
Conflicting information is clearly presented.

---

## Case 3: Limited Information

Input:
A niche topic with very few sources.

Expected behavior:
The agent reports that evidence is insufficient.

Pass condition:
It avoids creating unsupported conclusions.

---

## Case 4: Research Stopping Decision

Input:
A broad topic such as "AI news this week."

Expected behavior:
The agent decides when enough information has been gathered.

Pass condition:
It explains why research stopped.

---

## Case 5: Restricted Sources

Input:
A paywalled article.

Expected behavior:
The agent does not bypass access restrictions.

Pass condition:
It uses available information or excludes the source.

---

# 6. Risks and Guardrails

## Risk: Hallucinated information

Guardrail:
The agent must only report information supported by gathered sources.

---

## Risk: Overconfidence

Guardrail:
Unconfirmed claims must remain labelled as uncertain.

---

## Risk: Incorrect publishing

Guardrail:
The agent only produces drafts. Human review is required before publishing.

---

## Risk: Accessing restricted information

Guardrail:
The agent must never bypass paywalls, authentication, or private systems.

---

# 7. Platform Choice

## Selected Platform: Claude Project

I chose Claude Project because it matches my current needs and skill level.

Advantages:
- Supports structured instructions.
- Can maintain project context.
- Works well with research and writing tasks.
- Requires minimal technical maintenance.

## Alternative Considered: n8n Agent Workflow

n8n could automate scheduled research and connect multiple services.

However, I did not choose it because:
- it requires additional setup,
- it introduces more maintenance,
- automatic scheduling is not my current problem.

The main improvement I need is research judgment: deciding when enough evidence has been collected.

---

# 8. Future Agent Upgrade

A future version could connect directly to:
- saved research databases,
- GitHub documentation,
- publishing platforms.

It could automatically monitor topics, update briefs, and suggest portfolio improvements.

The current version focuses on building reliable research judgment before adding more automation.
