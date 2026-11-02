# AI Recruitment Operations Agent

**A production tool for spotting recruitment delays and preparing the next action**

Recruiting a distributed, seasonal workforce creates a lot of small dependencies: a manager has not returned feedback, an application is missing information, or a candidate has been sitting at the same stage for too long.

I built a recruitment operations tool that turns those records into a prioritised list of issues. An AI assistant can investigate the queue, explain what needs attention and prepare follow-up drafts. **The person running recruitment remains responsible for decisions and sending communications.**

## The workflow

1. **Track the pipeline.** Candidate stage, hiring-manager ownership, interview dates, deadlines and activity sit in one view.
2. **Surface exceptions.** Explicit rules flag overdue feedback, missing ownership or information and stalled applications.
3. **Investigate and prepare.** The AI assistant reviews available records, identifies priorities and drafts suggested follow-ups for approval.

The distinction between rules and AI matters. An overdue deadline is determined from the record, not guessed by a language model; AI helps interpret the context and formulate a useful next step.

## What it looks like

These three screens use **fictional candidate records** to show the working interface.

### Candidate pipeline

A shared view of applications, ownership and outstanding feedback.

![Candidate pipeline with stages, ownership and feedback deadlines](images/1%20Candidate%20Pipeline.png)

### Attention queue

Rules identify issues, explain why they were flagged and propose a next step.

![Attention queue with prioritised recruitment issues](images/2%20Data.png)

### Agent investigation

The assistant presents its top priorities with supporting evidence and an editable follow-up draft. The annotations highlight the question, response and proposed action.

![Annotated AI agent investigation and draft follow-up](images/3%20Ask%20Agent%20to%20invesitgate.png)

## Implementation and safeguards

I defined the recruitment checks, built the interface and connected an AI assistant to a small set of tools for reading candidate and attention records and preparing drafts. The application uses **TypeScript and structured AI tool calls**.

Provider credentials remain server-side. Tool actions are validated and agent runs are bounded. The assistant does **not** autonomously reject applicants, assign hiring managers or send emails. Draft communications require human review.

The system passed **34 automated tests and a build** at a recorded development checkpoint, including an end-to-end AI tool-calling flow. The workflow is now **in production**.

## Operational value

Instead of opening each candidate record to work out what is late or missing, the coordinator starts with the exceptions that need attention. The agent helps turn those findings into a practical follow-up, without taking control of recruitment decisions.

It makes the hand-off from identifying a recruitment problem to taking action clearer, while leaving the final decision with the coordinator.

---

[← Back to portfolio](../README.md) · [Operations CRM](operations-crm.md) · [Image automation and AI vision](image-editing-automation-ai-vision.md)
