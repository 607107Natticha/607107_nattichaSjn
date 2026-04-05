# Portfolio & Resume — Natticha (Benz)

เว็บไซต์พอร์ตโฟลิโอส่วนตัว (ไฟล์เดียว `index.html` + สื่อประกอบ) ใช้ **HTML + Tailwind CSS (CDN)** แสดงผลงานด้านเว็บและระบบอัตโนมัติ พร้อมหน้า **Resume** ภาษาอังกฤษ/ไทย และพิมพ์เป็น PDF ได้

**GitHub:** [607107_nattichaSjn](https://github.com/607107Natticha/607107_nattichaSjn)

---

## โปรเจกต์ที่แสดงบนเว็บ (สรุปเข้าใจง่าย)

| โปรเจกต์ | คืออะไร (สั้นๆ) |
|-----------|------------------|
| **MINI-ERP / Smart ERP** | ระบบ ERP บนเว็บสำหรับ SME — จัดซื้อ คลัง ขาย เอกสาร อนุมัติ ในที่เดียว ใช้ Django + Vue 3 มีคลิปสาธิต `miniocr.mp4` |
| **SabaiBill** | แอปเอกสาร SME (QT/SO/DO/IV) แปลงต่อเนื่อง คำนวณ VAT/WHT ส่วนลด พิมพ์ PDF ตั้งค่าบริษัท–เทมเพลต–QR ชำระเงิน UI ไทย/อังกฤษ คลิป `saibaiiii.mp4` · React, Node.js, Prisma |
| **CJP Frozen Food** | เว็บแคตตาล็อก B2B + ขอใบเสนอราคา/PO เชื่อม **LINE Notify** แจ้งทีมแบบเรียลไทม์ |
| **Yuki Pepper Art Store** | ร้านอีคอมเมิร์ซงานศิลปะ สไตล์มินิมอล แจ้งเตือนออเดอร์ผ่าน LINE |
| **Workflow Automation (Make.com)** | เวิร์กโฟลว์ **Integration LINE** — รับรูปจาก LINE → OCR → ดึงเลขพัสดุ → บันทึก Google Sheets → ส่ง Push Message คลิป `ocr.mp4` |

หน้า **Resume** สรุปประสบการณ์ ทักษะ และโปรเจกต์ข้างต้นแบบย่อ — สลับ EN/TH และกด **Save as PDF** ได้

---

## วิธีเปิดดูในเครื่อง

1. โคลน repo นี้
2. เปิดไฟล์ `index.html` ด้วยเบราว์เซอร์  
   หรือใช้เซิร์ฟเวอร์ท้องถิ่น เช่น `npx serve .` แล้วเข้า URL ที่ขึ้น

> ต้องมีไฟล์วิดีโอ `miniocr.mp4`, `ocr.mp4` อยู่โฟลเดอร์เดียวกับ `index.html` ถึงจะเห็นคลิปในพอร์ตโฟลิโอครบ

---

## โครงสร้างโฟลเดอร์หลัก

```
index.html          # เว็บพอร์ตโฟลิโอ + เรซูเม่
miniocr.mp4         # คลิปสาธิต MINI-ERP
saibaiiii.mp4       # คลิปสาธิต SabaiBill
ocr.mp4             # คลิปสาธิตเวิร์กโฟลว์ Make.com + LINE
image/              # รูปประกอบ (ถ้ามี)
```

---

## เจ้าของผลงาน

**Natticha Satjawatthana (Benz)** — Web Developer & System Automator  
