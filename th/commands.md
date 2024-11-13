# Git Commands

## 1. Git Areas

Git มีการจัดการไฟล์ในสามพื้นที่หลัก ได้แก่:

### พื้นที่ทำงาน 
ชื่อที่ใช้เรียก:
- Working Directory
- Working Area
- Working Tree
- Workspace

**คำอธิบาย**: เป็นพื้นที่ที่เราทำงานจริงๆ กับไฟล์ต่างๆ ในโปรเจค สามารถแก้ไข สร้าง หรือลบไฟล์ได้โดยตรง ไฟล์ในพื้นที่นี้ยังไม่ถูกติดตามโดย Git จนกว่าจะถูก add เข้า Staging Area

### พื้นที่จัดเตรียม 
ชื่อที่ใช้เรียก:
- Staging Area
- Index
- Cache
- Stage

**คำอธิบาย**: คือที่ที่คุณเตรียมไฟล์ที่จะทำการคอมมิท เมื่อคุณใช้คำสั่ง `git add <filename>` ไฟล์จะถูกย้ายจาก Working Directory ไปยัง Staging Area ซึ่ง Staging Area ช่วยให้คุณสามารถเลือกเฉพาะไฟล์ที่ต้องการจะคอมมิทได้

### พื้นที่เก็บถาวร
ชื่อที่ใช้เรียก:
- Repository
- Repository Area
- Git Repository
- Repo
- .git Directory

**คำอธิบาย**: คือที่ที่ Git เก็บประวัติการเปลี่ยนแปลงทั้งหมด (commits) ของโปรเจกต์ เมื่อคุณทำการคอมมิท (`git commit`), การเปลี่ยนแปลงใน Staging Area จะถูกบันทึกลงใน Repository ซึ่งเป็นที่เก็บข้อมูลที่สามารถมีประวัติการเปลี่ยนแปลงหลาย ๆ เวอร์ชัน

การเข้าใจ Git Areas ช่วยให้คุณสามารถควบคุมการเปลี่ยนแปลงในโปรเจกต์ได้ดีขึ้น และช่วยในการจัดการเวอร์ชันของโค้ดอย่างมีประสิทธิภาพ!

## 2. การรีเซ็ตไปยังคอมมิทก่อนหน้า

### คำสั่ง:
```
git reset HEAD~1
```

### คำอธิบาย:
คำสั่งนี้จะทำให้ `HEAD` ย้อนกลับไปยังคอมมิทที่ก่อนหน้าคอมมิทสุดท้าย โดยค่าเริ่มต้นจะใช้ตัวเลือก `mixed` ซึ่งหมายความว่าการเปลี่ยนแปลงที่ทำโดยคอมมิทล่าสุดจะยังคงอยู่ใน Working directory (พื้นที่ทำงาน) ของคุณ

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
  
  **ข้อแตกต่างและคำสั่งของการ Reset สามแบบสามารถสรุปได้ดังนี้**

|                      | **ผลกระทบต่อไฟล์ที่ได้แก้ไขไป** | **สิ่งที่ต้องทำหากต้องการ Commit ใหม่**       | **คำสั่ง**                          |
|----------------------|----------------------------------|-------------------------------------------------|-------------------------------------|
| **Soft Reset**       | ย้ายไปอยู่ Staging Area          | Commit ใหม่ได้เลย                              | `git reset --soft <target_commit_id>` |
| **Mixed Reset (default)** | ย้ายไปอยู่ Working Directory       | ต้องเลือกไฟล์เข้าไปใน Staging Area ก่อน       | `git reset --mixed <target_commit_id>` |
| **Hard Reset**       | หายไปอย่างถาวร                   | ต้องทำการแก้ไขใหม่ทั้งหมด                    | `git reset --hard <target_commit_id>` |


## 3. การย้อนกลับคอมมิทล่าสุด

### คำสั่ง:
```
git revert HEAD
```

### คำอธิบาย:
- คำสั่งนี้จะสร้างคอมมิทใหม่ที่ยกเลิกการเปลี่ยนแปลงที่เกิดจากคอมมิทก่อนหน้า ใช้เมื่อคุณต้องการย้อนผลของคอมมิทโดยไม่ต้องแก้ไขประวัติคอมมิท
- การ Revert คือการยกเลิกการแก้ไขโดยการสร้าง Commit ใหม่ขึ้นมาซึ่งมีหน้าตาเหมือนกับ Version ก่อนหน้านั้นของของ Commit ที่เรา Revert
- Revert จะปลอดภัยกว่า Reset ตรงที่ History การแก้ไขทั้งหมดจะยังคงได้รับการเก็บรักษาไว้

## 4. แสดงอีเมลของผู้ใช้ที่ตั้งค่าไว้

### คำสั่ง:
```
git config user.email
```

### คำอธิบาย:
คำสั่งนี้จะทำการแสดงอีเมลของผู้ใช้ที่ได้ตั้งค่าไว้ใน Git สำหรับการคอมมิทต่างๆ ที่เกี่ยวข้องกับโปรเจกต์ปัจจุบัน

### ตัวเลือก:
- ตั้งค่าอีเมลสำหรับโปรเจกต์ปัจจุบัน:
  ```bash
  git config user.email "newemail@example.com"
  ```
- ตั้งค่าอีเมลสำหรับทุกโปรเจกต์ (แบบ global):
  ```bash
  git config --global user.email "newemail@example.com"
  ```

## 5. แสดงชื่อของผู้ใช้ที่ตั้งค่าไว้

### คำสั่ง:
```
git config user.name
```

### คำอธิบาย:
คำสั่งนี้จะทำการแสดงชื่อของผู้ใช้ที่ได้ตั้งค่าไว้ใน Git สำหรับการคอมมิทต่างๆ ที่เกี่ยวข้องกับโปรเจกต์ปัจจุบัน

### ตัวเลือก:
- ตั้งชื่อสำหรับโปรเจกต์ปัจจุบัน:
  ```bash
  git config user.name "New Name"
  ```
- ตั้งชื่อสำหรับทุกโปรเจกต์ (แบบ global):
  ```bash
  git config --global user.name "New Name"
  ```

## 6. การตั้งค่า SSH Key สำหรับ GitHub
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
## 7. วิธีการเขียน Commit Message ที่ดี
ตามหลักการนี้ ตัว Commit Message ควรจะอยู่ในรูปแบบ `type(scope?): subject`

- `type` คือ ชนิดของ Commit
- `(scope?)` คือ ขอบเขตของการเปลี่ยนแปลงใน Commit ส่วนนี้เป็นส่วนที่ไม่จำเป็นต้องมีก็ได้
- `subject` คือ รายละเอียดของการเปลี่ยนแปลงที่ทำใน Commit

  **ตัวอย่างการเขียน Commit message ที่ดี**

  ```bash
  git commit -m "feat: add header section on landing page"
  git commit -m "fix(product-listing): limit display product to 10"
  git commit -m "style: format code with prettier"
  git commit -m "refactor: simplify authentication logic"
  git commit -m "docs: update API documentation"
  git commit -m "chore(package.json): update dependencies to latest version"
  git commit -m "perf(dashboard): decrease loading time on graphs"
  git commit -m "test(payment): ensure checkout function"
  ```
**รายระเอียดของ type แต่ละแบบ**

| **“type”** | **รายละเอียด** |
| --- | --- |
| feat | ใช้กำกับ Commit ที่เกี่ยวข้องกับการทำ Feature ใหม่ๆ เช่น ระบบลงทะเบียน, ระบบอัพเดทโปรไฟล์ |
| fix | ใช้กำกับ Commit ที่เกี่ยวข้องกับการแก้ไขข้อผิดพลาดที่เกิดจากการเขียนโค้ด |
| style | ใช้กำกับ Commit ที่เกี่ยวข้องกับการทำให้หน้าตาเว็บไซท์ดูดีขึ้น |
| docs | ใช้กำกับ Commit ที่เกี่ยวข้องกับการเขียน Documents (เอกสาร) เช่น เอกสารที่ระบุสเปคของโปรแกรม |
| chore | ใช้กำกับ Commit ที่เกี่ยวข้องกับงานทั่วไป เช่น การอัปเดต dependencies, การตั้งค่า config, หรือการแก้ไขงานที่ไม่เกี่ยวกับโค้ดโดยตรง |
| refactor | ใช้กำกับ Commit ที่เกี่ยวข้องกับการ Refactor คือการเขียนโค้ดอีกแบบที่ให้ผลลัพธ์เหมือนเดิม |
| perf | ใช้กำกับ Commit ที่เกี่ยวข้องกับการปรับ Performance (ประสิทธิภาพการทำงาน) ของโปรแกรม |
| test | ใช้กำกับ Commit ที่เกี่ยวข้องกับการเขียน Test (ชุดทดสอบการทำงานของโปรแกรม) |

### ตัวเลือกเพิ่มเติมสำหรับ git commit:
#### 1. การใช้ -m (Message)
1. เตรียมไฟล์ที่จะ Commit
```bash
git add file1.txt file2.txt    # เพิ่มไฟล์เฉพาะที่ต้องการ
git add .                      # เพิ่มไฟล์ที่แก้ไขทั้งหมด
```

2. ทำการ Commit
```bash
git commit -m "อธิบายการเปลี่ยนแปลงที่ทำ"
```

##### การทำงาน:
- ใช้เมื่อคุณต้องการคอมมิทการเปลี่ยนแปลงในไฟล์ที่อยู่ใน Staging Area
- คำสั่งนี้จะทำการคอมมิทเฉพาะไฟล์ที่ถูกเพิ่มใน Staging Area โดยใช้ `git add` ก่อนหน้านี้

##### กรณีที่เหมาะสม
- เมื่อต้องการควบคุมว่าจะ Commit ไฟล์ไหนบ้าง
- เมื่อต้องการแยก Commit เป็นชุดๆ ตามฟีเจอร์
- เมื่อมีไฟล์ใหม่ที่ยังไม่เคยถูก Track

#### 2. การใช้ -am (Add + Message)
```bash
git commit -am "อธิบายการเปลี่ยนแปลงที่ทำ"
```
##### การทำงาน:
- ใช้เมื่อคุณต้องการคอมมิทการเปลี่ยนแปลงในไฟล์ที่ถูกติดตาม (tracked files) และต้องการให้ Git เพิ่มไฟล์เหล่านั้นไปยัง Staging Area อัตโนมัติ
- คำสั่งนี้จะทำการคอมมิทการเปลี่ยนแปลงทั้งหมดในไฟล์ที่ถูกติดตามที่มีการแก้ไขแล้ว โดยไม่จำเป็นต้องใช้ `git add`

##### กรณีที่เหมาะสม
- เมื่อแก้ไขไฟล์ที่มีอยู่แล้วหลายไฟล์
- เมื่อต้องการ Commit ไฟล์ที่แก้ไขทั้งหมดพร้อมกัน
- เมื่อมั่นใจว่าการแก้ไขทั้งหมดควรอยู่ใน Commit เดียวกัน

##### ข้อควรระวัง
- ไม่รวมไฟล์ใหม่ที่ยังไม่เคยถูก Track
- ควรตรวจสอบสถานะไฟล์ด้วย `git status` ก่อนใช้

#### 3. การใช้ --amend

1. แก้ไขเฉพาะข้อความ Commit
```bash
git commit --amend -m "ข้อความ Commit ใหม่"
```

2. เพิ่มไฟล์ที่ลืม Commit
```bash
git add forgotten_file.txt
git commit --amend --no-edit    # ใช้ข้อความ Commit เดิม
```

3. แก้ไขทั้งไฟล์และข้อความ
```bash
git add new_changes.txt
git commit --amend -m "ข้อความใหม่พร้อมไฟล์เพิ่มเติม"
```

##### กรณีที่เหมาะสม
- แก้ไขข้อความ Commit ที่พิมพ์ผิด
- เพิ่มไฟล์ที่ลืม Commit ในชุดการแก้ไขเดียวกัน
- รวมการแก้ไขเล็กๆ น้อยๆ เข้ากับ Commit ล่าสุด

##### ข้อควรระวังสำคัญ
1. ห้ามใช้กับ Commit ที่:
   - Push ขึ้น Remote แล้ว
   - มีคนอื่น Pull ไปใช้แล้ว
   - อยู่ใน Branch ที่แชร์กับผู้อื่น

2. เพราะ --amend จะ:
   - เปลี่ยน Hash ของ Commit
   - สร้างประวัติ Git ใหม่
   - อาจทำให้เกิดปัญหาเมื่อ Merge

### ตารางเปรียบเทียบตัวเลือกการ Commit

| ตัวเลือก | การใช้งาน | ข้อดี | ข้อควรระวัง | คำสั่งตัวอย่าง |
|----------|----------|-------|-------------|----------------|
| **-m** | Commit ไฟล์ที่อยู่ใน Staging Area | - ควบคุมได้ว่าจะ Commit ไฟล์ไหนบ้าง<br>- เหมาะกับการแยก Commit เป็นชุดๆ | - ต้องใช้ `git add` ก่อนทุกครั้ง | `git commit -m "เพิ่มระบบ login"` |
| **-am** | Commit ไฟล์ที่ถูกติดตามทั้งหมด | - สะดวก รวดเร็ว<br>- ไม่ต้องใช้ `git add` | - อาจ Commit ไฟล์ที่ไม่ต้องการโดยไม่ตั้งใจ | `git commit -am "แก้บัคหน้า login"` |
| **--amend** | แก้ไขคอมมิทล่าสุด | - แก้ไขข้อผิดพลาดได้<br>- เพิ่มไฟล์ที่ลืม Commit ได้ | - ห้ามใช้กับ Commit ที่ Push แล้ว<br>- เปลี่ยนประวัติ Git | `git commit --amend -m "แก้ไขข้อความ"` |

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
