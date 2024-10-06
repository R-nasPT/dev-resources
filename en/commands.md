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
  ```
  git config user.email "newemail@example.com"
  ```
- Set the email globally:
  ```
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
  ```
  git config user.name "New Name"
  ```
- Set the username globally:
  ```
  git config --global user.name "New Name"
  ```
---

# Utility Commands
## 1. Creating a Secret Key
### Command:
```
node -e "console.log(require('crypto').randomBytes(256).toString('base64'));"
```
### Description:
This command generates a random 256-byte string encoded in base64, suitable for use as a secret key in your applications. It uses Node.js and the built-in `crypto` module to create a cryptographically strong random key.
### Options:
- To change the key length, modify the number in `randomBytes()`. For example, for a 128-byte key:
  ```
  node -e "console.log(require('crypto').randomBytes(128).toString('base64'));"
  ```
