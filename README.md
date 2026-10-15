# ระบบบัญชี คุณนู๋สไลด์ออน

บันทึกรายรับรายจ่ายรถสไลด์ พร้อมหน้าสรุปและส่งออก Excel

## ไฟล์
- `index.html` ตัวโปรแกรมทั้งหมด
- ข้อมูลเดิมจาก Excel (932 งาน) ไม่ได้อยู่ใน repo นี้เพื่อไม่ให้ข้อมูลลูกค้าเปิดเผยสาธารณะ เปิดโปรแกรมครั้งแรกแล้วกด "เลือกไฟล์ Excel" แล้วเลือกไฟล์ รับ-จ่าย มค - มิย 69.xlsx เพื่อนำเข้า

## ตั้งค่า (แก้ที่ด้านบนของ `<script>` ใน index.html)
```js
const LOGIN={user:"admin",pass:"1234"};   // ชื่อผู้ใช้/รหัสผ่าน
const FIREBASE_CONFIG=null;               // ใส่ config Firebase เพื่อให้ทุกเครื่องเห็นข้อมูลตรงกัน
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
