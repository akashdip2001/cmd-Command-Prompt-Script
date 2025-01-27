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
curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd && office_2019_2021.cmd
```

---

### **For PowerShell**
Use the following command in **PowerShell**:
```powershell
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd" -OutFile "office_2019_2021.cmd"; Start-Process -FilePath ".\office_2019_2021.cmd" -Wait
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

---

# ✅ Auto Change Directory to Desktop (recommended)

Automatically change the directory to the Desktop and download the file there before running it:

---

### **For Windows Command Prompt**
Run this command:
```cmd
cd %USERPROFILE%\Desktop && curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd && office_2019_2021.cmd
```

- `%USERPROFILE%\Desktop` ensures you move to the Desktop directory.
- `curl -O` downloads the file to the current directory (Desktop).
- `office_2019_2021.cmd` executes the downloaded file.

---

### **For PowerShell** (✅ recommended)
Use this command:
```powershell
Set-Location -Path "$HOME\Desktop"; Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd" -OutFile "office_2019_2021.cmd"; Start-Process -FilePath ".\office_2019_2021.cmd" -Wait
```

- `Set-Location -Path "$HOME\Desktop"` changes the directory to the Desktop.
- `Invoke-WebRequest` downloads the file.
- `Start-Process` runs the `.cmd` file.

---

### **For Linux/WSL**
If you're running this on Linux or WSL, adjust the path to match your Desktop directory:
```bash
cd ~/Desktop && curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd && chmod +x office_2019_2021.cmd && ./office_2019_2021.cmd
```

---
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

---

# ask for Delet

---

### **For Windows Command Prompt** (⚠️ Not work properly)
```cmd
cd %USERPROFILE%\Desktop
curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd
office_2019_2021.cmd
echo.
set /p deleteFile="Do you want to delete the downloaded file (yes/no)? "
if /i "%deleteFile%"=="yes" del office_2019_2021.cmd
```

---

### **For PowerShell** (✅ recommended)
```powershell
Set-Location -Path "$HOME\Desktop"
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd" -OutFile "office_2019_2021.cmd"
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
curl -O https://raw.githubusercontent.com/akashdip2001/cmd-Command-Prompt-Script/refs/heads/main/office_2019_2021.cmd
chmod +x office_2019_2021.cmd
./office_2019_2021.cmd
read -p "Do you want to delete the downloaded file (yes/no)? " deleteFile
if [ "$deleteFile" = "yes" ]; then
    rm office_2019_2021.cmd
fi
```
