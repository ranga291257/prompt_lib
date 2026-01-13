# Model Selection for Domain-Specific LLM Workflows

## 1. Purpose

This note guides selection of LLMs for domain-specific, safety-conscious workflows (plant operations, maintenance and engineering, technical services). The aim is the right trade-off between reasoning quality, data control, cost, and deployment constraints, not “biggest model wins.”

Use this as a companion to prompts like `ot-historian-replacement.md` and `ai-technical-services-workflow.md`.

---

## 2. Model Types and When to Use Them

### 2.1 General-purpose frontier models

**What**  
Large proprietary models (e.g. GPT/Claude/Gemini class) via API, with strong reasoning, broad knowledge, and long context.

**Use when**  
- Designing new workflows and prompts.  
- Doing complex reasoning and synthesis across long technical docs.

**Pros**  
- Top raw quality and reasoning.  
- Zero infra: quick to start.

**Cons**  
- Data leaves your boundary; may not meet OT/regulatory constraints.  
- Ongoing API cost; limited control over weights and safety tuning.

---

### 2.2 Open-source / self-hosted base models

**What**  
Foundation models you run yourself (e.g. Llama-family, Gemma, Qwen, DeepSeek, etc.) on-prem or in a controlled VPC.

**Use when**  
- Data residency, OT security, or regulatory rules require strong data control.  
- You can operate GPU/infra or have a platform that abstracts it.

**Pros**  
- Full control over deployment, logging, guardrails.  
- Lower marginal cost at scale; quality improving rapidly.

**Cons**  
- You own reliability, upgrades, and incident handling.  
- Quality may trail top proprietary models slightly on some tasks.

---

### 2.3 Domain-specific and fine-tuned models

**What**  
Models adapted on your sector’s data (procedures, RCAs, maintenance logs, standards) or industry-tuned variants.

**Use when**  
- Workflows are repetitive and domain-heavy (process safety, maintenance strategy, technical services).  
- You can curate representative domain data and eval sets.

**Pros**  
- Better on domain jargon, failure modes, and document formats.  
- More aligned with your templates and standards.

**Cons**  
- Upfront work: data cleaning, labeling, evaluation harness.  
- Risk of overfitting if data is narrow or biased.

---

## 3. Open vs Proprietary (Quick View)

| Dimension          | Open-source / Self-hosted                 | Proprietary API                     |
|-------------------|--------------------------------------------|-------------------------------------|
| Data control       | Strong – stays in your infra              | Weaker – goes to vendor             |
| Customization      | High – fine-tune, adapters, control stack | Moderate – mainly prompt + RAG      |
| Upfront complexity | Higher – infra + MLOps                    | Lower – plug-and-play               |
| Cost at scale      | Lower per-token; infra overhead           | Pure usage fees, no infra           |
| Peak quality       | Very good, catching up fast               | Slight edge today in many benchmarks|

For regulated or safety-critical plants, bias toward open/self-hosted plus strong governance, even if you prototype with proprietary APIs first.

---

## 4. “Thinking” Requirements for Technical Workflows

For prompts in this repo, any chosen model should:

- **Support explicit reasoning**  
  - Follow step-by-step instructions (chain-of-thought style) and handle ambiguity by asking for more data instead of guessing.

- **Work well with RAG and tools**  
  - Accept long context from historians/CMMS/docs via RAG and respect citations/traceability.  
  - Run inside m
