# ระบบบัญชี คุณนู๋สไลด์ออน

บันทึกรายรับรายจ่ายรถสไลด์ พร้อมหน้าสรุปและส่งออก Excel

## ไฟล์
- `index.html` ตัวโปรแกรมทั้งหมด
- ข้อมูลเดิมจาก Excel (932 งาน) ไม่ได้อยู่ใน repo นี้เพื่อไม่ให้ข้อมูลลูกค้าเปิดเผยสาธารณะ เปิดโปรแกรมครั้งแรกแล้วกด "เลือกไฟล์ Excel" แล้วเลือกไฟล์ รับ-จ่าย มค - มิย 69.xlsx เพื่อนำเข้า

## ตั้งค่า (แก้ที่ด้านบนของ `<script>` ใน index.html)
```js
const FIREBASE_CONFIG={...}   // เชื่อมกับโปรเจกต์ Firebase "khunnu-slideon" แล้ว
```

## ขึ้น GitHub Pages
2. Settings → Pages → Source: Deploy from a branch → `main` / root → Save
3. เปิดลิงก์ `https://<username>.github.io/<repo>/`

## เก็บข้อมูลให้ทุกเครื่องเห็นตรงกัน (Firebase)
ถ้า `FIREBASE_CONFIG` เป็น `null` ข้อมูลจะเก็บในเครื่อง/เบราว์เซอร์นั้นเท่านั้น
1. Firebase Console → สร้างโปรเจกต์ → เพิ่ม Web app → คัดลอก `firebaseConfig` มาวางแทน `null`
2. Build → Firestore Database → Create database
3. ข้อมูลเก็บใน collection `months` (1 เอกสารต่อเดือน เช่น `2026-01`)

## ข้อควรรู้เรื่องความปลอดภัย
หน้าล็อกอินตรวจรหัสในเบราว์เซอร์ ใครเปิดดูซอร์สโค้ดจะเห็นรหัสผ่านได้ และ repo สาธารณะบน GitHub ทุกคนอ่านโค้ดได้
ถ้าใช้จริงกับข้อมูลการเงิน ควรเปลี่ยนไปใช้ Firebase Authentication และตั้ง Firestore Rules ให้เฉพาะผู้ล็อกอินอ่าน/เขียนได้

## สถานะปัจจุบัน
- เชื่อม Firebase โปรเจกต์ `khunnu-slideon` แล้ว (Firestore: asia-southeast1)
- ล็อกอินด้วยอีเมล/รหัสผ่านของ Firebase Authentication — เพิ่มผู้ใช้ที่ Firebase Console → Authentication → Users → Add user
- Firestore Rules: อ่าน/เขียนได้เฉพาะผู้ที่ล็อกอิน
