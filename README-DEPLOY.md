# Numerics Advisory — Deploy Package

โฟลเดอร์นี้คือเว็บไซต์เวอร์ชั่นพร้อม deploy ขึ้น production

## 🚀 วิธี Deploy ขึ้น Netlify (เร็วสุด ฟรี)

### ครั้งแรก
1. ZIP โฟลเดอร์ `deploy/` ทั้งหมด
2. ไปที่ **https://app.netlify.com/drop**
3. ลาก zip ลงในกรอบ → รอ 30 วินาที → ได้ URL เช่น `random-name.netlify.app`
4. กด **Claim site** → สมัคร account ฟรี
5. ไปที่ **Site settings → Domain management → Add custom domain**
6. ใส่ `numericsadvisory.com` → Netlify จะบอกค่า DNS ที่ต้องตั้ง
7. เข้าไปที่ผู้ให้บริการ domain (ที่ซื้อ numericsadvisory.com มา) → แก้ DNS ตามที่บอก
8. รอ 5 นาที – 1 ชั่วโมง → SSL ฟรีติดอัตโนมัติ

### อัพเดทครั้งต่อๆ ไป
- ทุกครั้งที่เพิ่มบทความใหม่หรือแก้เนื้อหา → ZIP โฟลเดอร์ใหม่ → ลากทับขึ้น Netlify site เดิม → live ใน 10 วินาที
- หรือใช้ Netlify CLI / GitHub auto-deploy เพื่อลด step

## 📁 โครงสร้างไฟล์

```
index.html               ← หน้าแรก
articles/
  index.html             ← รายการบทความ
  *.html                 ← บทความแต่ละชิ้น
  article.css            ← stylesheet สำหรับบทความ
services/
  *.html                 ← หน้าบริการแต่ละอัน
  service.css            ← stylesheet สำหรับ services
assets/
  numerics-logo.png      ← โลโก้ (ใช้เป็น favicon + og:image ด้วย)
  ...
brochure/
  numerics-service-brochure.html ← service brochure (มีปุ่ม print)
robots.txt               ← บอก search engine ว่าให้ index ได้
sitemap.xml              ← แผนผังเว็บ สำหรับ Google
```

## ⚠️ สิ่งที่ยังต้องทำ (อยู่นอก scope การ deploy)

1. **CTA "นัด Health Check ฟรี" บน index.html** ตอนนี้ link เป็น `#` — ต้องเปลี่ยนเป็นลิงก์ booking จริง (Calendly / LINE / form)
2. **Footer links** "ร่วมงานกับเรา", "LINE: @numerics", "นัดประชุมออนไลน์" ยังเป็น `#`
3. **อีเมลใน footer** แสดงเป็น `.co.th` แต่ link เป็น `.com` — อันไหนถูก?
4. **เนื้อหา EN** — ยังไม่ได้ทำ (ถูกซ่อน toggle ไปแล้ว)
5. **Google Analytics** — ยังไม่ได้ใส่

## 🔄 การเพิ่มบทความใหม่
ให้บอกใน chat:
> "เพิ่มบทความเรื่อง [หัวข้อ] ใน articles/"

ระบบจะ:
1. สร้างไฟล์ `articles/[slug].html` ตาม template ที่มีอยู่
2. เพิ่ม card บน `articles/index.html`
3. เพิ่ม card บน hero `index.html` (ถ้าอยากให้ขึ้นหน้าแรก)
4. เพิ่ม URL ใน `sitemap.xml`
