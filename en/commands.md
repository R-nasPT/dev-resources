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
## 5. Setting Up SSH Key for GitHub
### Generate SSH Key
1. Open Terminal and run the following command:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
  **Note**: If you're using a legacy system that doesn't support 
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
2. When prompted, specify a file path to save the key, or press Enter to use the default path:
```bash
# Custom file path
> Enter file in which to save the key (C:\Users\YouFolderName/.ssh/id_ed25519):  C:\Users\YouFolderName/.ssh/my_custom_key

# Or press Enter for the default path
> Enter file in which to save the key (C:\Users\YouFolderName/.ssh/id_ed25519):
```
3. Next, you’ll be asked to enter a passphrase. You can add a passphrase for additional security or press Enter to skip (not recommended for security reasons):
```bash
> Enter passphrase (empty for no passphrase): [Type your passphrase]
> Enter same passphrase again: [Confirm your passphrase]
```

4. Once complete, you’ll see a message indicating the private and public keys have been generated:
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

### Add SSH Key to SSH Agent
 **About SSH Agentt**: 
 You can choose not to add the SSH key to the SSH agent, but this means that when you want to use the SSH key (e.g., to connect to GitHub or a server), you will need to enter the passphrase for the SSH key every time you connect. If you haven't set a passphrase, the connection will proceed without the SSH agent, and you won't need to enter any password.
 - If you don't add the SSH key to the SSH agent: You will need to enter the passphrase (if set) every time you use the SSH key.
 - If you add the SSH key to the SSH agent: The SSH agent will manage your SSH key, and you won't have to re-enter the passphrase when using it.

**Steps to Add Your SSH Key to the SSH Agent:**: 
1. Add the SSH key to the SSH agent so that the SSH agent can manage the key for you. You can use the following command:

   - Start the SSH agent:
     ```bash
      eval "$(ssh-agent -s)"
      ```
   - Add your SSH private key to the agent:
    ```bash
      ssh-add ~/.ssh/id_ed25519
    
    # If using RSA:
      ssh-add ~/.ssh/id_rsa
    ```

### Add SSH Key to GitHub Account
1. Add SSH Key to GitHub Account
- For  macOS:
```bash
pbcopy < ~/.ssh/id_ed25519.pub
# or
gc .\.ssh\id_ed25519.pub
```

- For  Windows:
```bash
clip < C:/Users/YouFolderName/.ssh/id_ed25519.pub
```

**To view the public key before copying, use**:
- Commands in the terminal:
  ```bash
  # macOS
  cat ~/.ssh/id_ed25519.pub
  
  # Windows
  type C:\Users\YouFolderName\.ssh\id_ed25519.pub
  ```

- **Alternative Methods to View Public Key Files**: 
Open the .pub file with Notepad or any text editor and copy it,
or you can open this file using the command:
```bash
notepad C:\Users\YouFolderName\.ssh\id_ed25519.pub
```

2. Go to GitHub website:
   - Click your profile photo
   - Go to **Settings > SSH and GPG keys**
   - Click **New SSH key**
   - Paste the public key you copied into the **Key** field and add a name in the **Title** field.
   - Click **Add SSH key**

### Test SSH Connection
```bash
ssh -T git@github.com
```
If successful, you'll see a message like:
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
