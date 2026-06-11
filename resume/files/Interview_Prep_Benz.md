# คู่มือติวก่อนสัมภาษณ์ (อัปเดตหลังเห็นพอร์ตจริง) — เบนซ์

> เป้าหมาย: Internship LV.3 + จูเนียร์ Data Scientist / AI Engineer
> ความจริงใหม่: **คุณแข็งกว่าที่เรซูเม่ชุดแรกสื่อมาก** คุณมีโปรเจกต์ ML จริงที่มี metric — งานสัมภาษณ์จะไม่ใช่ "พิสูจน์ว่ารู้ DS ไหม" แต่เป็น **"อธิบายของที่ทำมาให้ลึกได้ไหม"**

---

## 0. ต้องเช็กก่อนส่ง (สำคัญ)

- [ ] **README ภาษาอังกฤษในทุก GitHub repo** — `minierpbybez`, `billbybz` คนจ้างกดเข้า GitHub แล้วดู README ก่อนโค้ด ถ้าว่างเปล่า = เสียโอกาส (ให้ผมช่วยเขียนได้)
- [ ] **Demo credentials ที่โชว์บนเว็บ** (admin / รหัส) — โอเคสำหรับเดโม แต่ถ้าถูกถามให้บอกได้ว่า "ตั้งใจเปิดเป็น demo account ข้อมูลไม่ sensitive" แสดงว่าคุณคิดเรื่อง security
- [ ] **วันที่ให้ตรงกันทุกที่** — เรซูเม่ชุดนี้ใช้ Graphic Designer = 2021–2023 (ตามเว็บ) ไฟล์เก่าเคยเป็น 2024–2025 ลบความสับสนให้หมด
- [ ] LinkedIn อัปเดตให้ตรงกับเรซูเม่

---

## 1. ของที่ต้องอธิบายให้ลึก (interviewer จะเจาะแน่)

คุณเขียน metric ไว้ในเรซูเม่ = คุณเปิดประตูให้เขาถามลึก **เตรียมตอบทุกข้อ**

### Edge AI (Jetson Nano) — โปรเจกต์เรือธง
- **"ทำไม MobileNetV3-S ไม่ใช่โมเดลใหญ่กว่า?"** → รันบน edge ต้องเบา+เร็ว แลกความแม่นกับ FPS
- **"TensorRT FP16 ช่วยยังไงถึงเร็วขึ้น 6×?"** → layer fusion + ลด precision (FP32→FP16) คำนวณเร็วขึ้นบน GPU โดยความแม่นแทบไม่ตก
- **"YOLO ต่างกับ MobileNet ตรงไหน?"** → YOLO = detect หากล่องรถ, MobileNet = classify ยี่ห้อ/สีของรถที่ crop มา
- **"เป็น Data Team Lead ทำอะไร?"** → แบ่งงาน 4 squad, pre-label + QC, ปัญหา label จริง (Toyota/Honda สลับ, MG5 เป็น Benz)

### Demand Forecasting (CatBoost WMAPE 8.85)
- **"WMAPE คืออะไร ทำไมใช้?"** → Weighted Mean Absolute Percentage Error วัด error เทียบยอดจริง เหมาะกับยอดที่ต่างกันมากต่อสาขา **ต้องตอบได้แน่นอน**
- **"ทำไม CatBoost ชนะ ARIMA?"** → ARIMA จับ seasonality หยาบได้ แต่พลาด spike แรง (วันหยุด/payday); boosted trees ใช้ฟีเจอร์ lag+calendar ได้ดีกว่า
- **"feature engineering ทำอะไร?"** → 6 กลุ่ม: lag/rolling, cyclical calendar (sin/cos), store, KMeans cluster, promotion, local event
- **"กัน overfitting ยังไง?"** → train/val split ตามเวลา, ดู validation error, regularization

### RAG (FahMai)
- **"embedding / vector DB คืออะไร?"** → แปลงข้อความเป็นเวกเตอร์ วัดความใกล้เคียงเชิงความหมาย
- **"3-model cascade ทำไม 3 ตัว?"** → relevance filter → re-rank → generate ลด noise ก่อนให้ LLM ตอบ
- **"semantic chunking ดีกว่าตัดตามตัวอักษรยังไง?"** → ตัดตามความหมาย ไม่ตัดกลางประโยค retrieve แม่นขึ้น

### OCR Human-in-the-Loop
- **"ทำไมต้องมี HITL?"** → งานผิดไม่ได้ ให้ AI ทำ 95% ที่มั่นใจ ส่ง 5% confidence ต่ำให้คนเช็ก
- **"confidence routing ตัดที่เท่าไร?"** → threshold ~0.75 และ trade-off speed vs accuracy

### Enterprise Data Agent (FahMai Finale — โปรเจกต์ที่ชนะ 🏆)
- **"ทำไมถึงชนะ / ต่างจากทีมอื่นยังไง?"** → เตรียมเล่าจุดเด่น: ความแม่น OCR, HITL, การออกแบบให้ใช้จริงในองค์กร
- **"โจทย์มีเรื่อง cybersecurity ด้วย — จัดการข้อมูล statement/ใบเสร็จที่ sensitive ยังไง?"** → เตรียมตอบเรื่อง data privacy, ไม่ leak ข้อมูลเข้า LLM ภายนอกโดยไม่จำเป็น, การ validate input **(กรรมการจาก BOL/สกมช. เน้นเรื่องนี้)**
- **"agent ต่างกับ chatbot ธรรมดายังไง?"** → agent วางแผน+เรียกใช้ tool/ขั้นตอนเองได้ ไม่ใช่แค่ตอบข้อความ

### WellSense AIoT "Sip" (โปรเจกต์ใหม่ — รางวัลพิเศษ)
- **"ทำไมประมวลผลบน edge (UNO Q) ไม่ส่งขึ้น cloud หมด?"** → latency ต่ำ, ทำงาน real-time, ประหยัด bandwidth, privacy
- **"rule-based engine ทำไมไม่ใช้ ML?"** → ข้อมูล/เวลาจำกัด, rule อธิบายได้และเชื่อถือได้สำหรับ health, เป็น baseline ที่ดี
- **"BLE กับ 8 sensors จัดการ noise/sampling ยังไง?"** → validation + filtering layer ในไปป์ไลน์
- เตรียมเล่าบทบาทตัวเองในทีมให้ชัด (ทำ layer ไหน: sensor / edge / dashboard / data)

> **สำคัญ:** hackathon บ้าน Machima แบ่งเป็นทีมย่อย — **ยืนยันให้ได้ว่าคุณอยู่ทีมที่ชนะจริง และทำส่วนไหน** อย่าเคลมงานที่ไม่ได้ทำ พูดบทบาทตัวเองให้ตรง

> **เทคนิค:** เปิดเว็บพอร์ตตัวเองอ่านซ้ำก่อนสัมภาษณ์ — flow diagram อยู่ครบแล้ว ทบทวนให้พูดลื่น

---

## 2. พื้นฐานที่ควรกันเหนียว (เผื่อถูกถามตรงๆ)

- **ML พื้นฐาน:** supervised vs unsupervised, classification vs regression, train/val/test, overfitting/underfitting
- **Metric:** accuracy/precision/recall/F1 ต่างกันยังไง, เมื่อไหร่ accuracy หลอก (imbalanced), WMAPE/MAE/RMSE
- **pandas + SQL:** groupby, merge/join, filter — ฝึกบน Colab สัก 2 ชม.
- **Python/CS:** list/dict, complexity เบื้องต้น, อ่านโค้ดตัวเองอธิบายได้
- **Git:** commit/branch/merge/PR

👉 ไม่รู้จริงๆ ตอบตรงๆ + "ผมจะหาแบบนี้..." — จูเนียร์/อินเทิร์นเขาดู **วิธีคิด + เรียนรู้ได้** มากกว่ารู้ครบ

---

## 3. คำถามยอดฮิต + แนวตอบ

| คำถาม | แนวทาง |
|------|--------|
| เล่าโปรเจกต์ที่ภูมิใจสุด | **Edge AI** — ปัญหา → บทบาท Data Lead → pipeline → ผล ~18 FPS → สิ่งที่เรียนรู้ |
| ทำไมจากดีไซน์มาสาย AI/Data | "Art eye, data mind" — สายตาดีไซน์ช่วย EDA/visualization/UX ของ dashboard |
| จุดอ่อน | "เพิ่งเริ่มทำงานเป็นทีมจริงจังตอน camp — กำลังพัฒนา collaboration + ทฤษฎี DS เชิงลึก" |
| ใช้ AI ช่วยโค้ดเยอะไหม | "ใช้เร่งงาน แต่อ่าน/แก้/debug เองได้" — เตรียมโดนขออธิบายโค้ดสักส่วน |
| ทำไมยังเป็น LV.2 / หางานช่วงนี้ | "หา internship LV.3 เพื่อเอาของในห้องเรียนไปใช้จริง" — เป็นจังหวะปกติของโปรแกรม |
| เงินเดือน | หาเรตอินเทิร์น/จูเนียร์ในตลาดก่อน ตอบเป็นช่วง |

---

## 4. แผนทบทวน 1 สัปดาห์

1. **วัน 1–2:** อ่านเว็บพอร์ต + เปิดโค้ด/notebook ทุกโปรเจกต์ ฝึกเล่าแต่ละอันใน 2 นาที
2. **วัน 3:** ทฤษฎี ML + metric (โดยเฉพาะ WMAPE, precision/recall, overfitting)
3. **วัน 4:** RAG + embedding + vector DB + TensorRT/edge เล่าแบบเข้าใจจริง
4. **วัน 5:** pandas + SQL ลงมือจริง
5. **วัน 6:** Git + อ่านโค้ดตัวเองอธิบายทีละส่วน
6. **วัน 7:** ซ้อมตอบตาราง ข้อ 3 ออกเสียงจริง + เตรียมคำถามย้อนถามบริษัท

---

## 5. กฎทอง 3 ข้อ

1. **ทุก metric ที่เขียน ต้องเล่าที่มาได้** — เล่าไม่ได้ ตัดออก
2. **ดึงคำถามกลับมาที่ของจริงที่ทำ** — คุณมีของเยอะ ใช้เป็นอาวุธ
3. **ไม่รู้บอกไม่รู้ แล้วต่อด้วยวิธีคิด** — คนจ้างมองหา "คนเรียนรู้ได้"

---
*ปรับให้ตรงกับบริษัท/ตำแหน่งจริงอีกทีก่อนสัมภาษณ์*
