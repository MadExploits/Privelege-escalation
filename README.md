# Privelege-escalation
Localroot Privelege escalation for linux


`find / -perm -u=s -type f 2>/dev/null` > Exploiting SUID Executables

# Gaining some knowledge of the OS running

```
(cat /proc/version || uname -a ) 2>/dev/null

lsb_release -a 2>/dev/null # old, not by default on many systems

cat /etc/os-release 2>/dev/null # universal on modern systems
```

# Env Info
`(env || set) 2>/dev/null`

<samp>
Tools that could help to search for kernel exploits are:
</samp>

`https://github.com/carlospolop/PEASS-ng, https://github.com/jondonas/linux-exploit-suggester-2, http://www.securitysift.com/download/linuxprivchecker.py`

# Enumerate useful binaries
```
which nmap aws nc ncat netcat nc.traditional wget curl ping gcc g++ make gdb base64 socat python python2 python3 python2.7 python2.6 python3.6 python3.7 perl php ruby xterm doas sudo fetch docker lxc ctr runc rkt kubectl 2>/dev/null
```

# Check if any compiler is installed.
```
(dpkg --list 2>/dev/null | grep "compiler" | grep -v "decompiler\|lib" 2>/dev/null || yum list installed 'gcc*' 2>/dev/null | grep gcc 2>/dev/null; which gcc g++ 2>/dev/null || locate -r "/gcc[0-9\.-]\+$" 2>/dev/null | grep -v "/doc/")
```
# Check User
```
#Info about me
id || (whoami && groups) 2>/dev/null
#List all users
cat /etc/passwd | cut -d: -f1
#List users with console
cat /etc/passwd | grep "sh$"
#List superusers
awk -F: '($3 == "0") {print}' /etc/passwd
#Currently logged users
w
#Login history
last | tail
#Last log of each user
lastlog

#List all users and their groups
for i in $(cut -d":" -f1 /etc/passwd 2>/dev/null);do id $i;done 2>/dev/null | sort
#Current user PGP keys
gpg --list-keys 2>/dev/null
```

<samp>
  Refrence : https://book.hacktricks.xyz/linux-hardening/privilege-escalation
</samp>
