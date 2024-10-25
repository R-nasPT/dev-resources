# Git Commands

## 1. Resetting to the Previous Commit

### Command :
```
git reset HEAD~1
```

### Description :
This command resets the `HEAD` to the previous commit. By default, it uses the `mixed` option, which means the changes made in the latest commit will remain in your working directory but will be removed from the staging area.

### Options :
- `--soft`: Keeps changes in the staging area.
  ```
  git reset --soft HEAD~1
  ```
- `--mixed` (default): Keeps changes in the working directory but removes them from the staging area.
- `--hard`:  Removes changes from both the staging area and the working directory.
  ```
  git reset --hard HEAD~1
  ```

## 2. Reverting the Last Commit

### Command:
```
git revert HEAD
```

### Description:
This command creates a new commit that undoes the changes made by the previous commit. Use this when you want to reverse the effects of a commit without altering the commit history.

## 3. Displaying the User's Configured Email

### Command:
```
git config user.email
```

### Description:
This command displays the email address configured for the current project in Git, which is used when committing changes.

### Options:
- Set the email for the current project:
  ```bash
  git config user.email "newemail@example.com"
  ```
- Set the email globally:
  ```bash
  git config --global user.email "newemail@example.com"
  ```

## 4. Displaying the User's Configured Name

### Command:
```
git config user.name
```

### Description:
This command displays the username configured for Git, which is used in the commit history of the current project.

### Options:
- Set the username for the current project:
  ```bash
  git config user.name "New Name"
  ```
- Set the username globally:
  ```bash
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
## 1. Creating a Secret Key
### Command:
```bash
node -e "console.log(require('crypto').randomBytes(256).toString('base64'));"
```
### Description:
This command generates a random 256-byte string encoded in base64, suitable for use as a secret key in your applications. It uses Node.js and the built-in `crypto` module to create a cryptographically strong random key.
### Options:
- To change the key length, modify the number in `randomBytes()`. For example, for a 128-byte key:
  ```bash
  node -e "console.log(require('crypto').randomBytes(128).toString('base64'));"
  ```
