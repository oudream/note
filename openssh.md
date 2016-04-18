## 1 ##

## win7 安装 ##
https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
下载 https://www.microsoft.com/en-us/download/details.aspx?id=50395

//Download the latest build. To get links to latest downloads - see here.
//Extract contents to C:\Program Files\OpenSSH-Win32
//Start Powershell as Administrator
cd 'C:\Program Files\OpenSSH-Win32'
//Setup SSH host keys (this will generate all the 'host' keys that sshd expects when its starts)
.\ssh-keygen.exe -A

//Open Firewall
New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName SSH

//If you need key-based authentication, run the following to setup the key-auth package
powershell.exe .\install-sshlsa.ps1
Restart-Computer

//Install and run daemon as NT Service running as Local System
powershell.exe .\install-sshd.ps1
Start-Service sshd

//Make the service start on boot (PowerShell): 
Set-Service sshd -StartupType Automatic



## 使用 ##
https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples
Login With SSH Keys

//Generate a key pair on the client:
ssh-keygen.exe -t rsa -f id_rsa

//Copy id_rsa.pub (client's public key) to corresponding user's directory on ssh HOST
as %systemdrive%\users\user\\.ssh\authorized_keys
//可以用 cat id_rsa.pub >> %systemdrive%\users\user\\.ssh\authorized_keys
//可以用（ mkdir d:\con\         创建     rmdir d:\con\ /s /q   删除 )

//Login using private key
ssh.exe -i .\id_rsa user@host (work group user)
ssh.exe -i .\id_rsa -l user@domain host (domain user)




