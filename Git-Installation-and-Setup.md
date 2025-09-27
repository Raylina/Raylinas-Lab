# 🛠 Git Installation and Setup

This document explains how I installed Git on Windows 11 for use in my **home lab**.  
It includes the choices I made during setup and why they matter.

---

## 🔹 Why Git?
- Git lets me version-control my lab notes and scripts.  
- It integrates with **VS Code** and **GitHub**, so I can sync my local work with my online portfolio.  

---

## 🔹 Installation Steps

### 1. Download Git
- Site: [https://git-scm.com/download/win](https://git-scm.com/download/win)

---

### 2. Setup Screens

#### ✅ Select Components
- ✔ Windows Explorer integration  
- ✔ Git LFS  
- ✔ Add Git Bash Profile to Windows Terminal  
- ❌ Skip auto update checks  
📝 Reason: Integration makes Git easier to access from right-click menus and terminals.

---

#### ✅ Default Editor
- Chose: **Visual Studio Code**  
📝 Reason: Easier than Vim, aligns with my workflow.

---

#### ✅ Initial Branch Name
- Chose: **main**  
📝 Reason: Matches GitHub default branch.

---

#### ✅ PATH Environment
- Chose: **Git from the command line and also from 3rd-party software**  
📝 Reason: Allows Git in PowerShell, CMD, and VS Code.

---

#### ✅ SSH Executable
- Chose: **Bundled OpenSSH**  
📝 Reason: Works out of the box.

---

#### ✅ HTTPS Transport
- Chose: **Windows Secure Channel**  
📝 Reason: Integrates with Windows certificate store.

---

#### ✅ Line Endings
- Chose: **Checkout Windows-style, commit Unix-style line endings**  
📝 Reason: Keeps compatibility across systems.

---

#### ✅ Terminal Emulator
- Chose: **MinTTY**  
📝 Reason: Nicer terminal with better font support.

---

#### ✅ Pull Behavior
- Chose: **Fast-forward or merge**  
📝 Reason: Safer default, keeps history clear.

---

#### ✅ Credential Helper
- Chose: **Git Credential Manager**  
📝 Reason: Saves GitHub login securely.

---

#### ✅ Extra Options
- ✔ Enable file system caching  
- ❌ Skip symbolic links  
📝 Reason: Performance boost, no need for symlinks in this lab.

---

## 🔹 Verification
```powershell
git --version
