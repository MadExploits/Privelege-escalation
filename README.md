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

`https://github.com/carlospolop/PEASS-ng/`
