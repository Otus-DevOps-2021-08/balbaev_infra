# balbaev_infra
balbaev Infra repository

bastion_IP = 51.250.12.74
someinternalhost_IP = 10.129.0.15
```ssh -A appuser@10.129.0.15 -J appuser@51.250.12.74```

# Connect using alias
```$ cat ~/.ssh/config
HOST someinternalhost
   Hostname 10.129.0.15
   USER appuser
   ProxyJump appuser@51.250.12.74
   ForwardAgent yes```

```ssh someinternalhost```
