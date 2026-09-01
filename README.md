# Wastewater Treatment Advisor

เครื่องมือประเมินระบบบำบัดน้ำเสียเบื้องต้น — แนะนำ treatment train, ขนาดถัง, งบประมาณ (CAPEX/OPEX/NPV) จากข้อมูลน้ำเสียที่กรอกเข้าไป

เป็น static HTML/CSS/JS ล้วน ไม่มี build step ไม่มี backend ไม่มี dependency ภายนอกที่ต้อง install — เปิดไฟล์ `index.html` ในเบราว์เซอร์ก็ใช้งานได้ทันที หรือ deploy ขึ้น hosting อะไรก็ได้ที่รองรับ static site

## Deploy ขึ้น Vercel (ผ่าน GitHub)

### 1. สร้าง repo บน GitHub
```bash
cd wastewater-advisor-app
git init
git add .
git commit -m "Initial commit: wastewater treatment advisor"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```
(สร้าง repo เปล่าบน github.com ก่อน แล้วแทนที่ `<your-username>/<repo-name>` ด้วยของจริง)

### 2. Import เข้า Vercel
1. เข้า https://vercel.com → "Add New" → "Project"
2. เลือก "Import Git Repository" แล้วเลือก repo ที่เพิ่ง push
3. Framework Preset: เลือก **"Other"** (เพราะเป็น static HTML ไม่ใช่ Next.js/React)
4. Build Command: เว้นว่างไว้ (ไม่มี build step)
5. Output Directory: เว้นว่างไว้ หรือใส่ `.` (root)
6. กด Deploy

Vercel จะเสิร์ฟ `index.html` เป็นหน้าแรกอัตโนมัติ ได้ URL ทันที เช่น `your-project.vercel.app`

### ทางลัด: Deploy โดยไม่ผ่าน GitHub (Vercel CLI)
ถ้าอยากลองก่อนโดยไม่สร้าง repo:
```bash
npm i -g vercel
cd wastewater-advisor-app
vercel
```
ตอบคำถามตาม prompt (framework = Other) ก็จะได้ URL preview ทันที

## หมายเหตุ
- ไฟล์นี้เก็บสถานะทั้งหมดไว้ใน browser memory ระหว่าง session เดียว ไม่มีการบันทึกข้อมูลถาวร (ไม่ใช้ localStorage) — ถ้าปิดหน้าเว็บแล้วข้อมูลที่กรอกจะหายไป ต้องกรอกใหม่ทุกครั้ง
- ราคา/สมมติฐานทางวิศวกรรมทั้งหมดเป็นค่าประมาณ ดูรายละเอียดสูตรได้ในเอกสาร `budget_formulas_reference.md` แยกต่างหาก (ถ้าต้องการรวมเข้า repo ให้ก็อปปี้เข้ามาด้วย)
