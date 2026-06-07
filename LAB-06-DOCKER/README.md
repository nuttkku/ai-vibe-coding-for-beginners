# LAB-06 | รู้จัก Docker และสร้าง Dockerfile ด้วย AI

**Session:** 2.2 | **เวลา:** 09:30 - 10:30 น. | **ระยะเวลา:** ~1 ชั่วโมง

> ผลลัพธ์: ผู้เรียนเข้าใจแนวคิด Docker และรันหน้าเว็บจากเมื่อวานผ่าน Docker ได้

---

## Docker คืออะไร? (อธิบายง่ายๆ)

### อุปมาที่ 1: กล่องบรรจุอาหาร

ลองนึกถึงอาหารกล่อง:
- **ปัญหาเดิม:** "ทำอาหารที่บ้านได้ แต่พอไปอุ่นที่โรงเรียนแล้วรสชาติเปลี่ยน"
- **Docker แก้ปัญหา:** บรรจุทั้งอาหาร + ภาชนะ + สภาพแวดล้อม ไว้ในกล่องเดียว เปิดที่ไหนก็ได้รสชาติเดิม

### อุปมาที่ 2: การแสดงละคร

- **โปรแกรมเรา** = บทละคร (Script)
- **Docker Container** = เวทีพร้อมฉาก นักแสดง อุปกรณ์ครบ
- เอา Container ไปวางที่ไหน ก็แสดงได้เหมือนกันทุกที่

### ปัญหาที่ Docker แก้ได้

> **"รันบนเครื่องฉันได้ แต่พอส่งให้เพื่อนแล้วพัง!"**

Docker ทำให้โปรแกรมรันได้เหมือนกันทุกเครื่อง ไม่ว่าจะเป็น Windows, Mac, หรือ Linux

---

## คำศัพท์สำคัญ

| คำ | ความหมาย |
|---|---|
| **Image** | สูตรหรือ Template ของ Container (เหมือนสูตรอาหาร) |
| **Container** | โปรแกรมที่กำลังรันอยู่จาก Image (เหมือนอาหารที่ทำแล้ว) |
| **Dockerfile** | ไฟล์คำสั่งสำหรับสร้าง Image |
| **Build** | กระบวนการสร้าง Image จาก Dockerfile |
| **Run** | เริ่มต้น Container จาก Image |

---

## ส่วนที่ 1: ตรวจสอบ Docker Desktop

1. เปิด Docker Desktop
2. ดูที่ taskbar มุมล่างขวา — ควรเห็นไอคอนปลาวาฬสีเขียว
3. เปิด Docker Desktop แล้วตรวจสอบว่าสถานะเป็น **"Docker Desktop is running"**

---

## ส่วนที่ 2: ให้ AI สร้าง Dockerfile สำหรับหน้าเว็บของเรา

**2.1 เปิดโฟลเดอร์ my-first-webpage ใน VS Code**

(ถ้ายังไม่ได้เปิด: File → Open Folder → เลือก my-first-webpage)

**2.2 เปิด Cline แล้วส่ง Prompt นี้:**

```
ฉันมีไฟล์ index.html อยู่ในโฟลเดอร์นี้ ต้องการรันมันด้วย Docker
ช่วยสร้างไฟล์ Dockerfile ที่ใช้ nginx ในการ serve ไฟล์ HTML นี้
และสร้างไฟล์ .dockerignore ด้วย
อธิบายสั้นๆ ว่าแต่ละบรรทัดทำอะไรด้วยนะ
```

**2.3 อนุมัติการสร้างไฟล์**
- คลิก **Approve** เมื่อ Cline ขอสร้างไฟล์ `Dockerfile`
- คลิก **Approve** เมื่อ Cline ขอสร้างไฟล์ `.dockerignore`

**ผลที่ควรได้:** ไฟล์ `Dockerfile` คล้ายกับนี้:

```dockerfile
# ใช้ nginx เป็น web server (เบา เร็ว เหมาะสำหรับ static files)
FROM nginx:alpine

# คัดลอกไฟล์ทั้งหมดไปไว้ใน container
COPY . /usr/share/nginx/html

# เปิด port 80 (port มาตรฐานของ web)
EXPOSE 80
```

---

## ส่วนที่ 3: Build Docker Image

**3.1 เปิด Terminal ใน VS Code**
1. คลิก **Terminal** → **New Terminal** (หรือกด `` Ctrl + ` ``)
2. Terminal จะเปิดขึ้นด้านล่าง และอยู่ในโฟลเดอร์ `my-first-webpage`

**3.2 สร้าง (Build) Image**

พิมพ์คำสั่งนี้แล้วกด Enter:
```
docker build -t my-first-webpage .
```

อธิบายคำสั่ง:
- `docker build` = สั่งให้ Docker สร้าง Image
- `-t my-first-webpage` = ตั้งชื่อ Image ว่า my-first-webpage
- `.` = ใช้ Dockerfile ในโฟลเดอร์ปัจจุบัน

**รอดูผล:** Docker จะดาวน์โหลด nginx และสร้าง Image (ครั้งแรกอาจใช้เวลา 1-2 นาที)

เมื่อเสร็จจะเห็น:
```
Successfully built xxxxxxxx
Successfully tagged my-first-webpage:latest
```

---

## ส่วนที่ 4: Run Container

**4.1 รัน Container**

พิมพ์คำสั่ง:
```
docker run -d -p 8080:80 --name webpage my-first-webpage
```

อธิบายคำสั่ง:
- `docker run` = สั่งให้ Docker รัน Container
- `-d` = รันในพื้นหลัง (ไม่ต้องเปิด terminal ค้างไว้)
- `-p 8080:80` = เปิด port 8080 บนเครื่องเรา เชื่อมกับ port 80 ใน Container
- `--name webpage` = ตั้งชื่อ Container ว่า webpage

**4.2 เปิดดูในเบราว์เซอร์**
1. เปิด Browser
2. ไปที่: `http://localhost:8080`
3. จะเห็นหน้าเว็บแนะนำตัวของเรา!

---

## ส่วนที่ 5: จัดการ Container ใน Docker Desktop

**5.1 ดู Container ที่รันอยู่**
1. เปิด Docker Desktop
2. คลิกที่ **"Containers"** ในแถบซ้าย
3. จะเห็น Container ชื่อ `webpage` กำลังรันอยู่ (สีเขียว)

**5.2 หยุด และลบ Container**

เมื่อต้องการหยุด:
1. ใน Docker Desktop คลิกปุ่ม Stop (■) ข้างๆ Container
2. หรือพิมพ์ใน Terminal: `docker stop webpage`

เมื่อต้องการลบ:
```
docker rm webpage
```

> **หมายเหตุ:** การลบ Container ไม่ได้ลบ Image — ถ้าอยากรันอีกครั้ง แค่ `docker run` ใหม่ได้เลย

---

## ส่วนที่ 6: Commit ไฟล์ Dockerfile ด้วย Git Desktop

1. เปิด GitHub Desktop
2. จะเห็นไฟล์ใหม่ `Dockerfile` และ `.dockerignore` ใน Changes
3. เขียน Commit Message:
   ```
   เพิ่ม Dockerfile สำหรับรันด้วย Docker
   ```
4. คลิก **"Commit to main"**

---

## Checkpoint ✅

- [ ] Build Docker Image สำเร็จ (`docker build` ไม่มี Error)
- [ ] รัน Container สำเร็จ (`docker run`)
- [ ] เปิด `http://localhost:8080` แล้วเห็นหน้าเว็บของตัวเอง
- [ ] Commit Dockerfile ด้วย GitHub Desktop แล้ว

---

## สรุปคำสั่ง Docker ที่ใช้บ่อย

| คำสั่ง | ทำอะไร |
|---|---|
| `docker build -t ชื่อ .` | สร้าง Image จาก Dockerfile |
| `docker run -d -p 8080:80 ชื่อ` | รัน Container เปิด port 8080 |
| `docker stop ชื่อ-container` | หยุด Container |
| `docker rm ชื่อ-container` | ลบ Container |
| `docker images` | ดูรายการ Image ทั้งหมด |
| `docker ps` | ดู Container ที่รันอยู่ |

---

> ➡️ **ถัดไป:** [LAB-07 - Workshop สร้างเว็บรับความคิดเห็น](../LAB-07-FEEDBACK-APP/)
