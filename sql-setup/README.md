# Microsoft SQL Server 2019 Developer Edition  
**Installation Guide – Step-by-Step (Windows)**

---

## Step 1: Download SQL Server 2019 Developer

1. Go to:  
   [https://www.microsoft.com/en-us/sql-server/sql-server-downloads](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
2. Click **"Download now"** under **Developer**.
3. Save file: `SQL2019-SSEI-Dev.exe` → **Downloads folder**
4. Double-click to run.

---

## Step 2: Choose Installation Type

- Select: **Custom**  
  → Click **Next**

---

## Step 3: Set Media Download Location

- Note:  
  - **Minimum free space**: 891 MB  
  - **Download size**: 1420 MB  
- Click **Install**

---

## Step 4: Open SQL Server Installation Center

1. Wait for **SQL Server Installation Center**  
2. Click **Installation** tab  
3. Select:  
   **New SQL Server stand-alone installation**

---

## Step 5: Confirm Product Key

- Ensure: **Developer** is selected  
- Click **Next**

---

## Step 6: Accept License Terms

- Check: **"I accept the license terms"**  
- Click **Next**

---

## Step 7: Install Setup Files

- Wait for support files  
- Click **Next**

---

## Step 8: Select Features

**Required**:
- **Database Engine Services**

> *Optional (CS779 only)*: Replication, Full-Text Search, etc.

> Default paths are fine (`C:\Program Files\...`)  
> Click **Next**

---

## Step 9: Instance Configuration

- Choose: **Default instance**  
- Instance ID: `MSSQLSERVER`  
- Click **Next**

---

## Step 10: Server Configuration

| Service | Startup Type |
|--------|--------------|
| SQL Server (Database Engine) | **Manual** (recommended) |
| SQL Server Agent | **Manual** |
| SQL Server Browser | **Disabled** |

- **Collation**: Leave default  
  `SQL_Latin1_General_CP1_CI_AS`  
- Click **Next**

---

## Step 11: Database Engine Configuration

1. **Authentication Mode**:  
   Select **Mixed Mode**  
2. **SA Password**:  
   Enter strong password (e.g., `P@ssw0rd123!`)
3. **Add Admin**:  
   Click **Add Current User**  
   → Your Windows account = SQL Admin

> Click **Next**

---

## Step 12: Final Review & Install

- Review summary  
- Click **Install**  
- Wait 5–15 minutes

---

## Step 13: Installation Complete

- See: **"Setup completed successfully"**  
- Click **Close**

**SQL Server is installed!**

---

## Step 14: Download SSMS (Management Studio)

1. Go to:  
   [https://aka.ms/ssmsfullsetup](https://aka.ms/ssmsfullsetup)
2. Download: `SSMS-Setup-ENU.exe`

---

## Step 15: Install SSMS

1. Run the file  
2. Click **Install**  
3. Wait → Click **Close**

**SSMS is ready!**

---

## Step 16: Start SQL Server Service

1. Press `Win + R` → Type: `services.msc`  
2. Find: **SQL Server (MSSQLSERVER)**  
3. Right-click → **Start**

> Optional: Set to **Automatic** for always-on

---

## Step 17: Open SSMS

- Search: **SQL Server Management Studio**  
- or find in Start Menu

---

## Step 18: Connect to Server

| Field | Value |
|------|-------|
| Server type | Database Engine |
| Server name | `.` (dot) or `(local)` |
| Authentication | **Windows Authentication** (preferred)  
| OR | **SQL Server Authentication** → `sa` + password |

→ Click **Connect**

---

## Step 19: Create Your Database

1. In **Object Explorer** (left):  
   Right-click **Databases** → **New Database…**
2. Name: `CS669` (or your choice)  
3. Click **OK**

---

## Step 20: Test Your Database

1. Right-click your database → **New Query**  
2. Type:

```sql
SELECT DB_NAME() AS CurrentDatabase;
