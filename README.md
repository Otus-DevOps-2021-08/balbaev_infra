# balbaev_infra
balbaev Infra repository

bastion_IP = 51.250.12.74

someinternalhost_IP = 10.129.0.15

```
ssh -A appuser@10.129.0.15 -J appuser@51.250.12.74
```

# Connect using alias
```
$ cat ~/.ssh/config
HOST someinternalhost
   Hostname 10.129.0.15
   USER appuser
   ProxyJump appuser@51.250.12.74
   ForwardAgent yes
```

```
ssh someinternalhost
```

# cloud-testapp
testapp_IP = 130.193.48.4

testapp_port = 9292

# Create instance and deploy reddit-app
```
yc compute instance create \
  --name reddit-app \
  --hostname reddit-app \
  --memory=4 \
  --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1604-lts,size=10GB \
  --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4 \
  --metadata serial-port-enable=1 \
  --metadata-from-file user-data=metadata.yml
```

# packer-base
- Service account was created
- Packer template has been written
- Variables were moved to a separate json-file
