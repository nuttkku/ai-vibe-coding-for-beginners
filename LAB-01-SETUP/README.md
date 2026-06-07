# LAB-01 | ติดตั้งเครื่องมือทั้งหมด

**Session:** 1.2 | **เวลา:** 09:45 - 11:30 น. | **ระยะเวลา:** ~1 ชั่วโมง 45 นาที

> ผลลัพธ์: ผู้เรียนมีเครื่องมือครบทุกตัวและพร้อมเริ่ม Vibe Coding

---

## ภาพรวมสิ่งที่จะติดตั้ง

```
1. VS Code          → โปรแกรมเขียนโค้ด (เหมือน Word แต่สำหรับโค้ด)
2. GitHub Desktop   → บันทึกประวัติงานด้วยคลิก (ไม่ต้องพิมพ์คำสั่ง)
3. Docker Desktop   → กล่องสำหรับรันโปรแกรม
4. Ollama           → ตัวรัน AI บนเครื่องเรา
5. Cline            → AI Assistant ที่อยู่ใน VS Code
```

---

## ขั้นตอนที่ 1: ติดตั้ง VS Code

VS Code คือโปรแกรมที่เราจะใช้เขียน/ดูโค้ด และเปิด AI ผ่าน Cline

**1.1 ดาวน์โหลด VS Code**
1. เปิด Browser แล้วไปที่: `code.visualstudio.com`
2. คลิกปุ่มสีน้ำเงิน **"Download for Windows"**
3. รอให้ไฟล์ `.exe` ดาวน์โหลดเสร็จ

**1.2 ติดตั้ง VS Code**
1. ดับเบิลคลิกไฟล์ที่ดาวน์โหลดมา (ชื่อประมาณ `VSCodeSetup-x64-xxx.exe`)
2. คลิก **"I accept the agreement"** แล้วคลิก **Next**
3. ติ๊กถูกที่ **"Add to PATH"** (สำคัญมาก!) และ **"Create a desktop icon"**
4. คลิก **Install** แล้วรอ
5. คลิก **Finish** — VS Code จะเปิดขึ้นมาอัตโนมัติ

**✅ ตรวจสอบ:** VS Code เปิดได้และเห็นหน้าจอสีเข้ม

---

## ขั้นตอนที่ 2: ติดตั้ง GitHub Desktop

GitHub Desktop ช่วยให้เราบันทึกประวัติการแก้ไขโค้ดโดยไม่ต้องพิมพ์คำสั่งเลย

**2.1 ดาวน์โหลด GitHub Desktop**
1. ไปที่: `desktop.github.com`
2. คลิก **"Download for Windows"**
3. รอให้ไฟล์ดาวน์โหลดเสร็จ

**2.2 ติดตั้ง GitHub Desktop**
1. ดับเบิลคลิกไฟล์ที่ดาวน์โหลดมา (ชื่อประมาณ `GitHubDesktopSetup-x64.exe`)
2. โปรแกรมจะติดตั้งและเปิดขึ้นมาอัตโนมัติ (ไม่ต้องตั้งค่าอะไร)
3. เมื่อเปิดขึ้นมา จะถามให้ Sign in — คลิก **"Skip this step"** (ไม่จำเป็นต้องมี account GitHub)

> **หมายเหตุ:** ถ้าต้องการใช้ GitHub ในอนาคตค่อยสมัคร แต่ตอนนี้ข้ามได้เลย

**✅ ตรวจสอบ:** GitHub Desktop เปิดได้ เห็นหน้าจอต้อนรับ

---

## ขั้นตอนที่ 3: ติดตั้ง Docker Desktop

Docker เป็นเหมือน "กล่อง" ที่เอาไว้รันโปรแกรมของเราอย่างสะอาด

> **ก่อนติดตั้ง:** Docker Desktop ต้องการ WSL2 (Windows Subsystem for Linux) ซึ่ง Windows 11 มักมีอยู่แล้ว

**3.1 เปิดใช้งาน WSL2 (ถ้ายังไม่มี)**
1. กดปุ่ม Windows แล้วค้นหา **"PowerShell"**
2. คลิกขวาที่ PowerShell แล้วเลือก **"Run as administrator"**
3. พิมพ์คำสั่งนี้แล้วกด Enter:
   ```
   wsl --install
   ```
4. รอให้เสร็จ แล้ว **Restart เครื่อง**

**3.2 ดาวน์โหลด Docker Desktop**
1. ไปที่: `docker.com/products/docker-desktop`
2. คลิก **"Download for Windows"**
3. รอให้ไฟล์ดาวน์โหลดเสร็จ

**3.3 ติดตั้ง Docker Desktop**
1. ดับเบิลคลิกไฟล์ที่ดาวน์โหลดมา (ชื่อประมาณ `Docker Desktop Installer.exe`)
2. คลิก **OK** ที่ dialog ที่ขึ้นมา
3. รอการติดตั้ง (อาจใช้เวลา 3-5 นาที)
4. เมื่อเสร็จ คลิก **Close and restart** หรือ **Close**
5. เปิด Docker Desktop จาก Desktop หรือ Start Menu

**3.4 ยืนยันการติดตั้ง**
1. เปิด Docker Desktop
2. รอให้ไอคอนปลาวาฬ (🐳) ที่ taskbar เปลี่ยนเป็นสีเขียว
3. ถ้าเห็นข้อความ "Docker Desktop is running" = สำเร็จ!

**✅ ตรวจสอบ:** Docker Desktop รันอยู่ ไอคอนสีเขียวที่ taskbar

---

## ขั้นตอนที่ 4: ติดตั้ง Ollama

Ollama คือตัวรัน AI Model บนเครื่องเรา (ใช้งานออฟไลน์ได้!)

**4.1 ดาวน์โหลด Ollama**
1. ไปที่: `ollama.com`
2. คลิกปุ่ม **"Download"**
3. เลือก **Windows** แล้วคลิกดาวน์โหลด

**4.2 ติดตั้ง Ollama**
1. ดับเบิลคลิกไฟล์ที่ดาวน์โหลดมา (ชื่อ `OllamaSetup.exe`)
2. คลิก **Install**
3. รอการติดตั้ง

**4.3 ดาวน์โหลด AI Model: Qwen2.5-Coder:7b**

> นี่คือตัว AI ที่จะช่วยเราเขียนโค้ด ขนาดประมาณ 4-5 GB

1. กดปุ่ม Windows แล้วค้นหา **"PowerShell"** (หรือ Command Prompt)
2. คลิกเปิด PowerShell
3. พิมพ์คำสั่งนี้แล้วกด Enter:
   ```
   ollama pull qwen2.5-coder:7b
   ```
4. รอให้ดาวน์โหลดเสร็จ (อาจใช้เวลา 5-15 นาทีขึ้นอยู่กับความเร็ว internet)
5. เมื่อเสร็จจะเห็นข้อความ `success`

**4.4 ทดสอบ Ollama**
1. ใน PowerShell เดิม พิมพ์:
   ```
   ollama list
   ```
2. จะเห็น `qwen2.5-coder:7b` อยู่ในรายการ

**✅ ตรวจสอบ:** พิมพ์ `ollama list` แล้วเห็น qwen2.5-coder:7b

---

## ขั้นตอนที่ 5: ติดตั้ง Cline Extension ใน VS Code

Cline คือ AI Assistant ที่อาศัยอยู่ใน VS Code — เป็นตัวหลักที่เราจะใช้สั่งงาน AI

**5.1 เปิด VS Code**
1. เปิด VS Code (ถ้ายังไม่ได้เปิด)

**5.2 ติดตั้ง Cline**
1. คลิกไอคอนรูปสี่เหลี่ยม 4 ชิ้น (Extensions) ที่แถบซ้ายมือ
   - หรือกด `Ctrl + Shift + X`
2. ในช่องค้นหา พิมพ์: `Cline`
3. เลือก Extension ชื่อ **"Cline"** (ของ saoudrizwan)
4. คลิก **Install**
5. รอให้ติดตั้งเสร็จ

**5.3 ตั้งค่า Cline ให้ใช้ Ollama**
1. คลิกไอคอน Cline ที่แถบซ้าย (รูปหุ่นยนต์หรือตัว C)
2. Cline จะเปิดขึ้นด้านขวา
3. คลิกไอคอนฟันเฟือง (⚙️) หรือปุ่ม Settings ของ Cline
4. ตั้งค่าดังนี้:
   - **API Provider:** เลือก `Ollama`
   - **Base URL:** `http://localhost:11434`
   - **Model:** เลือก `qwen2.5-coder:7b` (หรือพิมพ์เอง)
5. คลิก **Save** หรือ **Done**

**✅ ตรวจสอบ:** Cline แสดงข้อความว่าเชื่อมต่อสำเร็จ หรือไม่มี Error แดง

---

## Checklist สรุป

ก่อนไปต่อ LAB-02 ตรวจสอบให้ครบทุกข้อ:

- [ ] VS Code เปิดได้
- [ ] GitHub Desktop เปิดได้
- [ ] Docker Desktop ไอคอนสีเขียวที่ taskbar
- [ ] พิมพ์ `ollama list` แล้วเห็น `qwen2.5-coder:7b`
- [ ] Cline ติดตั้งใน VS Code และตั้งค่าใช้ Ollama แล้ว

---

## แก้ปัญหาที่พบบ่อย

| ปัญหา | วิธีแก้ |
|---|---|
| Docker ไม่ยอมเริ่ม | ตรวจสอบว่า WSL2 ติดตั้งแล้ว ลอง Restart เครื่อง |
| Ollama pull ช้ามาก | ปกติครับ ไฟล์ใหญ่ รอต่อไป |
| Cline หาโมเดลไม่เจอ | ตรวจสอบว่า Ollama กำลังรันอยู่ (ดูที่ taskbar) |
| VS Code ไม่เห็น Cline | ลอง Restart VS Code |

---

> ➡️ **ถัดไป:** [LAB-02 - คุยกับ AI ครั้งแรก](../LAB-02-FIRST-CHAT/)
