# FahMai Enterprise Data-Agent — Website Write-up

> เนื้อหาอังกฤษพร้อมก๊อปวางเว็บ (เข้าธีมเดิม) + โน้ตไทย
> ใช้คู่กับสไลด์ที่มี (FULL PIPELINE / OCR BACKTEST / GUARDRAIL / RESULT / SECURITY) เป็นภาพประกอบในการ์ด

---

## 🟦 เวอร์ชันสั้น (การ์ดโปรเจกต์ / Hackathon card)

**Title:** `FahMai Enterprise Data-Agent — OCR-grounded Agentic Reasoning`
**Badge:** `🥇 WINNER — The Enterprise Data Agent Showdown (FahMai: The Finale)`
**Subtitle:** `Super AI Engineer S6 · AIAT × BOL × NCSA · Team Machima · Jun 2026`

**One-liner:**
> A secure enterprise AI agent that answers business questions over a company's own data — both **structured** (SQL tables) and **unstructured** (documents) — by grounding every answer in **OCR-extracted records** like bank statements and receipts, with **prompt-injection guardrails at every stage**.

**Highlights:**
- ReAct agent (Qwen 3 + **Typhoon 2-7B** Thai LLM) over **DuckDB** (SQL) + **ChromaDB** (vector/RAG)
- **OCR-to-data pipeline** (MinerU): bank-statement image → structured JSON → DuckDB
- **3-phase guardrail** (input → reasoning → output) against prompt injection & data leakage
- Served with **vLLM + Paged Attention + KV cache + FlashInfer**; up to **13.8× speedup** via RAG/SQL caching
- **Honest security finding:** router caught **100%** of syntactic injections; documented that the model resisted only **~40%** of *semantic/authority-framed* injections — flagged as a real limitation + future work

**Stack:** `Agentic AI (ReAct) · Qwen 3 · Typhoon 2-7B · MinerU OCR · ChromaDB · DuckDB · RAG · vLLM · KV Cache · FlashInfer · Guardrails · TLS`

---

## 🟩 เวอร์ชันยาว (หน้า project detail / expandable)

### What we built
An enterprise-grade **agentic AI assistant** for the Enterprise Data Agent Showdown. It takes a natural-language business question, decides which tools and data it needs, retrieves grounded evidence from company data, and returns a verified, policy-safe answer — judged on OCR accuracy, agent evaluation, system design, **cybersecurity**, and presentation.

### Architecture — three pipelines

**1) Agent pipeline (ReAct)**
User prompt → topic classification → an agent (Qwen 3 + Typhoon 2-7B) uses **ReAct** to call tools over two stores:
- **Structured data:** DuckDB / SQL tables
- **Unstructured data:** ChromaDB vector store (docs, reports, OCR text, logs, LINE)
→ retrieves relevant context → generates an initial response → guardrail-checked → final answer.

**2) OCR backtest pipeline**
- **Unstructured route:** OCR text → embeddings → ChromaDB
- **Structured route:** document image → **MinerU** (image → CSV) → rule-based extraction → JSON mapping → DuckDB
- *Example:* a bank-statement image becomes `{ "date": "...", "balance": 50000, "type": "deposit", "amount": 120 }` rows queryable in SQL.

**3) Guardrail pipeline (defense in depth)**
- **Phase 1 — Input Guard (pre-LLM):** normalize → detect → inspect → ALLOW / SANITIZE / BLOCK-ESCALATE
- **Phase 2 — Agent Reasoning:** unsafe injected instructions stripped, real business question preserved, then tool-calling
- **Phase 3 — Post-Validate Guard (post-LLM):** validate the answer for leakage of blocked/planted values, scrub disallowed phrases, return only a policy-safe response

### Performance & optimization
- **Serving:** vLLM with **Paged Attention** (KV cache in non-contiguous blocks → less VRAM fragmentation → bigger concurrent batches), **KV cache** reuse, and **FlashInfer**
- Hosted Thai LLM ran **~9× faster** than local; repeat sessions hit up to **13.8× speedup** thanks to RAG/SQL caching
- Profiled **tool-call latency**: each extra tool call ≈ **+15–20 s**, with context-overflow risk beyond ~10 calls; local OCR averaged ~330 s (**27× slower** than hosted) with a **58% fallback rate** — which drove our tool-calling optimization

### Security
- **TLS** session (cert + public key → verify → session key → encrypted comm.), **API-key protection**, and **governance / access control**
- **Prompt-injection testing (honest result):** the router achieved **100% detection** of syntactic overrides (e.g. `[SYSTEM_OVERRIDE PRIORITY=HIGH]`), but the model alone resisted only **~40%** of *authority-framed semantic* injections (e.g. a fake "policy memo" that silently skewed reported figures). We documented this gap as a known limitation and future hardening target.

---

## 📌 โน้ตก่อนวางเว็บ (ไทย)

1. **ระบุบทบาทตัวเองให้ชัด** — โปรเจกต์นี้ทำกันเป็นทีม (4 คนตามโปสเตอร์ Machima) เวลาเขียน/พูด ให้บอกว่า *คุณ* รับผิดชอบส่วนไหน (OCR pipeline? guardrail? agent? performance? security testing?) อย่าเขียนเหมือนทำคนเดียว — คนจ้างเจาะแน่
2. **เวอร์ชันโมเดล** — สไลด์เขียน "Qwen 3.6" ผมเขียนเป็น "Qwen 3" ไว้ก่อน ถ้ารู้เวอร์ชันจริงค่อยแก้ให้ตรง (Typhoon 2-7B เป็นชื่อจริงของ SCB10X ใช้ได้เลย)
3. **ใช้ภาพสไลด์เป็น visual** — FULL PIPELINE / OCR BACKTEST / GUARDRAIL วางในการ์ดได้เลย ช่วยให้ดูเป็นงานจริง
4. **จุดขายเด่นสุด** = ความซื่อสัตย์เรื่อง security (100% vs 40%) — อย่าตัดทิ้ง มันทำให้คุณดู "เข้าใจระบบจริง" ไม่ใช่แค่ทำให้เดโมผ่าน

---
*ก๊อปเฉพาะ copy ภาษาอังกฤษไปวาง จัดสไตล์ให้เข้าธีมเว็บได้เลย*
