# Stick Story ยอดติดตามสด (เวอร์ชัน GitHub Pages)

หน้าเว็บโชว์ยอดผู้ติดตาม YouTube และ Instagram พร้อมตัวละครประจำช่องที่ออกท่าเวลายอดขยับ
ฝากเว็บไว้บน GitHub Pages ได้ฟรี ลิงก์เว็บ: **https://stickstory.github.io/** (ต้องใช้บัญชี GitHub ชื่อ `stickstory` และ repo ชื่อ `stickstory.github.io`)

- **YouTube** ดึงยอดเองอัตโนมัติทุก 1 นาที
- **Instagram** คุณใส่ตัวเลขเองที่หน้า `admin.html`

```
stickstory-live/
├─ index.html    หน้าสำหรับแฟน ๆ
├─ admin.html    หน้าแก้ยอด IG (สำหรับคุณคนเดียว)
├─ config.js     ตั้งค่า YouTube key / ช่อง
├─ data.json     ยอด IG (หน้า admin จะแก้ไฟล์นี้ให้)
├─ img/          ท่าตัวละคร
└─ fonts/        ฟอนต์ FC Home
```

---

## ขั้นที่ 1 — สร้างที่เก็บเว็บบน GitHub

1. สมัคร GitHub ฟรีที่ https://github.com/signup
2. กดปุ่ม **+** มุมขวาบน → **New repository**
3. ช่อง Repository name ใส่ `stickstory.github.io` (ตรงตัวทุกตัวอักษร) และเลือก **Public** แล้วกด **Create repository**
4. ในหน้าถัดไป กดลิงก์ **uploading an existing file**
5. แตกไฟล์ zip แล้วเปิดโฟลเดอร์ `stickstory-live` **เลือกทุกอย่างข้างใน** (รวมโฟลเดอร์ img กับ fonts) แล้วลากไปวางในหน้า GitHub
6. รอให้อัปโหลดเสร็จ แล้วกด **Commit changes**

## ขั้นที่ 2 — เปิดเว็บ

1. ใน repo ไปที่ **Settings** → เมนูซ้าย **Pages**
2. ตรง Source เลือก **Deploy from a branch** → Branch เลือก **main** และโฟลเดอร์ **/ (root)** → กด **Save**
3. รอประมาณ 1–2 นาที แล้วรีเฟรชหน้านั้น จะมีลิงก์เว็บขึ้นมา คือ `https://stickstory.github.io/`

## ขั้นที่ 3 — ล็อก YouTube key ให้ใช้ได้เฉพาะเว็บนี้ (สำคัญ)

key อยู่ในไฟล์ `config.js` ซึ่งใครเปิดดูก็เห็นได้ จึงต้องล็อกไว้ให้ใช้ได้แค่บนเว็บของคุณ

1. เข้า https://console.cloud.google.com → **APIs & Services → Credentials** → กดชื่อ key
2. ตรง **Application restrictions** เลือก **Websites**
3. กด **Add** แล้วใส่ `https://stickstory.github.io/*`
4. ตรง **API restrictions** เลือก **Restrict key** → ติ๊ก **YouTube Data API v3**
5. กด **Save** แล้วรอประมาณ 5 นาทีให้ระบบมีผล

## ขั้นที่ 4 — สร้างกุญแจสำหรับหน้าแก้ยอด IG

หน้า `admin.html` ต้องใช้ GitHub token ไว้บันทึกตัวเลขลงไฟล์ `data.json`

1. เข้า https://github.com/settings/personal-access-tokens/new
2. **Token name:** `stickstory-ig` · **Expiration:** เลือกนานสุดเท่าที่มีให้เลือก
3. **Repository access:** เลือก **Only select repositories** → เลือก `stickstory.github.io`
4. **Permissions** → **Repository permissions** → **Contents** → เลือก **Read and write**
5. กด **Generate token** แล้วคัดลอก token ที่ขึ้นต้นด้วย `github_pat_…`
   (token นี้แก้ไขได้แค่ repo นี้ repo เดียว ห้ามส่งให้คนอื่น)

## วิธีแก้ยอด IG

1. เปิด `https://stickstory.github.io/admin.html` (ใช้ได้ทั้งในมือถือและคอม)
2. ครั้งแรกให้วาง GitHub token แล้วกด **เข้าสู่ระบบ** (ถ้าติ๊ก "จำไว้ในเครื่องนี้" ไว้ ครั้งหลังไม่ต้องใส่อีก)
3. พิมพ์ยอด หรือกด +1 / +5 / +10 แล้วกด **บันทึก**
4. ภายในประมาณ 1–2 นาที หน้าแฟน ๆ จะเห็นยอดใหม่ และตัวละครจะออกท่าดีใจ

ถ้าไม่สะดวกใช้หน้า admin ก็แก้ตรง ๆ บน github.com ได้ เปิดไฟล์ `data.json` → กดรูปดินสอ → แก้ตัวเลข → **Commit changes**

---

## ลูกเล่นของหน้าเว็บ

| เหตุการณ์ | ตัวละครทำอะไร |
|---|---|
| ยอดเพิ่ม | กระโดดตกใจ แล้วชูมือเชียร์ มีพลุกระดาษกับ `+1` |
| ยอดถึงเลขกลม (100, 200, 500, 1,000 …) | ยืนท่าฮีโร่ ขึ้นตราประทับ "ครบ 100!" |
| ยอดลด | ทำหน้างง |
| ยอดไม่ขยับ 2 นาที / 5 นาที | ยืนคิด / นั่งหลับ Z z z |
| แฟนจิ้มที่ตัวละคร | ทำท่าสุ่ม จิ้มรัว ๆ 6 ครั้งจะหัวหมุน |

- ต่อท้ายลิงก์ด้วย `?demo=1` เพื่อดูตัวละครเล่นกับตัวเลขจำลอง
- ต่อท้ายลิงก์ด้วย `?obs=1` จะได้พื้นหลังโปร่งใส เอาไปใช้ใน OBS ตอนไลฟ์ได้

## ค่าใช้จ่ายและข้อจำกัด

- **ฟรีทั้งหมด** ทั้ง GitHub Pages และ YouTube API ไม่ต้องผูกบัตร
- คนดู 1 คนที่เปิดหน้าเว็บค้างไว้จะใช้โควตา YouTube 1 หน่วยต่อนาที (ถ้าสลับไปแท็บอื่น หน้าเว็บจะหยุดดึงยอด)
  โควตาฟรีมีวันละ 10,000 หน่วย พอสำหรับคนเปิดดูรวมกันประมาณ 160 ชั่วโมงต่อวัน
  ถ้าเกินโควตา ยอด YouTube จะหยุดขยับจนโควตารีเซ็ต (ประมาณบ่ายสองถึงบ่ายสามโมงตามเวลาไทย) และไม่มีการเก็บเงิน
- ถ้าคนดูเยอะขึ้นมาก แก้ `YT_EVERY_SECONDS` ใน `config.js` เป็น 120 หรือ 300 เพื่อประหยัดโควตา
- อยากได้ชื่อ .com ซื้อโดเมนแล้วผูกได้ที่ Settings → Pages → **Custom domain**
