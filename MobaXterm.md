# Windows

1. empty
```PowerShell
Invoke-WebRequest -Uri "https://download.mobatek.net/2342023101450418/MobaXterm_Installer_v23.4.zip" -OutFile "$env:USERPROFILE\Downloads\MobaXterm_Installer_v23.4.zip"
```

2. empty
```PowerShell
Expand-Archive -Path "$env:USERPROFILE\Downloads\MobaXterm_Installer_v23.4.zip" -DestinationPath "$env:USERPROFILE\Downloads\MobaXterm_Installer_v23.4"
```

3. empty
```PowerShell
Start-Process -FilePath "$env:USERPROFILE\Downloads\MobaXterm_Installer_v23.4\MobaXterm_installer_23.4.msi" -Wait
```
