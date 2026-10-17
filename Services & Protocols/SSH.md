# SSH

**Port:** 22

**Quick Checklist**
- [ ] Banner / version?
- [ ] Auth methods?
- [ ] Weak creds?
- [ ] Private key found elsewhere?

```bash
nmap -p 22 -sV --script ssh-auth-methods IP
ssh-audit IP
ssh user@IP
ssh -i id_rsa user@IP
hydra -l user -P rockyou.txt ssh://IP
```

**Port Forwarding**
```bash
ssh -L 8080:127.0.0.1:80 user@IP
ssh -D 1080 user@IP
```
