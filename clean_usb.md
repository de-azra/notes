# In case USB removable devices don't cooperate anymore

cmd > as Administrator > diskpart

DISKPART>list disk

DISKPART>select #

DISKPART>clean

DISKPART>create partition primary

DISKPART>format fs=ntfs quick

# Diskpart to create bootable Windows Installation media

powershell > as Administrator > diskpart

DISKPART>list disk

DISKPART>select #

DISKPART>clean

DISKPART>create partition primary

DISKPART>select partition 1

DISKPART>active

DISKPART>format fs=exfat quick label="WinX"

DISKPART>exit

C:\>bootsect /nt60 X: *USB Stick drive letter*

C:\>xcopy Y:\*.* X:\ /E /H /F *Mounted ISO drive letter / USB Stick drive letter*
