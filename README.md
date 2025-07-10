# 📦 Linux File Permissions, Ownership & Users Management Cheat Sheet

---

## 📑 1️⃣ Linux Users & Groups

### 🔹 View existing users

```bash
cat /etc/passwd
```

### 🔹 View existing groups

```bash
cat /etc/group
```

---

## 📑 2️⃣ Create Users and Groups

### 🔸 Create a group

```bash
sudo groupadd developers
```

### 🔸 Create a user and assign to a group

```bash
sudo useradd -m -s /bin/bash -g developers atul
```

* `-m` : create home directory
* `-s /bin/bash` : default shell

### 🔸 Set password for user

```bash
sudo passwd atul
```

### 🔸 Add existing user to a group

```bash
sudo usermod -aG developers atul
```

### 🔸 Check groups of a user

```bash
groups atul
```

---

## 📑 3️⃣ Manage Permissions Like a Pro

### 🔸 View file permissions

```bash
ls -l file.txt
```

**Output Example:**

```bash
-rw-r--r-- 1 atul developers  1024 Jul 10  file.txt
```

**Breakdown:**

* `-` : file
* `rw-` : owner permissions
* `r--` : group permissions
* `r--` : others permissions

---

## 📑 4️⃣ Modify File Permissions

### 🔸 chmod — change permissions

**Symbolic mode:**

```bash
chmod u+x script.sh    # Add execute for owner
chmod g-w file.txt     # Remove write for group
chmod o+r file.txt     # Add read for others
```

**Numeric mode:**

```bash
chmod 755 file.sh
```

**Meaning:**

* 7 = rwx (4+2+1)
* 5 = r-x (4+0+1)
* 5 = r-x (4+0+1)

---

## 📑 5️⃣ Change File Ownership

### 🔸 chown — change file owner

```bash
sudo chown atul file.txt
```

### 🔸 Change owner and group

```bash
sudo chown atul:developers file.txt
```

---

## 📑 6️⃣ Special Permissions: SUID, SGID, Sticky Bit

### 🔸 Set SUID (execute as file owner)

```bash
sudo chmod u+s file.sh
ls -l file.sh
```

**Output:** `-rwsr-xr-x`

---

### 🔸 Set SGID (execute as group owner for directories)

```bash
sudo chmod g+s /opt/mydir
ls -ld /opt/mydir
```

**Output:** `drwxr-sr-x`

---

### 🔸 Set Sticky Bit (restrict delete to file owners in dir)

```bash
sudo chmod +t /tmp/mydir
ls -ld /tmp/mydir
```

**Output:** `drwxrwxrwt`

---

## 📑 7️⃣ Advanced Permissions with FACL (File Access Control Lists)

### 🔸 Install ACL tools (if not installed)

```bash
sudo apt-get install acl         # Ubuntu/Debian
sudo yum install acl             # RHEL/CentOS
```

### 🔸 Enable ACL on directory

```bash
sudo setfacl -m u:atul:rwx file.txt
```

**Meaning:** User `atul` gets `rwx` permissions on `file.txt`

### 🔸 View ACL

```bash
getfacl file.txt
```

### 🔸 Remove ACL for a user

```bash
setfacl -x u:atul file.txt
```

### 🔸 Set default ACL for a directory

```bash
setfacl -d -m u:atul:rw /opt/mydir
```

---

## 📦 Suggested Repo Name:

`linux-permissions-management`

---

## 📜 Bonus: View Effective Permissions for User

```bash
sudo -u atul ls -l file.txt
```

---

## ✅ Done — you now have a clean set of **commands, code, and explanations** to manage:

* Users & Groups
* File Permissions
* Ownership
* Special Permissions (SUID, SGID, Sticky Bit)
* ACL for fine-grained control

---

## 👨‍💻 Author

**Atul Kamble**

- 💼 [LinkedIn](https://www.linkedin.com/in/atuljkamble)
- 🐙 [GitHub](https://github.com/atulkamble)
- 🐦 [X](https://x.com/Atul_Kamble)
- 📷 [Instagram](https://www.instagram.com/atuljkamble)
- 🌐 [Website](https://www.atulkamble.in)
