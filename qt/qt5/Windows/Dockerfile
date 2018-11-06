# Copyright (c) 2018 Accupara Inc. All rights reserved
FROM microsoft/windowsservercore:1803

# $ProgressPreference: https://github.com/PowerShell/PowerShell/issues/2138#issuecomment-251261324
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]
RUN Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1')) ; \
    choco install -y git --params "/GitAndUnixToolsOnPath /NoAutoCrlf"; \
    choco install -y microsoft-build-tools; \
    choco install -y ruby winflexbison python strawberryperl; \
    choco install -y pwsh; \
    choco install -y openssh -params '"/SSHServerFeature /TERM:xterm-new /KeyBasedAuthenticationFeature"'; \
    . 'C:\Program Files\OpenSSH-Win64\Set-SSHDefaultShell.ps1' 'C:\Program Files\Powershell\6\pwsh.exe'; \
    . 'C:\Program Files\OpenSSH-Win64\FixHostFilePermissions.ps1'; \
    . 'C:\Program Files\OpenSSH-Win64\FixUserFilePermissions.ps1'; \
    # Get-ChildItem -Path 'C:\Program Files\OpenSSH-Win64\ssh_host_*_key' | % { \
	#    $acl = get-acl $_.FullName; \
	#    $ar = New-Object  System.Security.AccessControl.FileSystemAccessRule("NT Service\sshd", "Read", "Allow"); \
	#    $acl.SetAccessRule($ar); \
	#    Set-Acl $_.FullName $acl; \
	# }; \
    # New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName SSH; \
    # Set-Service SSHD -StartupType Automatic; \
    # $FilePath = "C:\Program Files\OpenSSH-Win64\sshd_config"; \
    # $FileData = (Get-Content $FilePath).Replace('#PasswordAuthentication yes','PasswordAuthentication yes'); \
    # $FileData += 'Subsystem	powershell C:\Program Files\PowerShell\6.0.0-alpha.18\powershell.exe -sshs -NoLogo -NoProfile'; \
    # $FileData | Out-File $FilePath -Force; \
    Restart-Service sshd;
