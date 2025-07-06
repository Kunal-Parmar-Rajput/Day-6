# System Troubleshooting & Networking Cheat‑Sheet

## 1. Safe Mode
### Purpose
* Load Windows with a minimal set of drivers/services so problems caused by third‑party software or drivers don’t interfere.

### When to Use
* BSOD or boot loops after a new driver/app install
* Suspected malware infection
* Driver rollback or uninstall
* Removing stubborn software

### Types of Safe Mode
| Mode | Boot Configuration | Networking | Typical Use‑Case |
| --- | --- | --- | --- |
| **Safe Mode** | Minimal drivers & services | ❌ | Core driver issues, malware clean‑up |
| **Safe Mode with Networking** | Safe Mode + network stack | ✔️ | Download patches/tools while troubleshooting |
| **Safe Mode with Command Prompt** | CLI only | ❌ | Advanced repairs, scripting, DISM/SFC |

### How to Access Safe Mode (Win 10/11)
1. **Settings › System › Recovery › Advanced startup › Restart now**
2. **Shift + Restart** from Start menu > Power > Restart
3. Interrupt boot 3× to launch **WinRE** › *Troubleshoot* › *Advanced options* › *Startup Settings* › *Restart* › Choose option (4–6).

---

## 2. Recovery Tools
* **Windows Recovery Environment (WinRE)** – graphical repair console
* **Startup Repair** – fixes boot files/BCD
* **System Restore** – rolls back system files & registry
* **System Image Recovery** – restore from full image
* **Command Prompt** – manual fix via CLI

### OS Repair Methods
| Method | Tool | Scenario |
| --- | --- | --- |
| **In‑place upgrade** | Windows Setup USB | Corrupted OS but data intact |
| **SFC /scannow** | CMD (admin) | Missing/altered system files |
| **DISM /RestoreHealth** | CMD (admin) | Damaged component store |
| **Reset this PC** | Settings › Recovery | Severe OS problems, keep/delete files |

### Plugins (Add‑ons for WinRE)
* **Microsoft DaRT** – Diagnostics & Recovery Toolset
* **AOMEI Backupper** or **Macrium PE** plug‑ins

---

## 3. Virus & Malware

### Common Symptoms
| Symptom | Likely Cause |
| --- | --- |
| Endless pop‑ups/ads | Adware/PUP |
| CPU/GPU spikes at idle | Crypto‑miner |
| Browser homepage changes | Browser hijacker |
| Unknown processes & services | Trojan/rootkit |
| Files renamed with *.locked* extension | Ransomware |

### Basic Malware Removal Steps
1. Disconnect from internet/LAN.
2. Boot to **Safe Mode with Networking** (download updates only if needed).
3. Update & run trusted scanner (e.g., Windows Defender Offline, Malwarebytes).
4. Quarantine/delete detections.
5. Clear %TEMP% and browser caches.
6. Check startup entries (Task Manager › Startup, `shell:` locations, `msconfig`).
7. Run **SFC** and **DISM** to repair OS files.
8. Patch OS/apps & change passwords once clean.

---

## 4. Storage & Backup

### Where Should You Keep Your Windows Storage?
* **System Drive (C:) on SSD** – OS + apps for speed.
* **Separate Data Partition (D:)** – isolate personal files from OS.
* **External SSD/HDD** – offline backups & system images.

### Various Ways of Backing Up Important Files
| Method | Tool | Frequency | Pros | Cons |
| --- | --- | --- | --- | --- |
| File History | Built‑in | Hourly/Daily | Versioning, auto | Same‑PC risk |
| Cloud Sync | OneDrive, Google Drive | Continuous | Off‑site, easy | Bandwidth, cost |
| System Image | wbAdmin, Macrium | Weekly | Bare‑metal restore | Large size |
| Disk Clone | Macrium, Clonezilla | Monthly | Fast fail‑over | Manual process |
| 3‑2‑1 Rule | — | Strategy | 3 copies, 2 media, 1 off‑site | More planning |

### Summary (OS Troubleshooting)
| Task | Recommended Tool | Notes |
| --- | --- | --- |
| Boot loop fix | Startup Repair | WinRE automatic |
| Replace DLLs | `sfc /scannow` | Run twice if needed |
| Component store repair | `DISM /RestoreHealth` | Needs internet/ISO |
| Driver rollback | Device Manager | Use Safe Mode |

---

## 5. Networking Basics

### RJ45
* 8‑position, 8‑contact modular connector used for Ethernet.
* Locks with a plastic tab; careful not to break it.

### CAT Cable (Ethernet)
| Category | Max Bandwidth | Max Length (1 Gbps) | Shielding |
| --- | --- | --- | --- |
| CAT5e | 1 Gbps | 100 m | UTP/STP |
| CAT6 | 10 Gbps* (37‑55 m) | 100 m @ 1 Gbps | UTP/STP |
| CAT6a | 10 Gbps | 100 m | F/UTP, S/FTP |
| CAT7 | 10 Gbps | 100 m | S/FTP only |

\*10 Gbps over CAT6 limited by alien crosstalk.

### Crimping Tool
* Attaches RJ45 plugs to bulk twisted‑pair cable.
* Ratcheting action ensures full termination.
* Use cable tester after crimping.

#### Networking Summary Table
| Component | Purpose |
| --- | --- |
| RJ45 Plug | Terminate cable ends |
| Keystone Jack | Patch panel/outlet termination |
| Punch‑down Tool | Seat wires into IDC terminals |
| Cable Tester | Validate pinout & continuity |

### T568B Wiring Standard (Straight‑through)
| Pin | Color | Pair | Signal |
| --- | --- | --- | --- |
| 1 | White‑Orange | 2 | TX+ |
| 2 | Orange | 2 | TX‑ |
| 3 | White‑Green | 3 | RX+ |
| 4 | Blue | 1 | — |
| 5 | White‑Blue | 1 | — |
| 6 | Green | 3 | RX‑ |
| 7 | White‑Brown | 4 | — |
| 8 | Brown | 4 | — |

---

## 6. Types of Cables in Networking
| Cable | Medium | Typical Use |
| --- | --- | --- |
| **Twisted Pair (UTP/STP)** | Copper | LAN up to 100 m |
| **Coaxial** | Copper w/ shield | Cable internet, CCTV |
| **Fiber Optic** | Glass/Plastic | Backbone, long‑distance |

![Image](https://github.com/user-attachments/assets/d24730e5-e9fc-4b23-85e6-9797701bcca7)
### Twisted Pair Cable
* Paired conductors twisted to reduce EMI.
* Shielded variants (STP, FTP) for high‑noise areas.

<img width="764" height="532" alt="Image" src="https://github.com/user-attachments/assets/d77d1ed1-d21b-4f27-b295-eb97599cb0d5" />
### Coaxial Cable
* Single copper core + braided shield.
* 75 Ω (RG‑6) for DOCSIS broadband, CCTV.

![Image](https://github.com/user-attachments/assets/e5e5905e-64c8-495f-9f0c-a88f652ec1a3)
### Fiber Optic Cable
* Transmits light—immune to EMI.
* **Single‑mode (OS2)**: 1310/1550 nm lasers, >10 km.
* **Multi‑mode (OM3/OM4)**: 850 nm LEDs, 10 Gbps ≈ 300 m.

---

*Feel free to insert diagrams or images where helpful.*
