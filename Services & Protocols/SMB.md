# SMB

**Ports:** 139, 445

**Quick Checklist**
- [ ] Null session?
- [ ] Signing disabled?
- [ ] Shares accessible?
- [ ] Users enumerable?

```bash
nmap -p 139,445 --script smb-enum-shares,smb-enum-users,smb-security-mode IP
smbclient -L //IP -N
smbmap -H IP
enum4linux -a IP
nxc smb IP -u '' -p '' --shares
rpcclient -U "" -N IP
```
