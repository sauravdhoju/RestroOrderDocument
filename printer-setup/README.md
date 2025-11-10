# POS80 Thermal Printer Setup & Troubleshooting Guide  
**For ZKP POS80 (80mm Thermal Receipt Printer)**

> **Beginner-Friendly Setup**  
> **No Prior Knowledge Needed**  
> **Windows-Focused** (Mac/Linux notes included)  
> **Updated: November 2025**  
> **Source**: Aarambha Solution Troubleshooting Guide  
> **Printer Model**: ZKP8005 / ZKP8008 / ZKP8016 (POS80 Compatible)

---

## Quick Start: Basic Setup (5–10 Minutes)

### Step 1: Unbox & Power On
1. Plug in the **power adapter** to a wall outlet.  
2. Connect the **power cable** to the printer.  
3. Turn ON the printer switch.  
   - **Green light**: Ready!  
   - **Red/Orange light**: Error (see troubleshooting below).  

### Step 2: Load Paper
1. Use **80mm thermal paper roll** (must be thermal – no ink needed!).  
2. Open the printer cover.  
3. Insert roll with **thermal side facing down** (shiny side up).  
4. Pull paper through the front.  
5. Close cover.  

### Step 3: Connect to Computer
Choose **one** connection type:

| Type | Steps |
|------|-------|
| **USB** (Easiest) | Plug USB cable from printer to PC. |
| **Ethernet/LAN** | Plug Ethernet cable to router & printer. |
| **Wi-Fi** | Follow printer manual for setup (or use app). |
| **Bluetooth** | Enable Bluetooth on PC; pair printer. |

### Step 4: Install Driver
1. Go to: [Aarambha Solution Downloads](https://aarambhasolution.com.np/download/)  
2. Download **ZKP8005 Driver** (for POS80):  
   [Direct Link](https://drive.google.com/file/d/1AJuOxNF1pdonY0Hnn_2S9QQE4A0BI9fH/view?usp=sharing)  
3. Run the `.exe` file.  
4. Follow wizard: **Next** → **Install** → **Finish**.  
5. Restart PC if prompted.  

> **Alternative Driver** (if above fails):  
> [POS80 Generic Driver (Nextar)](https://help.nextar.com/tutorial/how-to-install-pos-58-or-pos-80-printer) – Works for most 80mm thermal printers.

### Step 5: Test Print
1. Go to **Settings → Devices → Printers & Scanners**.  
2. Select your printer → **Manage** → **Print a test page**.  
3. If it prints: **Success!**  

---

## Full Troubleshooting Guide  
**Follow in Order – Fixes 90% of Issues**

### 1. Power & Basic Checks
- **No power?**  
  - Check outlet & adapter (try another).  
  - Confirm light: Green = OK, Red = Error.  
- **Self-Test**:  
  1. Turn OFF printer.  
  2. Hold **FEED button** + Turn ON **POWER**.  
  3. If it prints config page: Hardware is fine.  

### 2. Paper Problems
- **Blank/faded print?**  
  - Use **new 80mm thermal roll**.  
  - Clean **print head** with alcohol swab (printer OFF).  
- **Paper jam?**  
  1. Open cover.  
  2. Gently remove paper.  
  3. Restart printer.  
- **Cutter stuck?**  
  1. Turn OFF.  
  2. Remove jam.  
  3. Restart.  

### 3. Connection Fixes
#### USB
- Try different **USB port/cable**.  
- Reinstall driver (Step 4 above).  

#### LAN/Ethernet
- Ensure **cable is secure**.  
- Find printer IP: Print self-test page (has IP).  
- On PC: Open **Command Prompt** (Win+R → `cmd`) → Type `ping [printer IP]` (e.g., `ping 192.168.1.100`).  
  - Reply? Connected! No reply? Check cable/router.  
- Disable **firewall** temporarily (Windows Defender → Allow port 9100).  
- Ensure PC & printer on **same network** (e.g., both 192.168.1.x).  

#### Wi-Fi
- Same as LAN, but check Wi-Fi setup in printer menu.  

#### Bluetooth
- Make printer **discoverable** (hold button per manual).  
- On PC: **Settings → Bluetooth** → Remove old pair → Re-pair.  
- Install Bluetooth driver if needed.  

### 4. Driver & Software Fixes
- **Gibberish print?** Wrong driver or code page.  
  - Reinstall **ESC/POS compatible driver** (from Step 4).  
- **Printer not in list?**  
  - Add manually: **Printers & Scanners → Add a printer**.  
- **POS Software not printing?**  
  - Set correct printer name in POS app.  
- **Mac/Linux?** Use generic ESC/POS drivers (search "CUPS thermal printer driver").  

### 5. Print Spooler Issues (Windows)
**Common: "Error on bill printing" or "Print spooler restart needed"**
1. Clear queue:  
   - **Settings → Devices → Printers** → Select printer → **Open queue** → **Cancel All Documents**.  
2. Restart Spooler:  
   1. Win+R → Type `services.msc`.  
   2. Find **Print Spooler** → Right-click → **Restart**.  
3. Still stuck? Reinstall driver.  

### 6. IP & Network Problems
**Common: "IP change" or device not shown**
- **Check IP conflict**:  
  - Self-test print → Note IP.  
  - On PC: `cmd` → `arp -a` (see if IP used elsewhere).  
- **Set Static IP**:  
  1. On printer menu (or app): Set IP like 192.168.1.50 (match your network).  
  2. Subnet: 255.255.255.0.  
- **DHCP Issue**: Restart router → Re-print self-test for new IP.  
- Test: `ping [IP]` in cmd.  

### 7. Configuration Fixes
- Set as **default printer**: Right-click in Printers list → **Set as default**.  
- In POS app: Select correct printer name.  
- Printer mode: ESC/POS (default for thermal).  
- Update POS software to latest.  

### 8. Hardware Fixes (Advanced – Call Support if Needed)
- **Won't power on?** Faulty adapter/board – replace.  
- **Damaged ports?** Repair USB/LAN.  
- **Overheating?** Let cool 10 mins.  
- **Firmware?** Download from manufacturer (rare).  
- **Worn print head?** Replace (after 50k prints).  

---

## Quick Flowchart (Follow This Order)
1. **Power + Self-Test** → Fails? Hardware fault.  
2. **Paper Check** → Orientation, size, no jam.  
3. **Connection** → USB/LAN/Wi-Fi/Bluetooth fix.  
4. **Driver** → Reinstall/update.  
5. **Spooler** → Restart/clear.  
6. **Network/IP** → Ping + static IP.  
7. **POS Config** → Correct printer set.  

---

## Restro Order POS Software Setup  
**If Using with Restro Order (or Similar POS)**

> **Requires SQL Server + IIS**  
> **For Restaurant Billing**

### Step 1: Install SQL Server 2019 Developer
1. Download: [Microsoft SQL Server 2019](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)  
2. Follow guide: [Visual Expert SQL 2019 Guide](https://www.visual-expert.com/EN/visual-expert-documentation/install-and-configure-visual-expert/sql-server-2019-installation-guide-visual-expert.html)  
   - Choose **Developer Edition**.  
   - Install **Database Engine**.  
   - Mixed Mode authentication.  

### Step 2: Enable IIS (Internet Information Services)
1. Win+R → `optionalfeatures` → Check **Internet Information Services** (all sub-items).  
2. OK → Restart PC.  
3. Open **IIS Manager** (Search: IIS).  
4. Right-click **Sites** → **Add Website**.  
   - Name: `RestroSite`.  
   - Physical Path: Your POS folder (e.g., `C:\RestroOrder`).  
   - Port: 80.  

### Step 3: Check Connection String
1. In IIS → Your site → **Connection Strings**.  
2. Add:  
   - Name: `DefaultConnection`.  
   - Connection String: `Server=localhost;Database=RestroDB;Trusted_Connection=true;`  
     (Replace `localhost` with your SQL server name).  

### Step 4: Install SSMS v20
1. Download: [SQL Server Management Studio v20](https://aka.ms/ssmsfullsetup)  
2. Install → Open.  
3. Connect: Server = `(local)`, Authentication = Windows.  
4. Import Database: Right-click **Databases** → **Restore** → Select `.bak` file from Restro Order provider.  

### Step 5: Install Restro Order Software
- Download from provider (e.g., [RestroPRO on CodeCanyon](https://codecanyon.net/item/restropro-pos-software-for-restaurant-cafe-hotel-food-truck/51779937) – $59).  
- Extract to IIS folder.  
- Configure: Set SQL server/database in `web.config`.  
- Test: Browse `http://localhost/RestroSite`.  

> **Demo**: Email: demo@gmail.com | Pass: demo  

---

## Common Issues & Fixes
| Issue | Fix |
|-------|-----|
| **Device not in list** | Reinstall driver + restart PC. |
| **IP Change** | Set static IP (Step 6). |
| **Driver not found** | Download from Aarambha. |
| **Error on bill print (IIS restart)** | Restart IIS: `iisreset` in cmd. |
| **Need thermal paper** | Buy 80mm rolls (Amazon/eBay). |
| **Ethernet connection** | Check cable + ping. |
| **Driver mismatch** | Use ESC/POS driver. |
| **Print spooler restart** | See Step 5. |

---

## Tips for Beginners
- **Always restart PC/printer** after changes.  
- **Thermal paper only** – regular paper won't work.  
- **Backup settings** before updates.  
- **Mac Users**: Use Parallels VM with Windows.  
- **Need Help?** Contact Aarambha: [aarambhasolution.com.np](https://aarambhasolution.com.np/)  

---

## Useful Links
| Item | Link |
|------|------|
| ZKP Drivers | [Aarambha Downloads](https://aarambhasolution.com.np/download/) |
| POS80 Generic Driver | [Nextar Guide](https://help.nextar.com/tutorial/how-to-install-pos-58-or-pos-80-printer) |
| SQL Server 2019 Guide | [Visual Expert](https://www.visual-expert.com/EN/visual-expert-documentation/install-and-configure-visual-expert/sql-server-2019-installation-guide-visual-expert.html) |
| SSMS Download | [Microsoft SSMS](https://aka.ms/ssmsfullsetup) |
| RestroPRO POS | [CodeCanyon](https://codecanyon.net/item/restropro-pos-software-for-restaurant-cafe-hotel-food-truck/51779937) |
| Thermal Paper | [Amazon 80mm Rolls](https://www.amazon.com/s?k=80mm+thermal+paper) |

---

> **You're Set!** Print a test receipt and start billing.  
> **Star this repo if helpful!** 🚀
