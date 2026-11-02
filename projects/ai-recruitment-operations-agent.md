# AI Recruitment Operations Agent

**Turning recruitment follow-up into a structured, reviewable workflow**

Recruitment across a distributed workforce involves more than screening applications. Hiring managers need to respond, candidate records need to be complete, and someone has to keep track of what is waiting on whom. When this work sits across inboxes and spreadsheets, delays are easy to miss.

I built and put into production an AI-assisted recruitment operations workflow to surface coordination issues automatically, while keeping decisions and external communications under human control.

> **Status:** In production. The technical testing described below used 10 fictional candidate records; those test records should not be confused with live recruitment data. Any time savings below are illustrative estimates, not measured results.

## At a glance

| | |
| --- | --- |
| **Business challenge** | Recruitment coordination depends on repeatedly checking candidate status, outstanding information and hiring-manager feedback |
| **Solution** | Rules-based checks paired with an AI assistant that investigates issues, prioritises next steps and prepares draft follow-ups |
| **My role** | Defined the operational problem, designed the workflow, built and tested the application and AI integration |
| **Safeguards** | Fictional test data, server-held API keys, validated tool actions, bounded agent execution and human approval before communications |
| **Technology** | TypeScript, AI tool calling via an OpenAI-compatible provider, automated tests |
| **Evidence** | Production use, with working end-to-end tool calling; 34 tests and build passing at the recorded development checkpoint |

## The operational problem

Recruitment creates many small administrative dependencies. A candidate may be waiting for feedback, a hiring manager may not have been assigned, or information required to progress an application may still be missing. Individually these are straightforward; across a busy hiring campaign they compete for attention.

The goal was to reduce time spent searching for exceptions and composing routine follow-ups, so the person coordinating recruitment could focus on resolving blockers.

## How I approached it

### 1. Translate operational issues into explicit checks

I started with a fictional candidate dataset and defined deterministic rules for issues such as:

- Overdue hiring-manager feedback
- Missing candidate or process information
- Candidates stalled in a stage for more than seven days

The checks identify what needs attention. This matters because a language model should not be the sole source of truth for whether a deadline has been missed.

### 2. Build an actionable queue

The application groups findings into an attention queue rather than leaving the user to inspect every candidate individually. The interface also includes a dashboard and draft queue, so an issue can move from identification to a proposed next action.

### 3. Add an AI assistant with narrow tools

The assistant can use defined functions to list candidates, inspect attention items and create follow-up drafts. Its role is to interpret the operational context, help identify priorities and prepare communications for review—not to make hiring decisions.

```mermaid
flowchart LR
    A["Fictional candidate records"] --> B["Rules identify exceptions"]
    B --> C["Attention queue"]
    C --> D["AI reviews available evidence"]
    D --> E["Suggested priorities and draft follow-ups"]
    E --> F["Human reviews and acts"]
```

### 4. Put limits around the automation

The implementation keeps provider credentials on the server and validates tool actions. Agent runs are bounded to prevent uncontrolled loops. Drafts remain drafts: the agent does not autonomously send emails, reject applicants or make hiring decisions.

## Implementation and testing

The application successfully completed an end-to-end AI tool-calling flow and passed 34 tests and its build at a recorded development checkpoint. The workflow is now used in production.

It also revealed practical limitations worth addressing before deployment:

- Repeated runs could create duplicate drafts.
- The agent sometimes overemphasised email drafting rather than clearly explaining the highest-priority operational issues.
- Missing-information cases were not always handled with a useful draft or next step.

These findings informed ongoing improvements: a useful operations agent needs dependable prioritisation, idempotent actions and clear escalation—not simply fluent text.

## Potential operational impact

For planning purposes, I modelled a recruitment coordination task falling from **2 hours to 30 minutes per week**. That would represent **90 minutes of potential weekly capacity**, or **18 hours over a 12-week campaign**.

**This is a scenario estimate, not an observed saving.** A measured baseline and comparison of time spent would be needed before presenting this estimate as an achieved saving.

## What I would improve next

1. Prevent duplicate drafts and make each action traceable.
2. Separate **urgent blockers**, **awaiting responses** and **routine follow-ups** more clearly.
3. Improve explanations of why a candidate needs attention and what evidence supports the recommendation.
4. Continue evaluating human review and approval in day-to-day use.
5. Continue reviewing authentication, permissions, data-retention controls and privacy safeguards for live candidate data.

## Why this project matters

This project is an example of applying AI to a specific operational problem: understand the work, define reliable rules, introduce AI only where interpretation or drafting helps, and test the whole workflow against the realities of daily use.

It also reinforced an important lesson: the quality of an AI-enabled process depends as much on exception handling, ownership and human judgement as on the model itself.

---

[← Back to portfolio](../README.md) · [Operations CRM case study](operations-crm.md)
