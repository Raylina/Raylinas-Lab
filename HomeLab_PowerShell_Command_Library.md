# Home Lab Command Library

_A living notebook for PowerShell and CLI commands. Add new commands as you learn. Use code fences for commands and brief explanations._

---

## How to Use This Library
- Create a new section when a topic grows (System, Networking, Storage, Virtualization, Security).
- For each command, add: **What it does**, **Command**, **Expected output (short)**, and **Notes**.
- Run PowerShell as Administrator when needed (right‑click → **Run as administrator**).

---

## System (Basics)

### Check OS Architecture (32‑bit or 64‑bit)
**What it does:** Shows whether Windows is 32‑bit or 64‑bit.
```powershell
Get-CimInstance Win32_OperatingSystem | Select-Object OSArchitecture
```
**Expected output:** `64-bit` or `32-bit`

### Check Total RAM (GB)
**What it does:** Shows installed physical memory.
```powershell
(Get-CimInstance Win32_ComputerSystem).TotalPhysicalMemory / 1GB
```
**Notes:** Result is a decimal number (e.g., `15.75`).

### Check Free Disk Space (per drive)
**What it does:** Lists drives and free space in GB.
```powershell
Get-CimInstance Win32_LogicalDisk -Filter "DriveType=3" |
Select-Object DeviceID, @{Name="FreeSpaceGB";Expression={[math]::Round($_.FreeSpace/1GB,2)}}
```
**Notes:** Aim for 100+ GB free for multiple VMs.

### CPU Model & Core Count
**What it does:** Quick CPU overview.
```powershell
Get-CimInstance Win32_Processor | Select-Object Name, NumberOfCores, NumberOfLogicalProcessors
```

---

## Networking

### Show Network Adapters (status)
**What it does:** Lists adapters and if they’re up.
```powershell
Get-NetAdapter | Select-Object Name, Status, LinkSpeed
```

### Test Port Connectivity (like `nc`)
**What it does:** Checks if a host:port is reachable.
```powershell
Test-NetConnection google.com -Port 443
```
**Expected output:** `TcpTestSucceeded : True` when reachable.

### IP & DNS Details (CMD utility)
**What it does:** Full IP configuration (runs cmd from PowerShell).
```powershell
ipconfig /all
```

---

## Storage

### List Volumes
**What it does:** Shows drive letters, sizes, and health.
```powershell
Get-Volume | Select-Object DriveLetter, FileSystemLabel, Size, SizeRemaining, HealthStatus
```

### Physical Disks
**What it does:** See physical disk info.
```powershell
Get-PhysicalDisk | Select-Object FriendlyName, Size, MediaType, HealthStatus
```

---

## Virtualization Readiness (Host)

### Check if Virtualization is Enabled
**What it does:** Verifies Hyper‑V requirements on Windows.
```powershell
systeminfo | Select-String "Hyper-V Requirements"
```
**Notes:** Look for `Virtualization Enabled In Firmware: Yes`.

### List Optional Windows Features (Hyper‑V components)
**What it does:** Shows optional features and state.
```powershell
Get-WindowsOptionalFeature -Online | Where-Object {$_.FeatureName -like "*Hyper-V*"}
```

---

## Template (Copy/Paste for New Entries)
**Title:** Short description here  
**What it does:** One‑line summary.  
**Command:**
```powershell
# paste command here
```
**Expected output:** What success looks like.  
**Notes:** Flags, paths, or risks to remember.

---

## Tips
- Use triple backticks for code blocks: ```powershell … ```
- Group related commands into `.ps1` scripts when you repeat tasks.
- Consider installing VS Code with **Markdown All in One** and **PowerShell** extensions for preview and syntax highlighting.
