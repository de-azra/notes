Basic Configuration after Core install

Ctrl+Alt+Del in RDP = Ctrl+Alt+End

Switch from cmd to powershell

PS C:\>sconfig

Change name, Update system, set static IP, set DNS servers (easy mode)

PS commands

Change name

PS C:\>Rename-Computer -NewName <X> -LocalCredential <Y>\Administrator -PassThru
  
Windows Updates

PS C:\>Install-Module PSWindowsUpdate
PS C:\>Get-WindowsUpdate
PS C:\>Install-WindowsUpdate

Set IP

PS C:\>New-NetIPAddress <IP> -interfaceAlias Ethernet0 -DefaultGateway <Gateway> -AddressFamily IPV4 -PrefixLength 24
  
Set DNS

PS C:\>Set-DnsClientServerAddress -InterfaceAlias Ethernet0 -ServerAddresses <DNS Adress>
  
Get Windows Admin Center running

PS C:\Temp\>Invoke-WebRequest 'http://aka.ms/WACDownload' -OutFile <Filename>
PS C:\Temp\>msiexec /i <Filename> /qn /L*v log.txt SME_PORT=<443> SSL_CERTIFICATE_OPTION=generate
