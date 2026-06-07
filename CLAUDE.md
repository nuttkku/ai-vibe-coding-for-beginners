# CLAUDE.md — ภาพรวมโปรเจกต์ Vibe Coding for Beginners

## ข้อมูลหลักสูตร

**ชื่อ:** Vibe Coding สำหรับผู้เริ่มต้น
**ระยะเวลา:** 2 วัน (วันละ 6 ชั่วโมง)
**รูปแบบ:** Workshop Hands-on
**กลุ่มเป้าหมาย:**
- ครูคอมพิวเตอร์ที่ไม่ได้เขียนโปรแกรมมานาน
- ผู้ที่ใช้คอมพิวเตอร์เป็น แต่ไม่มีพื้นฐานการเขียนโค้ด
- ผู้ที่ต้องการนำเทคนิคไปต่อยอดสอนนักเรียนหรือสร้างชิ้นงานจริง

---

## เป้าหมายหลักของหลักสูตร

1. ผู้เรียนสร้างโปรเจกต์จริงได้โดยใช้ AI เป็นผู้เขียนโค้ด
2. เข้าใจ Loop การทำงาน: บอก AI → ดูผล → แก้ไข → บันทึก
3. ไม่กลัว Error และให้ AI ช่วยแก้ปัญหาได้
4. รันโปรแกรมด้วย Docker ได้อย่างสมบูรณ์
5. บันทึกประวัติงานด้วย GitHub Desktop (GUI ไม่ใช่ CLI)

---

## เครื่องมือที่ใช้

| เครื่องมือ | เวอร์ชันที่แนะนำ | หมายเหตุ |
|---|---|---|
| VS Code | ล่าสุด | Code Editor หลัก |
| GitHub Desktop | ล่าสุด | ใช้แทน git CLI ทั้งหมด |
| Docker Desktop | ล่าสุด | ต้องการ WSL2 บน Windows |
| Ollama | ล่าสุด | รัน Local LLM |
| Model: qwen2.5-coder:7b | 7b | `ollama pull qwen2.5-coder:7b` |
| Cline Extension | ล่าสุด | AI Assistant ใน VS Code |

---

## โครงสร้าง Outline หลักสูตร

### วันที่ 1: เข้าใจเครื่องมือ และคุยกับ AI ครั้งแรก

**ช่วงเช้า (09:00 - 12:00)**
- Session 1.1 (09:00-09:45): ปฐมนิเทศ — Vibe Coding คืออะไร? การเปลี่ยนบทบาทจาก "ผู้พิมพ์โค้ด" เป็น "ผู้สั่งการและตรวจสอบ"
- Session 1.2 (09:45-11:30): ติดตั้ง Environment — Docker, Ollama, VS Code, Cline, GitHub Desktop, Download Model
- Session 1.3 (11:30-12:00): ทดสอบระบบ — ตรวจสอบว่า Cline คุยกับ Local LLM ได้

**ช่วงบ่าย (13:00 - 16:00)**
- Session 1.4 (13:00-14:00): Prompt Engineering — บริบท + เป้าหมาย + ข้อจำกัด
- Session 1.5 (14:00-15:00): สร้างไฟล์ HTML แรก — Loop บอก → ดูผล → แก้ไข
- Session 1.6 (15:00-16:00): Git พื้นฐานด้วย GitHub Desktop — ⚠️ ใช้ GUI ไม่ใช่ CLI

### วันที่ 2: สร้าง Project จริง และรันด้วย Docker

**ช่วงเช้า (09:00 - 12:00)**
- Session 2.1 (09:00-09:30): ทบทวน Loop การทำงาน 4 ขั้นตอน
- Session 2.2 (09:30-10:30): Docker — แนวคิด + Dockerfile ด้วย AI
- Session 2.3 (10:30-12:00): Workshop "สร้างเว็บกล่องรับความคิดเห็น" ตั้งแต่ศูนย์

**ช่วงบ่าย (13:00 - 16:00)**
- Session 2.4 (13:00-14:30): Debug ด้วย AI + Rollback ด้วย GitHub Desktop
- Session 2.5 (14:30-15:30): ระดมสมองไอเดีย Project เพื่อการศึกษา
- Session 2.6 (15:30-16:00): สรุปและ Q&A

---

## โครงสร้างไฟล์ในโปรเจกต์นี้

```
/
├── README.md                   ← คู่มือหลักและตารางอบรม (สำหรับผู้เรียน)
├── CLAUDE.md                   ← ภาพรวมโปรเจกต์ (ไฟล์นี้)
├── outline.md                  ← Outline ต้นฉบับ (ร่าง)
├── WORKSHOP-AGENDA.md          ← ตาราง Agenda แยก (ยุบรวมใน README แล้ว)
├── LAB-01-SETUP/               ← ติดตั้งโปรแกรมทั้งหมด
├── LAB-02-FIRST-CHAT/          ← คุยกับ AI ครั้งแรก
├── LAB-03-PROMPT-ENGINEERING/  ← Prompt Engineering
├── LAB-04-FIRST-HTML/          ← สร้างหน้าเว็บแรก
├── LAB-05-GIT-DESKTOP/         ← Git ด้วย GitHub Desktop GUI
├── LAB-06-DOCKER/              ← Docker + Dockerfile
├── LAB-07-FEEDBACK-APP/        ← Workshop: Feedback Web App
└── LAB-08-DEBUG-ROLLBACK/      ← Debug + Rollback
```

---

## การตัดสินใจออกแบบสำคัญ

### ใช้ GitHub Desktop แทน git CLI
- เหตุผล: กลุ่มเป้าหมายคือครูที่ไม่ถนัดบรรทัดคำสั่ง
- ผลกระทบ: ไม่มี `git init`, `git add`, `git commit` ใน LAB ใดเลย
- ทุก LAB ใช้คลิกผ่าน GUI ทั้งหมด

### ใช้ LocalLLM (Ollama + Qwen2.5-Coder:7b) แทน Cloud API
- เหตุผล: ใช้งานออฟไลน์ได้, ไม่มีค่าใช้จ่าย, เหมาะกับโรงเรียน
- ข้อจำกัด: ต้องการ RAM อย่างน้อย 8GB, ดาวน์โหลดโมเดล ~4-5GB ล่วงหน้า

### Workshop ชิ้นใหญ่ (LAB-07) ใช้ localStorage
- เหตุผล: ไม่ต้องตั้ง Backend Server ให้ซับซ้อน
- ผู้เรียนโฟกัสที่ Frontend และ Docker

---

## สัญญาอนุญาต (License)

หลักสูตรนี้ใช้ **Dual License**:

| เนื้อหา | สัญญาอนุญาต |
|---|---|
| เอกสาร, LAB guides, slide.md | CC BY-NC-SA 4.0 — ใช้สอนได้ฟรี ห้ามขาย |
| ตัวอย่างโค้ด HTML/CSS/JS/Dockerfile | MIT License — ใช้ได้เสรี |

ข้อสงวนสิทธิ์: เนื้อหาเป็นแนวทางเบื้องต้นเท่านั้น ไม่ใช่เอกสารอ้างอิงขั้นสูง

---

## Credits

| เครื่องมือ | ผู้พัฒนา | License |
|---|---|---|
| VS Code | Microsoft | MIT |
| Cline | saoudrizwan | Apache 2.0 |
| Ollama | Ollama Inc. | MIT |
| Docker Desktop | Docker Inc. | Docker Subscription SA |
| GitHub Desktop | GitHub / Microsoft | MIT |
| Qwen2.5-Coder:7b | Alibaba Cloud | Qwen License |

---

## การเปลี่ยนแปลงล่าสุด

### 2026-06-07 — อัปเดต License, Credits, README และ slide.md
- **อัปเดต** `LICENSE` — เปลี่ยนเป็น Dual License (CC BY-NC-SA 4.0 + MIT) พร้อม disclaimer ภาษาไทย
- **อัปเดต** `README.md` — ปรับหน้าตาให้เป็น landing page สวยงาม มี badges, emoji, หลักการ 3 ข้อ, Credits
- **อัปเดต** `slide.md` — ขยายจาก 16 เป็น 80 สไลด์ แทรกหลักการแต่ละ LAB ครบ
- **เพิ่ม** ส่วน Credits ใน README.md ให้เครดิตเครื่องมือทุกตัว

### 2026-06-07 — สร้าง LAB ทั้งหมด 8 ชุด
- **เพิ่ม** `LAB-01-SETUP/README.md` — คู่มือติดตั้งทีละขั้นตอน รวม WSL2, Docker, Ollama pull
- **เพิ่ม** `LAB-02-FIRST-CHAT/README.md` — ทดสอบ Cline 3 ระดับ (ทักทาย, ถามเรื่องโค้ด, ขอสร้างโค้ด)
- **เพิ่ม** `LAB-03-PROMPT-ENGINEERING/README.md` — โครงสร้าง Prompt + แบบฝึกหัด 3 ข้อ + เทคนิค Iterate
- **เพิ่ม** `LAB-04-FIRST-HTML/README.md` — สร้างเว็บแนะนำตัว Loop 3 รอบ
- **เพิ่ม** `LAB-05-GIT-DESKTOP/README.md` — GitHub Desktop: สร้าง Repo, Commit, History (ไม่มี CLI เลย)
- **เพิ่ม** `LAB-06-DOCKER/README.md` — แนวคิด + Dockerfile + Build + Run + Docker Desktop UI
- **เพิ่ม** `LAB-07-FEEDBACK-APP/README.md` — Workshop เต็มรูปแบบ สร้างจาก Prompt วางแผน → HTML → CSS → JS → Docker → Commit
- **เพิ่ม** `LAB-08-DEBUG-ROLLBACK/README.md` — ฝึก Debug + ฝึก Revert Commit ด้วย GitHub Desktop
- **อัปเดต** `README.md` — รวม Agenda เข้ามา ปรับให้เป็นคู่มือหลัก

---

## Tips สำหรับวิทยากร

- **LAB-01** เผื่อเวลาจริงๆ บางเครื่องติดตั้ง Docker ยากเพราะ WSL2
- **LAB-03** เน้นกฎ "ห้ามพิมพ์โค้ดเอง" ตั้งแต่ต้น
- **LAB-07** ใช้หลัก 70:20:10 — ลงมือจริง 70%, วิทยากร Coach 20%
- **ทุก LAB** มี Checkpoint — ตรวจให้ครบก่อนไป LAB ถัดไป
- **Error** อย่าเฉลยทันที ใช้คำถามแบบกรวย "ลองอ่านบรรทัดสีแดงดู AI แจ้งว่าอะไร?"
