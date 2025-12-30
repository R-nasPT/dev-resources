# Comprehensive Commands and Utilities
## 📑 Table of Contents
- [💻 Git Commands](#-git-commands)
  - [📂 1. Git Areas](#-1-git-areas)
  - [⏪ 2. Resetting to the Previous Commit](#-2-resetting-to-the-previous-commit)
  - [🔄 3. Reverting the Last Commit](#-3-reverting-the-last-commit)
  - [📧 4. Displaying the User's Configured Email](#-4-displaying-the-users-configured-email)
  - [👤 5. Displaying the User's Configured Name](#-5-displaying-the-users-configured-name)
  - [🔐 6. Setting Up SSH Key for GitHub](#-6-setting-up-ssh-key-for-github)
  - [📝 7. How to Write Good Commit Messages](#-7-how-to-write-good-commit-messages)
  - [🔍 8. VS Code Tracking Symbols and Their Meanings](#-8-vs-code-tracking-symbols-and-their-meanings)
  - [🧶 9. Check globally installed packages](#yarn-global)
- [🔧 Utility Commands](#-utility-commands)
  - [🔑 1. Creating a Secret Key](#-1-creating-a-secret-key)

# 💻 Git Commands

## 📂 1. Git Areas

Git organizes files into three main areas:

### Working Directory 
Alternative Names:
- Working Area
- Working Tree
- Workspace

**Description**: This is the area where you actively work on your project files. Here, you can create, edit, and delete files directly. However, files in this area are not yet tracked by Git until they are added to the Staging Area using `git add`.

### Staging Area
Alternative Names:
- Index
- Cache
- Stage

**Description**: This area is where you prepare files to be committed. When you run the command `git add <filename>`, the file moves from the Working Directory to the Staging Area. This allows you to select specific files for commit, helping you control what changes you save in each version.

### Repository 
Alternative Names:
- Repository Area
- Git Repository
- Repo
- .git Directory

**Description**: This is where Git stores the complete history of changes (commits) for the project. When you commit changes using `git commit`, the staged changes are saved into the Repository, which serves as the long-term storage of your project’s version history.

Understanding these Git Areas allows you to better manage project changes and effectively organize code versions!

## ⏪ 2. Resetting to the Previous Commit

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

  **Differences and Commands for the Three Types of Git Reset**

|                      | **Effect on Modified Files**                  | **Action Required for New Commit**            | **Command**                                |
|----------------------|-----------------------------------------------|-----------------------------------------------|--------------------------------------------|
| **Soft Reset**       | Moves files to the Staging Area               | Ready for a new commit immediately            | `git reset --soft <target_commit_id>`      |
| **Mixed Reset (default)** | Moves files to the Working Directory          | Must add files back to the Staging Area       | `git reset --mixed <target_commit_id>`     |
| **Hard Reset**       | Deletes changes permanently                   | Requires redoing all modifications            | `git reset --hard <target_commit_id>`      |


## 🔄 3. Reverting the Last Commit

### Command:
```
git revert HEAD
```

### Description:
- This command creates a new commit that undoes the changes made by the previous commit. Use this when you want to reverse the effects of a commit without altering the commit history.
- Reverting is the process of undoing changes by creating a new commit that mirrors the version prior to the commit being reverted.
- Reverting is safer than resetting because the entire history of changes is preserved.

## 📧 4. Displaying the User's Configured Email

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

## 👤 5. Displaying the User's Configured Name

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
## 🔐 6. Setting Up SSH Key for GitHub
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
## 📝 7. How to Write Good Commit Messages
According to this principle, the Commit Message should be in the format `type(scope?): subject`

### Recommended Extended Format:
```bash
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```
- **`<type>`**  
  Specifies the type of change or the nature of the commit.

- **`(<scope>)`** *(optional)*  
  Specifies the area of the project affected by the change (e.g., `dashboard`, `product-listing`).
  - Use it to clarify the scope of the change.
  - If not needed, it can be omitted.

- **`<description> or Subject`**  
  A short, concise message summarizing the commit. Follow these rules:
  - Summary in present tense (e.g., "fix bug", not "fixed bug").
  - Do not capitalize the first word unnecessarily.
  - Do not end with a period (.).

- **`[optional body]`** *(optional)*  
  This section provides additional context or details about the change. Examples:
  - The motivation or reason behind the change.
  - A comparison with the previous behavior.
  - Explanation of prior behavior and the new behavior
  - Implications or caveats related to the change
  - Details of any conflicts or trade-offs.

- **`[optional footer(s)]`** *(optional)*  
  Used for additional references or metadata, such as:
  - Linking to issue or task IDs (e.g., Closes #123, Fixes JIRA-456)
  - Guidance for testing the changes.
  - Notes about breaking changes, prefixed with **BREAKING CHANGE**.

  **Examples of well-written Commit messages**

  ```bash
  git commit -m "feat: add header section on landing page"
  git commit -m "fix(product-listing): limit display product to 10"
  git commit -m "style: format code with prettier"
  git commit -m "refactor: simplify authentication logic"
  git commit -m "docs: update API documentation"
  git commit -m "chore(package.json): update dependencies to latest version"
  git commit -m "revert: undo migration to v2 endpoints"
  git commit -m "perf(dashboard): decrease loading time on graphs"
  git commit -m "test(payment): ensure checkout function"
  ```
   **Full Conventional Commit Example**
  ```bash
  refactor(api): migrate to v2 endpoints

  BREAKING CHANGE: The old v1 API endpoints have been deprecated and
  replaced with v2. Consumers must update their integrations. 

  Closes #101
  ```
**Details of each "type"**

| **"type"** | **Details** |
| --- | --- |
| feat | Use this to indicate Commits related to adding new features, such as a registration system or profile update system |
| fix | Use this to indicate Commits related to fixing bugs in the code |
| style | Use this to indicate Commits related to improving the appearance of the website |
| docs | Use this to indicate Commits related to writing Documents, such as documents specifying the program's specifications |
| chore | Use this to indicate Commits related to general tasks, such as updating dependencies, configuring settings, or making changes that are not directly related to the code |
| refactor | Use this to indicate Commits related to refactoring, which means rewriting the code in a different way while maintaining the same output |
| revert | Use this to indicate a commit that undoes a previous commit. For example, use this if you need to rollback changes introduced in an earlier commit. |
| perf | Use this to indicate Commits related to improving the performance (efficiency) of the program |
| test | Use this to indicate Commits related to writing tests (test suites) for the program's functionality |
| build | Indicates a commit related to build tools or scripts, e.g., updating build dependencies. |
| ci | Indicates a commit related to configuring Continuous Integration (CI), e.g., GitHub Actions or Jenkins. | 
| deps | for dependencies upgrading or downgrading commit. |
| i18n | Indicates a commit related to internationalization (i18n), e.g., adding translations or multilingual support. |

### Additional options for git commit:
#### 1. Using -m (Message)
1. Prepare the files to be Committed
```bash
git add file1.txt file2.txt    # Add only the specific files you want
git add .                      # Add all modified files
```

2. Perform the Commit
```bash
git commit -m "Explain the changes made"
```

##### How it works:
- Use this when you want to Commit the changes in the files in the Staging Area
- This command will Commit only the files added to the Staging Area using `git add` beforehand

##### When it's appropriate:
- When you want to control which files to Commit
- When you want to separate Commits into distinct sets by feature
- When you have new files that have not yet been Tracked

#### 2. Using -am (Add + Message)
```bash
git commit -am "Explain the changes made"
```
##### How it works:
- Use this when you want to Commit the changes in the Tracked files and you want Git to automatically add those files to the Staging Area
- This command will Commit all the changes in the Tracked files that have been modified, without the need to use `git add`

##### When it's appropriate:
- When you've modified multiple existing files
- When you want to Commit all the modified files together
- When you're confident that all the changes should be in the same Commit

##### Important Considerations
- It does not include new files that have not been Tracked yet
- You should check the file status with `git status` before using this

#### 3. Using --amend

1. Modify only the Commit message
```bash
git commit --amend -m "New Commit message"
```

2. Add a forgotten file to the Commit
```bash
git add forgotten_file.txt
git commit --amend --no-edit    # Use the same Commit message
```

3. Modify both the files and the message
```bash
git add new_changes.txt
git commit --amend -m "New message with additional files"
```

##### When it's appropriate:
- To fix a typo in the Commit message
- To add a file that was forgotten in the same set of changes
- To combine small, related changes into the latest Commit

##### Important Considerations
1. Do not use it for Commits that:
   - Have already been pushed to a Remote
   - Have been pulled by others
   - Are on a Branch shared with others

2. Because --amend will:
   - Change the Commit hash
   - Create a new Git history
   - Potentially cause issues when Merging

### Comparison Table for Commit Options

| Option | Usage | Advantages | Considerations | Example Command |
|----------|----------|-------|-------------|----------------|
| **-m** | Commit files in the Staging Area | - Control which files to Commit<br>- Suitable for separating Commits by feature | - Requires `git add` before every Commit | `git commit -m "Add login system"` |
| **-am** | Commit all Tracked files | - Convenient and fast<br>- No need for `git add` | - May accidentally Commit files you don't want | `git commit -am "Fix login page bug"` |
| **--amend** | Modify the latest Commit | - Fix mistakes<br>- Add forgotten files | - Prohibited for Commits that have been pushed<br>- Changes Git history | `git commit --amend -m "Fix message"` |


## 🔍 8. VS Code Tracking Symbols and Their Meanings

### Summary Table of Key Symbols

| Symbol | Status Name | Meaning | Management |
|-----------|-----------|-----------|------------|
| **U** | Untracked | New files that have never been Tracked | `git add <file>` |
| **M** | Modified | Files that have been modified and not yet Staged | `git add <file>` or `git commit -am` |
| **A** | Added | New files that have been Staged | Ready for Commit |
| **D** | Deleted | Files that have been deleted | `git rm <file>` |
| **R** | Renamed | Files that have been renamed | `git mv <old> <new>` |
| **C** | Copied | Files that have been copied | - |

## 🧶 9. Check globally installed packages with Yarn 1.x (Classic) <a id="yarn-global"></a>
### Command:
```bash
yarn global list
```

This command displays a list of globally installed packages along with their versions, for example:
```bash
yarn global v1.22.19
info "create-next-app@15.5.2" has binaries:
   - create-next-app
info "typescript@4.8.4" has binaries:
   - tsc
   - tsserver
```
### Removing a global package
```bash
yarn global remove <package-name>
```
Example:
```bash
yarn global remove create-next-app
```

---

# 🔧 Utility Commands
## 🔑 1. Creating a Secret Key
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
