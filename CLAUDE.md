# CLAUDE.md — เว็บบอร์ดครอบครัว "พ่อแสนย์ แม่โอ๋ เจน่า โนอาห์"

## 📋 สรุปโปรเจค

เว็บบอร์ดครอบครัวส่วนตัว (Family Bulletin Board) สำหรับครอบครัว "แสนย์โอ๋" ออกแบบในสไตล์ **Scholar's Scrapbook** — สมุดเก่าๆ ธีม Nostalgic School ที่ดูอบอุ่น อิงงาน Tactile Skeuomorphism (กระดานดำ, กระดาษสมุด, โพลารอยด์, กลัดหมุด, เทปกาว)

**URL ที่ Deploy:** `https://chatvidme.web.app` (Firebase Hosting)

---

## 🏗️ สถาปัตยกรรมโปรเจค

### ไฟล์สำคัญ

| ไฟล์ | คำอธิบาย |
|------|----------|
| `index.html` | **ไฟล์หลักเดียว** (~2,143 บรรทัด) — HTML + CSS + JS ทั้งหมดอยู่ในไฟล์เดียว (Single-file SPA) |
| `firebase.json` | การตั้งค่า Firebase Hosting + Firestore rules |
| `firestore.rules` | กฎ Firestore (ปัจจุบัน: allow read, write: if true — เปิดสาธารณะ) |
| `.firebaserc` | ชี้ไปที่โปรเจค Firebase `chatvidme` |
| `stitch_high_school_alumni_forum/` | ไดเรกทอรี reference design จาก Stitch (DESIGN.md + code.html + screenshot) — ไม่ได้ใช้ใน production |

### โครงสร้างหลัก

```
old school-new/
├── index.html              ← ไฟล์หลัก (HTML+CSS+JS all-in-one)
├── firebase.json           ← Firebase Hosting config
├── firestore.rules         ← Firestore security rules
├── .firebaserc             ← Firebase project: chatvidme
├── .firebase/              ← Firebase cache
└── stitch_high_school_alumni_forum/   ← Reference designs (ไม่ใช้ใน production)
    ├── DESIGN.md           ← Design system spec จาก Stitch
    ├── code.html           ← Stitch generated code (Tailwind version)
    └── screen.png          ← Screenshot จาก Stitch
```

---

## 🔧 เทคโนโลยีที่ใช้

### Frontend
- **Pure HTML/CSS/JS** — ไม่มี framework, ไม่มี build step
- **Single-page Application** ด้วย tab switching (ไม่ใช่ client-side routing)
- **CSS ทั้งหมดอยู่ใน `<style>` tag** ใน `index.html`
- **JavaScript ทั้งหมดอยู่ใน `<script>` tag** ท้ายไฟล์

### Fonts (Google Fonts)
- `Bricolage Grotesque` — Headlines/Brand
- `Work Sans` — Body text
- `Courier Prime` — Labels/Metadata (typewriter look)
- `Material Symbols Outlined` — Icons

### Backend / Database
- **Firebase (compat SDK v10.12.0)** ผ่าน CDN script tags
  - `firebase-app-compat.js`
  - `firebase-analytics-compat.js`
  - `firebase-firestore-compat.js`
  - `firebase-storage-compat.js`
- **Firestore** เก็บข้อมูลแบบ realtime sync
- **Firebase Hosting** สำหรับ deploy

### Firebase Config
```javascript
const firebaseConfig = {
  apiKey: "AIzaSyA7aX3ryqOeU2gM6mGAmksZ5Ca7pP9FlHc",
  authDomain: "chatvidme.firebaseapp.com",
  projectId: "chatvidme",
  storageBucket: "chatvidme.firebasestorage.app",
  messagingSenderId: "362977682885",
  appId: "1:362977682885:web:31a8ed6f74f145e58817ac",
  measurementId: "G-6WHTF49W65"
};
```

---

## 🎨 Design System — "Scholar's Scrapbook"

### คอนเซปต์หลัก
- **Tactile Skeuomorphism** — UI เลียนแบบวัตถุจริง (กระดานดำ, กระดาษสมุด, โพลารอยด์, เทปกาว, หมุดกลัด)
- **Scrapbook Aesthetic** — ความอบอุ่นแบบสมุดรุ่น/อัลบัมครอบครัว
- **สีหลัก:** Chalkboard Green (#152c24), Aged Paper (#fff9ed), Red Pen (#ac3231), Blue Ink (#002948), Desk Oak (#c4aa8f)
- **เอฟเฟกต์เด่น:**
  - Paper stacks (multi-border shadow)
  - Notebook ruled lines (CSS background-image)
  - Polaroid photo frames (white border + rotation)
  - Tape strips (semi-transparent + backdrop-filter)
  - Push pins on cards
  - Chalkboard texture (SVG noise filter + inset shadow)
  - Wood grain desk background (SVG noise + gradient)

### CSS Variables ที่สำคัญ
ดูตัวแปรทั้งหมดใน `:root` block (บรรทัด 16-57 ของ index.html)

---

## 📱 ฟีเจอร์ทั้งหมด

### 1. Tab Navigation (5 แท็บ)
- **🏠 หน้าแรก** (home) — ID Card, สถิติ, ออนไลน์, โพสต์ล่าสุด
- **📖 กระดาน** (forum) — โพสต์ทั้งหมด, เรียงลำดับ, สร้างโพสต์ใหม่
- **📸 ความทรงจำ** (gallery) — Polaroid gallery, filter, upload, lightbox
- **🎉 กิจกรรม** (activities) — Event cards, RSVP, ปฏิทิน, สร้างกิจกรรม
- **👥 สมาชิก** (members) — Member cards, ค้นหา, เพิ่มสมาชิก

### 2. ระบบโพสต์ (Posts)
- สร้างโพสต์ใหม่ผ่าน Dialog
- Like / Unlike
- ความคิดเห็น (Comments)
- แท็ก (Dymo tags): เรื่องป่วน, พ่อบ้านใจกล้า, แม่โอ๋สายช้อป, มุกตลก, เรื่องกินเรื่องใหญ่
- เรียงตาม: ล่าสุด / ยอดนิยม / ความคิดเห็น
- **บันทึกลง Firestore** collection: `posts`

### 3. แกลเลอรี (Gallery)
- Masonry grid (CSS columns: 3)
- Polaroid-style photo cards พร้อม rotation effects
- Filter: ทั้งหมด / ของฉัน / ยอดนิยม / ล่าสุด
- **Upload ภาพจริง:** ลาก-วางหรือคลิกเลือกไฟล์, รองรับหลายไฟล์ (สูงสุด 10)
- Lightbox: ดูภาพเต็ม, prev/next, like, comment, ลบ (ถ้าเป็นภาพตัวเอง)
- **บันทึกลง Firestore** collection: `photos`

### 4. กิจกรรม (Events)
- Event cards พร้อม badge (กำลังจะมาถึง, ใหม่, สำคัญมาก)
- RSVP toggle
- ปฏิทินขนาดเล็ก (Mini Calendar) — เดือนไทย
- สร้างกิจกรรมใหม่: เลือกประเภท (6 แบบ), กรอกรายละเอียด, Live preview
- ลบกิจกรรมที่สร้างเอง
- **บันทึกลง Firestore** collection: `events`

### 5. สมาชิก (Members)
- Member cards พร้อม online badge
- ค้นหาสมาชิก
- ดูโปรไฟล์ผ่าน Dialog
- เพิ่มสมาชิกใหม่ผ่าน Dialog (เลือก emoji, กรอกข้อมูล)
- **บันทึกลง Firestore** collection: `members`

### 6. แชท (Chat)
- เปิดจากรายชื่อออนไลน์หรือจากโปรไฟล์สมาชิก
- ตอบกลับอัตโนมัติ (simulated replies)
- **บันทึกลง Firestore** collection: `chats`

### 7. ระบบอื่นๆ
- **Toast notifications** — แจ้งเตือนชั่วคราว (2.8 วินาที)
- **Light-dismiss dialogs** — ปิด dialog เมื่อคลิกนอก (รองรับ Safari fallback)
- **Mobile responsive** — Hamburger menu, ซ่อน tabs, stack layouts
- **Firestore Realtime Sync** — ข้อมูลอัปเดตทันทีทุก collection

---

## 🗂️ โครงสร้างข้อมูล (Data Schema)

### MEMBERS
```javascript
{
  id: '#FAM-01',        // รหัสสมาชิก
  name: 'พ่อแสนย์',      // ชื่อ/ฉายา
  quote: '"คำพูดติดปาก"', // คำคม
  city: 'บ้านแสนย์โอ๋',   // พิกัด
  club: 'ชมรม...',       // ตำแหน่ง/ชมรม
  fav: 'ของโปรด',        // ของโปรด
  emoji: '👨',           // อีโมจิแทนรูป
  online: true           // สถานะออนไลน์
}
```

### POSTS
```javascript
{
  id: 1,                  // ID (ใช้ Date.now() สำหรับโพสต์ใหม่)
  author: 'แม่โอ๋',       // ชื่อผู้โพสต์
  authorEmoji: '👩',      // อีโมจิผู้โพสต์
  date: 'วันนี้ — 10:45 น.', // วันที่แสดง
  title: 'หัวข้อ',         // หัวข้อโพสต์
  body: 'เนื้อหา...',      // เนื้อหา
  likes: 18,              // จำนวนถูกใจ
  liked: false,           // สถานะกดถูกใจ
  tag: 'เรื่องป่วน',       // แท็ก
  comments: [{            // ความคิดเห็น
    author: 'พ่อแสนย์',
    emoji: '👨',
    text: 'ข้อความ...',
    time: '11:02 น.'
  }]
}
```

### PHOTOS
```javascript
{
  id: 1,
  emoji: '🚗',            // อีโมจิ (สำหรับ placeholder)
  caption: 'คำบรรยาย',
  author: 'แม่โอ๋',
  authorEmoji: '👩',
  date: 'สิงหาคม 2566',
  likes: 45,
  liked: false,
  color: '#d4c9a8',       // สีพื้นหลัง placeholder
  isReal: false,          // true = ภาพจริง (มี src), false = emoji placeholder
  src: 'data:image/...',  // Data URL (เฉพาะ isReal=true)
  isMine: false,          // เป็นรูปของฉัน?
  comments: [...]
}
```

### EVENTS
```javascript
{
  id: 1,
  badge: 'กำลังจะมาถึง',
  title: 'ทริปครอบครัว 🏖️',
  date: '15 ธันวาคม 2569',
  time: '08:00 — 18:00 น.',
  location: 'หัวหิน',
  body: 'รายละเอียด...',
  going: ['พ','ม','จ','น'],  // อักษรย่อผู้ไป
  goingCount: 4,
  day: 15,                   // วันที่ (สำหรับ calendar)
  isMine: false              // สร้างเอง?
}
```

---

## 🔌 Firestore Collections

| Collection | หน้าที่ | Realtime Sync |
|-----------|---------|:------------:|
| `posts` | โพสต์ทั้งหมด | ✅ |
| `photos` | รูปภาพทั้งหมด | ✅ |
| `events` | กิจกรรมทั้งหมด | ✅ |
| `members` | สมาชิกทั้งหมด | ✅ |
| `chats` | ประวัติแชท | ✅ |

Realtime sync ใช้ `onSnapshot()` ใน function `initFirebaseSync()` (บรรทัด 2037-2118)

---

## ⚠️ สิ่งที่ต้องระวัง / Known Issues

1. **Firestore Rules เปิดกว้าง** — `allow read, write: if true` ⚠️ ควรเพิ่ม Authentication ก่อนนำไปใช้จริง
2. **ไม่มี Authentication** — ระบบยังไม่มีระบบ login/register, ผู้ใช้ทุกคนจะถูกระบุเป็น "พ่อแสนย์" (hardcoded)
3. **ภาพ upload เก็บเป็น Data URL** ใน Firestore — ไม่ได้ใช้ Firebase Storage จริงๆ (อาจเกิน Firestore document size limit 1MB)
4. **Single file architecture** — ทุกอย่างอยู่ใน `index.html` ไฟล์เดียว (~131KB) ทำให้แก้ไขง่ายแต่ไม่ scalable
5. **ข้อมูลเริ่มต้น hardcoded ใน JS** — มีสมาชิก 6 คน, โพสต์ 4 อัน, รูป 9 รูป, กิจกรรม 3 อัน
6. **Chat auto-reply** เป็นแค่ simulation (random จากข้อความสำเร็จรูป)
7. **ปฏิทิน** ใช้ logic คำนวณวันแรกของเดือนแบบ simplified (ไม่ใช่ปฏิทินจริง 100%)

---

## 🚀 วิธี Deploy

```bash
# ติดตั้ง Firebase CLI (ถ้ายังไม่มี)
npm install -g firebase-tools

# Login
firebase login

# Deploy
firebase deploy
```

Firebase Hosting จะ serve `index.html` เป็นหน้าหลัก (rewrite `**` → `/index.html`)

---

## 📐 สไตล์ CSS ที่สำคัญ (ต้องรักษาไว้)

### Notebook Paper Effect
```css
.notebook-paper {
  background-image:
    linear-gradient(90deg, transparent 79px, rgba(172,50,49,0.35) 79px, rgba(172,50,49,0.35) 81px, transparent 81px),
    linear-gradient(#cee9dc 0.1em, transparent 0.1em);
  /* เส้นแดง margin ซ้าย + เส้นสมุดเขียว */
}
```

### Chalkboard
```css
.chalkboard {
  background: #1e3a2f;
  border: 6px solid #3a2615; /* กรอบไม้ */
  box-shadow: inset 0 0 20px rgba(0,0,0,0.4); /* เงาด้านใน */
  /* + SVG noise overlay */
}
```

### Paper Stack Shadow
```css
--shadow-paper: -1px 1px 0 #ebe2c8, -2px 2px 0 #ebe2c8, -3px 3px 0 #ebe2c8, -4px 4px 6px rgba(0,0,0,0.12);
```

### Polaroid
```css
.polaroid-img-wrap {
  background: white;
  padding: 8px 8px 40px;
  transform: rotate(-2deg); /* หมุนเล็กน้อย */
}
```

---

## 🧭 แผนพัฒนาต่อที่ควรทำ

### ลำดับความสำคัญสูง
1. **เพิ่ม Firebase Authentication** — Login/Register (Google Sign-in, Email/Password)
2. **แก้ Firestore Rules** — จำกัดสิทธิ์อ่าน/เขียนตาม auth
3. **ใช้ Firebase Storage** สำหรับรูปภาพจริง แทน Data URL ใน Firestore
4. **ระบุ user ตัวจริง** — แก้ hardcoded "พ่อแสนย์" ให้เป็น dynamic ตาม auth user

### ลำดับความสำคัญปานกลาง
5. **แยก Code ออกจาก index.html** — แยก CSS, JS เป็นไฟล์แยก
6. **ฟีเจอร์แก้ไขโปรไฟล์** — ตอนนี้แค่แสดง toast "กำลังพัฒนา"
7. **Search functionality** — ตอนนี้แค่แสดง toast เมื่อค้นหา
8. **ลบโพสต์/แก้ไขโพสต์** — ยังไม่มี

### ลำดับความสำคัญต่ำ
9. **Dark mode**
10. **PWA support** (Service Worker, offline)
11. **Push notifications**
12. **Image compression** ก่อน upload

---

## 💡 สำหรับ Claude Code — คำแนะนำในการทำงาน

### การแก้ไขโค้ด
- ไฟล์หลักมีเพียง `index.html` ไฟล์เดียว — CSS อยู่บรรทัด 12-472, HTML อยู่บรรทัด 474-983, Firebase + JS อยู่บรรทัด 984-2140
- **ใช้ภาษาไทยทุกที่** — ทั้ง UI text, comments, toast messages, variable names (บางตัว)
- Design system อ้างอิงจาก `stitch_high_school_alumni_forum/DESIGN.md` แต่ implementation จริงอยู่ใน CSS variables ของ `index.html`

### การ Deploy
```bash
firebase deploy --only hosting    # Deploy เฉพาะ Hosting
firebase deploy --only firestore  # Deploy เฉพาะ Firestore Rules
firebase deploy                   # Deploy ทั้งหมด
```

### การทดสอบ
- เปิด `index.html` ด้วย browser โดยตรง (ไม่ต้อง build)
- หรือใช้ `firebase serve` เพื่อทดสอบ local
- Firebase จะทำงานได้ทั้งเปิดตรงและผ่าน serve

### ข้อกำหนดสำคัญ
- **ห้ามเปลี่ยน Design Theme** — ต้องรักษาสไตล์ "Scholar's Scrapbook" / Tactile Skeuomorphism
- **ห้ามเปลี่ยนภาษา** — UI ทั้งหมดเป็นภาษาไทย
- **Firebase Project** คือ `chatvidme` — อย่าเปลี่ยน config
- **สมาชิกครอบครัว** หลัก 6 คน: พ่อแสนย์, แม่โอ๋, เจน่า, โนอาห์, เจ้าตูบโฮ่งโฮ่ง, อาม่าสายเปย์
