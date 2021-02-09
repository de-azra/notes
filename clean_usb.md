# In case USB removable devices doesn't cooperate anymore

cmd > as Administrator > diskpart

DISKPART>list disk

DISKPART>select #

DISKPART>clean

DISKPART>create partition primary

DISKPART>format fs=ntfs quick
