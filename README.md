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
