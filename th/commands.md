# Git Commands

## 1. การรีเซ็ตไปยังคอมมิทก่อนหน้า

### คำสั่ง:
```
git reset HEAD~1
```

### คำอธิบาย:
คำสั่งนี้จะทำให้ `HEAD` ย้อนกลับไปยังคอมมิทที่ก่อนหน้าคอมมิทสุดท้าย โดยค่าเริ่มต้นจะใช้ตัวเลือก `mixed` ซึ่งหมายความว่าการเปลี่ยนแปลงที่ทำโดยคอมมิทล่าสุดจะยังคงอยู่ใน Working directory (ไดเรกทอรีทำงาน) ของคุณ

### ตัวเลือก:
- `--soft`: เก็บการเปลี่ยนแปลงไว้ใน Staging area (พื้นที่จัดเตรียม)
  ```
  git reset --soft HEAD~1
  ```
- `--mixed` (ค่าเริ่มต้น): เก็บการเปลี่ยนแปลงไว้ใน Working directory แต่จะลบออกจาก Staging area
- `--hard`: ลบการเปลี่ยนแปลงออกจากทั้ง Staging area และ Working directory
  ```
  git reset --hard HEAD~1
  ```

## 2. การย้อนกลับคอมมิทล่าสุด

### คำสั่ง:
```
git revert HEAD
```

### คำอธิบาย:
- คำสั่งนี้จะสร้างคอมมิทใหม่ที่ยกเลิกการเปลี่ยนแปลงที่เกิดจากคอมมิทก่อนหน้า ใช้เมื่อคุณต้องการย้อนผลของคอมมิทโดยไม่ต้องแก้ไขประวัติคอมมิท
- การ Revert คือการยกเลิกการแก้ไขโดยการสร้าง Commit ใหม่ขึ้นมาซึ่งมีหน้าตาเหมือนกับ Version ก่อนหน้านั้นของของ Commit ที่เรา Revert
- Revert จะปลอดภัยกว่า Reset ตรงที่ History การแก้ไขทั้งหมดจะยังคงได้รับการเก็บรักษาไว้

## 3. แสดงอีเมลของผู้ใช้ที่ตั้งค่าไว้

### คำสั่ง:
```
git config user.email
```

### คำอธิบาย:
คำสั่งนี้จะทำการแสดงอีเมลของผู้ใช้ที่ได้ตั้งค่าไว้ใน Git สำหรับการคอมมิทต่างๆ ที่เกี่ยวข้องกับโปรเจกต์ปัจจุบัน

### ตัวเลือก:
- ตั้งค่าอีเมลสำหรับโปรเจกต์ปัจจุบัน:
  ```
  git config user.email "newemail@example.com"
  ```
- ตั้งค่าอีเมลสำหรับทุกโปรเจกต์ (แบบ global):
  ```
  git config --global user.email "newemail@example.com"
  ```

## 4. แสดงชื่อของผู้ใช้ที่ตั้งค่าไว้

### คำสั่ง:
```
git config user.name
```

### คำอธิบาย:
คำสั่งนี้จะทำการแสดงชื่อของผู้ใช้ที่ได้ตั้งค่าไว้ใน Git สำหรับการคอมมิทต่างๆ ที่เกี่ยวข้องกับโปรเจกต์ปัจจุบัน

### ตัวเลือก:
- ตั้งชื่อสำหรับโปรเจกต์ปัจจุบัน:
  ```
  git config user.name "New Name"
  ```
- ตั้งชื่อสำหรับทุกโปรเจกต์ (แบบ global):
  ```
  git config --global user.name "New Name"
  ```

## 5. การตั้งค่า SSH Key สำหรับ GitHub
### การสร้าง SSH Key
1. เปิด Terminal หรือ Command Prompt แล้วรันคำสั่งต่อไปนี้:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
  **หมายเหตุ**: สำหรับระบบเก่าที่ไม่รองรับ Ed25519 ให้ใช้คำสั่งนี้แทน:
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
2. จากนั้น Terminal จะถามที่อยู่ที่เอาไว้เก็บ Key ถ้าเรามีชื่อไฟล์และโฟลเดอร์ที่จะเอาไว้เก็บ Key ก็ให้ใส่เป็น File path แต่ถ้าไม่มีจะใช้ชื่อไฟล์และโฟลเดอร์ที่โปรแกรมกำหนดให้ในวงเล็บคือ 
```bash
# ตั่งชื่อไฟล์เอง
> Enter file in which to save the key (C:\Users\YouFolderName/.ssh/id_ed25519):  C:\Users\YouFolderName/.ssh/my_custom_key
# or
> Enter file in which to save the key (C:\Users\YouFolderName/.ssh/id_ed25519): # สามารถกด Enter เพื่อใช้ชื่อไฟล์เริ่มต้น (id_ed25519) ได้เลย
```
3. จากนั้นโปรแกรมก็จะถามต่อว่าอยากจะใส่ Passphrase หรือไม่
```bash
> Enter passphrase (empty for no passphrase): [ใส่ Passphrase ที่คุณต้องการ]
> Enter same passphrase again: [ยืนยัน Passphrase อีกครั้ง]
```
  **ข้อควรทราบ**: หากคุณไม่ต้องการตั้ง Passphrase (ไม่แนะนำ เพราะคีย์ SSH จะไม่มีรหัสป้องกัน) ให้กด Enter โดยไม่ต้องพิมพ์อะไร

4. จากนั้นโปรแกรมจะแจ้งเราว่า Private Key และ Public Key ได้ถูกสร้างแล้ว
```bash
> Your identification has been saved in C:\Users\YouFolderName/.ssh/id_ed25519
> Your public key has been saved in C:\Users\YouFolderName/.ssh/id_ed25519.pub
> The key fingerprint is:
> SHA256:EX+amP1eT3stteST your_email@example.com
> The key's randomart image is:
+--[ED25519 256]--+
| =EXX*=*.o       |
|X*AAM.+.P .      |
|P+Le*.P+.LE      |
| T +.E ...       |
|.   .  .o o      |
|      S .. T     |
|       +.-       |
|       ..        |
|  TE++S==to      |
+----[SHA256]-----+
```

### การเพิ่ม SSH Key เข้า SSH Agent
 **ข้อควรรู้เกี่ยวกับ SSH Agent**: 
 คุณสามารถเลือก ไม่เพิ่ม SSH key ไปยัง SSH agent ได้ แต่สิ่งนี้หมายความว่าเมื่อคุณต้องการใช้ SSH key (เช่นในการเชื่อมต่อกับ GitHub หรือเซิร์ฟเวอร์), คุณจะต้องพิมพ์ Passphrase ของ SSH key ทุกครั้งที่ทำการเชื่อมต่อ หรือหากคุณไม่ได้ตั้งค่า Passphrase ไว้ การเชื่อมต่อจะดำเนินการโดยไม่ต้องผ่าน SSH agent และจะไม่ต้องพิมพ์รหัสผ่านใด ๆ
 - ถ้าคุณไม่เพิ่ม SSH key ไปยัง SSH agent: คุณจะต้องป้อน Passphrase (หากตั้งไว้) ทุกครั้งที่มีการใช้งาน SSH key
 - ถ้าคุณเพิ่ม SSH key ไปยัง SSH agent: SSH agent จะจัดการกับ SSH key ของคุณ และคุณจะไม่ต้องป้อน Passphrase ซ้ำเมื่อใช้งาน

**ขั้นตอนการเพิ่ม SSH Key เข้า SSH Agent**: 
1. เพิ่ม SSH key ไปยัง SSH agent เพื่อให้ SSH agent จัดการคีย์ให้ คุณสามารถใช้คำสั่งนี้:

   - Start the SSH agent:
     ```bash
      eval "$(ssh-agent -s)"
      ```
   - Add your SSH private key to the agent:
    ```bash
      ssh-add ~/.ssh/id_ed25519
    
    # กรณีใช้ RSA:
      ssh-add ~/.ssh/id_rsa
    ```

### การเพิ่ม SSH Key เข้าบัญชี GitHub
1. คัดลอก SSH public key ไปยังคลิปบอร์ด:
- สำหรับ  macOS:
```bash
pbcopy < ~/.ssh/id_ed25519.pub
# or
gc .\.ssh\id_ed25519.pub
```

- สำหรับ  Windows:
```bash
clip < C:/Users/YouFolderName/.ssh/id_ed25519.pub
```

**หากต้องการดู Public Key ก่อนการคัดลอก สามารถใช้คำสั่งนี้**:
- คำสั่งในเทอร์มินอล:
  ```bash
  # macOS
  cat ~/.ssh/id_ed25519.pub
  
  # Windows
  type C:\Users\YouFolderName\.ssh\id_ed25519.pub
  ```

- **วิธีอื่นในการดูไฟล์ Public Key**: 
เปิดไฟล์ .pub ด้วย Notepad หรือโปรแกรม text editor ใด ๆ และคัดลอก
หรือคุณสามารถเปิดไฟล์นี้ด้วยคำสั่ง:
```bash
notepad C:\Users\YouFolderName\.ssh\id_ed25519.pub
```

2. Go to GitHub website:
   - คลิกที่รูปโปรไฟล์ของคุณ
   - ไปที่ **Settings > SSH and GPG keys**
   - คลิก **New SSH key**
   - วาง public key ที่คุณคัดลอกมาในช่อง **Key** และตั้งชื่อในช่อง **Title**
   - คลิก **Add SSH key**

### ทดสอบการเชื่อมต่อ
```bash
ssh -T git@github.com
```
เมื่อเชื่อมต่อสำเร็จ จะเห็นข้อความ:
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

# Utility Commands
## 1. การสร้าง Secret Key
### คำสั่ง:
```bash
node -e "console.log(require('crypto').randomBytes(256).toString('base64'));"
```
### คำอธิบาย:
คำสั่งนี้จะสร้างสตริงสุ่มขนาด 256 ไบต์ที่เข้ารหัสแบบ base64 เหมาะสำหรับใช้เป็น secret key ในแอปพลิเคชันของคุณ คำสั่งนี้ใช้ Node.js และโมดูล `crypto` ที่มีอยู่ในตัวเพื่อสร้างคีย์สุ่มที่มีความปลอดภัยทางคริปโตกราฟี
### ตัวเลือก:
- หากต้องการเปลี่ยนความยาวของคีย์ ให้แก้ไขตัวเลขใน `randomBytes()` เช่น สำหรับคีย์ขนาด 128 ไบต์:
  ```bash
  node -e "console.log(require('crypto').randomBytes(128).toString('base64'));"
  ```
