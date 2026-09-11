Yes. Since this is **Windows** and you can't share a screenshot, I can give you **safe commands to inspect your system**. I won't provide malware/exploit code, but I can provide defensive PowerShell commands that help identify what is executing.

 ### 1\. Disconnect first

 Turn off Wi-Fi and unplug Ethernet if possible. **Don't delete suspicious files yet**—preserving them can help determine what happened.

 ### 2\. Open PowerShell as Administrator

 Press **Win + X → Terminal (Admin)** and run:

```
Get-Process | Sort-Object CPU -Descending |
    Select-Object -First 30 Name, Id, CPU, Path
```

 This lists processes using the most CPU and their executable paths.

 Then:

```
Get-CimInstance Win32_Process |
    Select-Object ProcessId, ParentProcessId, Name, ExecutablePath, CommandLine |
    Format-List
```

 This is particularly useful because it can show **which program launched another program and what command line was used**.

 ### 3\. Check programs configured to start automatically

```
Get-CimInstance Win32_StartupCommand |
    Select-Object Name, Command, Location, User |
    Format-List
```

 And check scheduled tasks:

```
Get-ScheduledTask |
    Where-Object {$_.State -ne "Disabled"} |
    Select-Object TaskName, TaskPath, State
```

 ### 4\. Check Windows Defender

```
Get-MpComputerStatus |
    Select-Object AntivirusEnabled, RealTimeProtectionEnabled,
    BehaviorMonitorEnabled, IoavProtectionEnabled
```

 Then start a Defender scan:

```
Start-MpScan -ScanType FullScan
```

 If you strongly suspect an active infection, an **Microsoft Defender Offline scan** is preferable because it scans outside the normal Windows environment:

```
Start-MpWDOScan
```

 Windows will restart, so save anything important first.

 ### Important

 **Don't run commands or code you saw the attacker/malware execute.** If you can remember even a small piece of it—such as a filename, PowerShell 
 
 
 
 ---

 If you mean that **unknown code is actually executing on your computer and you suspect malware**, treat it as a security incident rather than trying to understand the code while it is running.

 ### Do this first

 1. **Disconnect the machine from the internet**
   - Turn off Wi-Fi and unplug Ethernet.
   - Don't log into email, banking, crypto, or other important accounts from that machine.
2. **Don't execute, modify, or “fight” the code yourself.**
   - If it is malicious, interacting with it can make things worse or destroy evidence.
3. **Take a photo/screenshot of what you're seeing** if it is safe to do so.
   - Preserve the exact commands, filenames, error messages, process names, and timestamps.
4. **From a known-clean device**, change important passwords and enable MFA, especially for email and financial accounts.
5. **Run an offline/boot-time malware scan** using your operating system's trusted security tools. If you believe the machine is seriously compromised, the safest remediation is often to **back up only necessary personal documents and perform a clean OS reinstall**, rather than attempting to “make the malware unaffected.”

 ### If you want me to help identify the code

 You can **paste the code here or upload a screenshot/text file of it**. I can explain what it does, identify suspicious behavior, and tell you which parts are likely malicious **without giving instructions for deploying or improving malware**.

 If by “they are talking what I listen” you mean the computer is **speaking aloud or you hear someone through the microphone**, tell me exactly what you are hearing and what operating system you're using (Windows, Linux, or macOS).
 
 command, `.exe`, `.bat`, `.ps1`, or strange URL—type it here exactly as you remember it. I can explain what each part means and help you determine whether it is malicious.
