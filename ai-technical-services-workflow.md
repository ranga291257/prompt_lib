# AI-Driven Technical Services Workflow (Plant Ops)

## 1. Intent

Design or refactor a **technical services** workflow in plant operations so that:
- AI handles repetitive, data-heavy steps.
- Humans stay in the loop for safety, compliance, and high-consequence decisions.
- Productivity is quantified step-by-step via an AI Multiplication Factor (N), not generic “10×” claims.

Use this as a companion to the historian prompt for work that spans historians, CMMS, ERP, logs, and field observations.

---

## 2. Core Prompt

ROLE  
You are a senior technical services lead supporting operating plants (process, mining, utilities, or discrete manufacturing). Your task is to redesign one technical-services workflow as an AI-enabled, Human-in-the-Loop (HIL) workflow that preserves safety, regulatory compliance, and clear human accountability.

OBJECTIVES  
- Split the workflow into granular steps and label each as:
  - HIL (human-in-the-loop, with AI assist), or  
  - AI-executable (autonomous within guardrails).  
- Assign an AI Multiplication Factor (N) to each step and justify it briefly.  
- Specify guardrails, escalation rules, and auditability requirements.  
- Show how to involve new graduates as “system designers” and reviewers, not only as data janitors.

CONTEXT  
Assume a plant with:
- DCS/PLC/SCADA, historian, CMMS/EAM, and a document system; digital maturity is mixed (some paper, some spreadsheets, some APIs).  
- HSE and regulatory standards where high-consequence decisions must always have human sign-off.  
- LLM + RAG over procedures, RCAs, OEM manuals, and logs, plus basic time-series analytics over historian/CMMS tags.  
- Workforce mix: senior SMEs with deep tacit knowledge and new grads comfortable with scripting, data tools, and prompt engineering.

---

## 3. Required Output (Short Form)

Ask the model to produce these sections, compact but explicit:

1) **Current Workflow (5–10 bullets)**  
- Brief bullets with: step name, main actor, inputs (systems, field data), tools used, and pain points.  
- Flag each step as: High / Medium / Low field coupling, and High / Medium / Low consequence if wrong.  

2) **Step Table with N and Modality**

Create a table with at least these columns:

- Step ID / Name  
- Inputs (systems, documents, or field observations)  
- Field Coupling (H/M/L)  
- Risk / Consequence (Safety / Env / Reliability / Commercial / Low)  
- Auditability Needed (High / Low)  
- Proposed Modality (HIL vs AI-executable)  
- AI Multiplication Factor N (e.g., 1.0, 1.5, 3, 7)  
- One-line justification for N  

Guidance:  
- High-risk + high field-coupling → HIL, modest N.  
- Digital, repetitive, low-risk → candidate for higher N and more automation.

3) **Future-State Flow (Narrative or ASCII)**  
- Show where data flows from historian/CMMS/docs into AI tools, and back into CMMS, reports, MOCs, or action logs.  
- Mark explicit HIL checkpoints where humans review, override, or approve AI suggestions.  
- Highlight how operator / engineer workload changes (less grunt work, more exception handling and decisions).

4) **Guardrails, Escalation, Accountability (Bullets)**  
- Guardrails on:
  - What AI is allowed to change or create (drafts, suggestions, pre-filled work orders).  
  - Confidence thresholds that trigger mandatory human review.  
- Escalation paths when:
  - AI confidence is low, data conflicts, or risk is high.  
- Accountability:
  - Who signs off for changes affecting safety, environment, or major economics.  
  - How logs / audit trails capture AI suggestions and human decisions.

5) **New-Grad Involvement Plan (3–6 bullets)**  
- Where new grads configure prompts, RAG scopes, tags, and dashboards under SME supervision.  
- How they help define exception rules and triage logic.  
- How they run periodic “sanity checks” comparing AI outputs to actual plant events, making recommendations to tune the workflow.

6) **Pilot Outline (4–6 weeks, very brief)**  
- Choose 1 workflow + 1 area + 2–3 engineers (incl. a new grad).  
- Baseline current time/effort and error/rework.  
- Run AI in shadow mode, then HIL mode.  
- Recalculate N from real data and document what worked vs failed.

---

## 4. Example Invocation

> “Use this template to redesign our weekly reliability review workflow for rotating equipment in Unit 200. Assume OSIsoft/AVEVA PI as historian, Maximo (or similar) as CMMS, and PDF RCAs stored in SharePoint. Include a section on how to use new grads to configure and monitor the workflow in month 1–2.”

---

## 5. When to Use / When Not To

Use this prompt when:
- You have at least partial digital signals (historian/CMMS/logs) and repeatable technical-services work.  
- You need a defensible story of where AI accelerates work and where human judgment remains dominant.

Do not use as-is when:
- The workflow is dominated by field investigation with little digital trace.  
- Safety or regulatory risk is so high that even AI pre-analysis must be heavily constrained—adapt the guardrails section first.
