<details>
  <summary style="opacity: 0.85;"><b>know more - Manually Change Directory</b></summary><br>

# Manually Change Directory
   
### Temporary turn 0ff windows defender

![Screenshot (56)](https://github.com/user-attachments/assets/428bba0f-162f-4ac5-8dae-4081edf9e4f9)

## cd Desktop (any known /Dir)
### Run in CMD or PowerShell

![Screenshot (59)](https://github.com/user-attachments/assets/242a6504-5768-465e-b2f3-2169fd18382f)
![Screenshot (58)](https://github.com/user-attachments/assets/4bb027f4-6530-4804-8493-fe798f5e9904)

To run your `.cmd` file directly using the provided raw GitHub URL (`https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd`), follow these steps:

---

### **For Windows Command Prompt**
Run the following command in **Command Prompt**:
```cmd
curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd && office_2019_2021.cmd
```

---

### **For PowerShell**
Use the following command in **PowerShell**:
```powershell
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd" -OutFile "office_2019_2021.cmd"; Start-Process -FilePath ".\office_2019_2021.cmd" -Wait
```

---

### **For Linux/WSL**
If you're running this in a Linux or WSL environment:
1. Grant execution permission:
   ```bash
   chmod +x office_2019_2021.cmd
   ```
2. Run the script:
   ```bash
   ./office_2019_2021.cmd
   ```
   
---
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

</details>

<details>
  <summary style="opacity: 0.85;"><b>know more - Auto Change Directory to Desktop</b></summary><br>

# ✅ Auto Change Directory to Desktop (recommended)

Automatically change the directory to the Desktop and download the file there before running it:

---

### **For Windows Command Prompt**
Run this command:
```cmd
cd %USERPROFILE%\Desktop && curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd && office_2019_2021.cmd
```

- `%USERPROFILE%\Desktop` ensures you move to the Desktop directory.
- `curl -O` downloads the file to the current directory (Desktop).
- `office_2019_2021.cmd` executes the downloaded file.

---

### **For PowerShell** (✅ recommended)
Use this command:
```powershell
Set-Location -Path "$HOME\Desktop"; Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd" -OutFile "office_2019_2021.cmd"; Start-Process -FilePath ".\office_2019_2021.cmd" -Wait
```

- `Set-Location -Path "$HOME\Desktop"` changes the directory to the Desktop.
- `Invoke-WebRequest` downloads the file.
- `Start-Process` runs the `.cmd` file.

---

### **For Linux/WSL**
If you're running this on Linux or WSL, adjust the path to match your Desktop directory:
```bash
cd ~/Desktop && curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd && chmod +x office_2019_2021.cmd && ./office_2019_2021.cmd
```

---
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

</details>

<details>
  <summary style="opacity: 0.85;"><b>know more - Ask for Delete</b></summary><br>

# Ask for Delete

---

### **For Windows Command Prompt** (⚠️ Not work properly)
```cmd
cd %USERPROFILE%\Desktop
curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd
office_2019_2021.cmd
echo.
set /p deleteFile="Do you want to delete the downloaded file (yes/no)? "
if /i "%deleteFile%"=="yes" del office_2019_2021.cmd
```

---

### **For PowerShell** (✅ recommended)
```powershell
Set-Location -Path "$HOME\Desktop"
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd" -OutFile "office_2019_2021.cmd"
Start-Process -FilePath ".\office_2019_2021.cmd" -Wait
$deleteFile = Read-Host "Do you want to delete the downloaded file (yes/no)?"
if ($deleteFile -eq "yes") {
    Remove-Item -Path "office_2019_2021.cmd" -Force
}
```

---

### **For Linux/WSL**
```bash
cd ~/Desktop
curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd
chmod +x office_2019_2021.cmd
./office_2019_2021.cmd
read -p "Do you want to delete the downloaded file (yes/no)? " deleteFile
if [ "$deleteFile" = "yes" ]; then
    rm office_2019_2021.cmd
fi
```
</details>

---

# with Error Handelling (✅ Use it)

![Screenshot (61)](https://github.com/user-attachments/assets/e9a7b088-0538-472b-b473-26247cb7d154)

- ⚠️ Temporary turn 0ff windows defender (Real Time)
- ✅ Auto Download to Desktop
- ✅ Auto Run
- ✅ Ask for Delete --> say "Yes"

```powershell
# Navigate to the Desktop
Set-Location -Path "$HOME\Desktop"

# Download the file
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd" -OutFile "office_2019_2021.cmd"

# Run the file
Start-Process -FilePath ".\office_2019_2021.cmd" -Wait

# Ask the user if they want to delete the file
$deleteFile = Read-Host "Do you want to delete the downloaded file (yes/no)?"

# Handle the user's response
if ($deleteFile -eq "yes") {
    # Ensure the file exists before attempting to delete
    if (Test-Path -Path "office_2019_2021.cmd") {
        Remove-Item -Path "office_2019_2021.cmd" -Force
        Write-Host "File deleted successfully."
    } else {
        Write-Host "File not found. Nothing to delete."
    }
} else {
    Write-Host "File was not deleted."
}
```

![Screenshot (60)](https://github.com/user-attachments/assets/093c14ec-5d46-40b8-9483-3064382d4aae)
![Screenshot (62)](https://github.com/user-attachments/assets/f07f1004-16bc-4686-8fb1-07691dfec660)


---
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

<details>
  <summary style="opacity: 0.85;"><b>know more - Auto PowerShell Script to Disable Entire Windows Defender, Run the Script, and Re-enable Defender</b></summary><br>

# Auto PowerShell Script to Disable Entire Windows Defender, Run the Script, and Re-enable Defender

![Screenshot (63)](https://github.com/user-attachments/assets/34b97edb-9005-48a2-8b16-4933425bc09d)

Completely disable Windows Defender (including real-time protection) and then re-enable it after the script runs in PowerShell

### PowerShell Script to Disable Entire Windows Defender, Run the Script, and Re-enable Defender

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; 
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script-office-2019-2021/refs/heads/main/office_2019_2021.cmd" -OutFile "$env:USERPROFILE\Desktop\office_2019_2021.cmd"; 
Set-Location -Path "$env:USERPROFILE\Desktop"; 

# Function to completely disable Windows Defender
function Disable-WindowsDefender {
    Write-Host "Disabling Windows Defender..." -ForegroundColor Yellow
    Set-MpPreference -DisableRealtimeMonitoring $true
    Set-MpPreference -DisableBehaviorMonitoring $true
    Set-MpPreference -DisableBlockAtFirstSeen $true
    Set-MpPreference -DisableIOAVProtection $true
    Set-MpPreference -DisablePrivacyMode $true
    Write-Host "Windows Defender has been disabled." -ForegroundColor Green
}

# Disable Windows Defender
Disable-WindowsDefender

# Run the script
Start-Process -FilePath "$env:USERPROFILE\Desktop\office_2019_2021.cmd" -Wait

# Ask for deletion
$deleteFile = Read-Host "Do you want to delete the downloaded file (yes/no)?"
if ($deleteFile -eq "yes") {
    Remove-Item -Path "$env:USERPROFILE\Desktop\office_2019_2021.cmd" -Force
    Write-Host "File deleted successfully." -ForegroundColor Green
}

# Function to re-enable Windows Defender
function Enable-WindowsDefender {
    Write-Host "Enabling Windows Defender..." -ForegroundColor Yellow
    Set-MpPreference -DisableRealtimeMonitoring $false
    Set-MpPreference -DisableBehaviorMonitoring $false
    Set-MpPreference -DisableBlockAtFirstSeen $false
    Set-MpPreference -DisableIOAVProtection $false
    Set-MpPreference -DisablePrivacyMode $false
    Write-Host "Windows Defender has been re-enabled." -ForegroundColor Green
}

# Re-enable Windows Defender
Enable-WindowsDefender
```

### Steps to Execute:
1. **Open PowerShell as Administrator** on the target PC.
2. Paste the entire script into the PowerShell window and press **Enter**.

### What This Script Does:
1. **Disables Windows Defender**:
   - Disables **Real-Time Monitoring**, **Behavior Monitoring**, **Block at First Seen**, **IOAV Protection**, and **Privacy Mode**.
2. **Downloads and Executes the File**:
   - Downloads the `.cmd` script from your GitHub repository.
   - Executes the script.
3. **File Deletion**:
   - Prompts the user to delete the file after execution.
4. **Re-enables Windows Defender**:
   - Re-enables all the features of Windows Defender that were previously disabled.

---

### Troubleshooting Tips:
1. **Windows Defender Blocking the File**: If Windows Defender still blocks the script, you may need to temporarily disable it through the **Windows Security Settings** manually or add an exclusion for the file/folder you're working with.
2. **File Being Marked as a Virus**: If your `.cmd` file is being flagged, you can:
   - **Submit the file** to Windows Defender as a false positive.
   - Use an **external antivirus tool** to check the file if you're sure it is safe.
   
---

</details>
