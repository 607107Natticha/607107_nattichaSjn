# Website Additions & Improvements — index-v2.html

> เนื้อหาภาษาอังกฤษพร้อมก๊อปวางลงเว็บ (ให้เข้ากับสไตล์เดิม) + โน้ตปรับปรุงเป็นภาษาไทย
> **หัวใจของรอบนี้: เว็บยังไม่ได้โชว์ว่าคุณ "ชนะ" — ต้องชู WIN ให้เด่นที่สุด**

---

## 🏆 1. เพิ่ม "Wins" ให้เด่น (สำคัญสุด)

ตอนนี้ metrics โชว์แค่ "5 Hackathons / 5 Projects / 3 Deployments" — **ขาดของที่ทรงพลังที่สุดคือผลแพ้ชนะ** เพิ่ม:

**Hero / ใต้ชื่อ — เพิ่ม badge:**
```
Super AI Engineer S6 · Team Machima · 2× Hackathon Winner
```

**Metrics block — เพิ่มตัวเลขที่ 4:**
```
2   Hackathon Wins (1st place)
```
หรือทำเป็นแถบ Awards:
```
AWARDS
🥇 FahMai Finale — Enterprise Data Agent Showdown · WINNER
🥇 Edge-AI for Intelligent Transport (NT) · WINNER
⭐ WellSense AIoT — Judges' Favorite (ขวัญใจพ่อยกแม่ยก)
```

---

## 2. แก้การ์ด FahMai → ใส่สถานะ WINNER + ราย​ละเอียด Finale

การ์ด OCR/Agentic เดิม ให้รีไรต์เป็น "การ์ดที่ชนะ" แบบนี้:

**Title:** `Enterprise Data Agent — FahMai: The Finale`
**Badge:** `🥇 WINNER · The Enterprise Data Agent Showdown`
**Subtitle:** `Super AI Engineer S6 · AIAT × BOL × NCSA · 4 Jun 2026`

**What I built (copy):**
> An enterprise-grade **agentic AI + OCR** system: it extracts data from business documents — bank statements and receipts — then reasons over that data to answer questions. Built with a **human-in-the-loop** review stage so low-confidence extractions are checked before they reach downstream systems.

**Judged on (copy):**
> OCR performance, system testing, Agentic AI model evaluation, system design & technical correctness, **cybersecurity**, and presentation — with emphasis on a system that works in a real enterprise.

**Flow:** `Documents (statement / receipt) → OCR → Confidence Scorer → HITL (low-conf) → Agentic LLM Reasoning → Answer / JSON`
**Result metric:** `95% auto · 5% human-checked · >99.2% field-level accuracy`
**Stack:** `Agentic AI · PaddleOCR · LLM Extraction · RAG · Vector DB · HITL · JSON Schema`

---

## 3. เพิ่ม badge WINNER ให้การ์ด Edge AI (มีอยู่แล้ว แค่เติมผล)

**Badge:** `🥇 WINNER · Edge-AI for Intelligent Transport System`
**Subtitle:** `Super AI Engineer S6 · AIAT × NT (National Telecom) · Data Team Lead`
เนื้อหาเดิมดีอยู่แล้ว แค่เพิ่มประโยคนำ:
> **1st place** in NT's Intelligent Transport System challenge. As **Data Team Lead**, I coordinated data collection, pre-labeling, and QC across a 4-squad team.

---

## 4. เพิ่มการ์ดใหม่ทั้งหมด — WellSense AIoT "Sip" (ยังไม่มีในเว็บ)

นี่คือโปรเจกต์ใหม่ที่เพิ่มมิติ **IoT / Embedded / Health-tech** ให้คุณ — ใส่ภาพ technical diagram ที่มีอยู่แล้ว

**Title:** `WellSense AIoT — "Sip" Smart Wellness Monitor`
**Badge:** `⭐ Special Award — Judges' Favorite (ขวัญใจพ่อยกแม่ยก)`
**Subtitle:** `Super AI Engineer S6 · Qualcomm × iMake × Faculty of Medicine, Chulalongkorn · WellSense AIoT Hackathon`

**What I built (copy):**
> An edge-AIoT device that monitors hydration and wellness in real time. Built on an **Arduino UNO Q** main hub with **8 sensors** (ultrasonic bottle-volume, gyro motion, temperature, EEG-based physiological input) streaming over **BLE**. A real-time pipeline cleans and validates the signals, a **rule-based intelligence engine** evaluates caffeine/sugar/water thresholds, and a live dashboard ("Sip") plus a **UNO Q LED matrix** gives instant **GOOD / MID / STOP** feedback.

**Why it was hard (copy):**
> A tightly constrained brief — limited hardware, 8 sensors, and a brand-new Arduino UNO Q board — pushed every design decision toward efficient, real-time edge processing.

**Pipeline:** `Sensors → UNO Q (Edge) → BLE → Stream Processing → Validation → Feature Store → Rule Engine → Dashboard + LED Feedback`
**Stack:** `Arduino UNO Q · C++ · Python · BLE · Supabase · HTML/CSS/JS · Ultrasonic / Gyro / Temp / EEG sensors`
**Image:** ใช้ technical diagram ที่อัปโหลด (วาง full-width ในการ์ดนี้)

---

## 5. Certifications — เพิ่ม TPQI

ในหมวด Certifications เพิ่ม:
> **TPQI — AI Competency Certification** · awarded together with **Huawei (HCCDA)** at the Super AI Engineer S6 camp.

(ใส่ credential ID/วันที่จริงถ้ามี)

---

## 6. โน้ตปรับปรุงเว็บ (ภาษาไทย)

1. **เปลี่ยนไฟล์ CV ที่ปุ่ม Download** — ตอนนี้ลิงก์ไป `Tech Portfolio.pdf` เวอร์ชันเก่า → อัปโหลด `Natticha_Resume.pdf` ใหม่ที่เพิ่งทำ (มีผลรางวัลแล้ว)
2. **Demo credentials (admin / รหัส) ที่โชว์หราบนหน้า** — ควรซ่อนหรือใส่ปุ่ม "Show demo login" และระบุชัดว่าเป็น demo account เพื่อความปลอดภัย (ตอนนี้รหัสจริงโชว์ใน HTML ใครก็เห็น)
3. **ใส่ลิงก์ GitHub ในทุกการ์ดโปรเจกต์/แฮกกาธอน** — โดยเฉพาะ AIoT "Sip" ถ้ามี repo/notebook
4. **เพิ่มแถบ Awards สรุปด้านบน** (ข้อ 1) ให้คนเห็นภายใน 3 วินาทีว่าคุณชนะอะไรบ้าง
5. **ความสม่ำเสมอของวันที่** — ให้ตรงกับ CV (Graphic Designer 2021–2023)
6. **meta description** อัปเดตให้มีคำว่า "2× hackathon winner" เพื่อ SEO เวลาแชร์ลิงก์

---
*ก๊อปเฉพาะ copy ภาษาอังกฤษไปวาง ส่วนสไตล์/HTML จัดให้เข้ากับธีมเดิมของเว็บได้เลย*
