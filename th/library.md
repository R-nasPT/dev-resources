# ไลบรารีสำหรับการพัฒนา

### การจัดการเส้นทาง (Routing)
- `react-router-dom`: ใช้สำหรับการจัดการเส้นทางในแอปพลิเคชัน React
- `nuqs`: ไลบรารีสำหรับจัดการ URL search params ที่รองรับการซิงค์ค่าระหว่าง URL และสถานะของแอปพลิเคชัน พร้อมฟีเจอร์การ parse และ serialize ข้อมูลแบบอัตโนมัติ
- `query-string`: ไลบรารีที่ช่วยในการจัดการและแปลง URL query strings ให้เป็น object และกลับกัน รองรับการ parse ค่าหลายรูปแบบและมี API ที่ใช้งานง่าย

### ฟอร์มและการตรวจสอบความถูกต้อง
- `@tanstack/react-query`: สำหรับการดึงข้อมูลและการแคช
- `@tanstack/react-query-devtools`: เครื่องมือสำหรับแก้ไขข้อบกพร่องและตรวจสอบคิวรีใน `@tanstack/react-query`
- `swr` (stale-while-revalidate): React Hooks สำหรับการดึงข้อมูล
- `react-hook-form` & `@hookform/resolvers`: การจัดการฟอร์มใน React
- `yup` | `zod` | `joi` | `ajv`: ไลบรารีสำหรับการตรวจสอบความถูกต้องของสคีมา

### การดึงข้อมูลและการจัดการสถานะ
- `axios`: ไลบรารี HTTP สำหรับการเรียก API
- `use-axios-client`: Custom React hook สำหรับการใช้งาน axios ใน React components
- `@reduxjs/toolkit` | `react-redux`: การจัดการสถานะโดยใช้ Redux ใน React
- `zustand`: ไลบรารีจัดการสถานะที่มีขนาดเบา

### ไลบรารียูทิลิตี้
- `lodash` & `@types/lodash`: ฟังก์ชันยูทิลิตี้สำหรับ JavaScript

### การเลือกและเมนูแบบดรอปดาวน์
- `react-select`: คอมโพเนนต์อินพุตแบบเลือกที่สามารถปรับแต่งได้
- `react-animate-height`: เอนิเมชันความสูงสำหรับเอฟเฟกต์การเลื่อนของดรอปดาวน์
- `react-tailwindcss-datepicker`: คอมโพเนนต์ตัวเลือกวันที่ที่ใช้สไตล์ Tailwind CSS

### แผนภูมิ
- `chart.js` & `react-chartjs-2`: สำหรับการแสดงข้อมูลด้วยภาพใน React
- `Recharts`: ไลบรารีการสร้างแผนภูมิที่สร้างขึ้นจากคอมโพเนนต์ React

### ลากและวาง
- `react-beautiful-dnd`: ไลบรารีสำหรับสร้างอินเตอร์เฟซแบบลากและวาง
- `react-dnd` & `react-dnd-html5-backend`: ยูทิลิตี้ลากและวางที่ยืดหยุ่น

### เอนิเมชัน
- `gsap` (GreenSock): ไลบรารีเอนิเมชันขั้นสูง
- `Framer Motion`: ไลบรารีเอนิเมชันสำหรับ React
- `React Spring`: เอนิเมชันที่ใช้หลักการทางฟิสิกส์แบบสปริง
- `react-reveal` | `react-awesome-reveal` | `ScrollReveal`: ไลบรารีเอนิเมชันที่ทำงานตามการเลื่อน

### เอนิเมชันข้อความ
- `react-type-animation`: เอฟเฟกต์แอนิเมชันแบบพิมพ์ดีด
- `react-random-reveal`: เอฟเฟกต์เปิดเผยข้อความแบบสุ่ม
- `react-countup`: คอมโพเนนต์นับเลขแบบเอนิเมชัน
- `react-text-loop` | `react-text-loop-next`: เอนิเมชันข้อความแบบวนซ้ำ
- `react-fast-marquee`: ข้อความเลื่อนแบบป้ายไฟวิ่ง
- `react-fade-in`: เอนิเมชันเฟดอินสำหรับ React

### Hooks หลากหลาย
- `react-use`: คอลเลกชันของ React hooks ที่จำเป็น
- `@uidotdev/usehooks`: Hooks ที่กำหนดเองหลากหลายรูปแบบ
- `usehooks-ts`: Hooks ที่มีการกำหนดประเภทสำหรับ TypeScript ใน React

### การสนับสนุน Tailwind
- `tailwind-merge`: รวมชื่อคลาสของ Tailwind CSS
- `clsx`: ยูทิลิตี้สำหรับการรวมชื่อคลาสแบบมีเงื่อนไข
- `classix`: ยูทิลิตี้ชื่อคลาสที่ทำงานเร็ว
- `classnames`: ยูทิลิตี้สำหรับจัดการชื่อคลาส
- `tailwind-variants`: รูปแบบตัวแปรสำหรับ Tailwind CSS
- `class-variance-authority`: ยูทิลิตี้สำหรับตัวแปร ของ Tailwind CSS
- `windstitch`: ตัวช่วยจัดสไตล์ Tailwind CSS

#### การใช้งานยูทิลิตี้ร่วมกัน
- **การใช้ `twMerge` และ `clsx`:** 
  ```javascript
  const cn = twMerge(clsx(...));
  ```
  การรวมกันนี้ใช้เพื่อรวมคลาสของ Tailwind CSS กับตรรกะแบบมีเงื่อนไขเพื่อการจัดการคลาสที่ดีขึ้น

### การประมวลผลเอกสารและสื่อ
- `react-to-print`: ไลบรารีสำหรับการพิมพ์คอมโพเนนต์ React
- `@react-pdf/renderer`: ไลบรารีสำหรับสร้างเอกสาร PDF ใน React
- `react-pdf-tailwind`: การจัดสไตล์ PDF โดยใช้ Tailwind CSS
- `react-barcode`: ตัวสร้างบาร์โค้ดสำหรับ React
- `react-qr-code`: ตัวสร้าง QR code สำหรับ React
- `@zxing/library`: ไลบรารีสำหรับการสแกนบาร์โค้ด
- `react-media-recorder`: ไลบรารีสำหรับบันทึกเสียงและวิดีโอใน React
- `exceljs`: ไลบรารีสำหรับอ่าน, จัดการ และเขียนข้อมูลสเปรดชีต

### ไลบรารีจัดการวันและเวลา
- `date-fns`: ไลบรารียูทิลิตี้วันที่สมัยใหม่สำหรับใช้ในการแยกวิเคราะห์, จัดรูปแบบ และจัดการวันที่
- `@date-fns/tz`: รองรับโซนเวลาสำหรับ date-fns
- `@date-fns/utc`: รองรับ UTC สำหรับ date-fns
- `dayjs`: ทางเลือกที่มีขนาดเบาแทน Moment.js สำหรับจัดการวันที่

---

## BACK END

### ทั้ง JavaScript และ TypeScript
- `dotenv`: โหลดตัวแปรสภาพแวดล้อม
- `express`: เว็บเฟรมเวิร์กสำหรับ Node.js
- `cors`: เปิดใช้งานการแชร์ทรัพยากรข้ามโดเมน

### JavaScript
- `nodemon`: รีสตาร์ทแอปพลิเคชัน Node.js โดยอัตโนมัติ

### TypeScript
- `@types/express`: คำจำกัดความประเภทสำหรับ Express.js
- `typescript` & `ts-node`: รองรับ TypeScript สำหรับ Node.js
- `ts-node-dev`: สภาพแวดล้อมการพัฒนา TypeScript สำหรับ Node.js
- `@types/cors`: คำจำกัดความประเภทสำหรับ `cors`

---

## การตรวจสอบสิทธิ์

### Front-end
- `jwt-decode`: ถอดรหัสโทเค็น JWT

### Back-end
- `(bcrypt & @types/bcrypt)` | `(bcryptjs & @types/bcryptjs)` | `bcrypt-ts`: การเข้ารหัสรหัสผ่าน
- `@types/jsonwebtoken` & `jsonwebtoken`: การจัดการ JWT สำหรับการตรวจสอบสิทธิ์
- **เคล็ดลับ (แบบง่าย)**: `jose`: ไลบรารียูทิลิตี้สำหรับจัดการ JWT และ JWS

---

## การเข้ารหัสและถอดรหัส

- `crypto-js` & `@types/crypto-js`: ไลบรารีการเข้ารหัสลับสำหรับเข้ารหัสและถอดรหัสข้อมูล
- `libsodium-wrappers` & `@types/libsodium-wrappers`: การเข้ารหัสและถอดรหัสที่ปลอดภัย
- **เคล็ดลับ (แบบง่าย)**: `cryptr`, `node-encryption`: ยูทิลิตี้การเข้ารหัสแบบง่าย

---

## Socket.io

### Front-end
- `socket.io-client`: WebSocket client สำหรับการสื่อสารแบบเรียลไทม์

### Back-end
- `socket.io`: WebSocket server สำหรับแอปพลิเคชันแบบเรียลไทม์
