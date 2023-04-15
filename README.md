# Add Additional new disk
## Format disk after you use
```
sudo mkfs.ext4 -m 0 -E lazy_itable_init=0,lazt_journal_init=0,discard /dev/sdb
```

## Create directory for additioanl storage /dev/sdb
```
sudo mkdir -p /var/lib/mariadbsql
```

## Mount /dev/sdb to directory /var/lib/mariadbsql
```
sudo mount -o discard,defaults /dev/sdb /var/lib/mariadbsq
```

## Show mount 
```
df -h
```

## Save configure mount on fstab and get UUID /dev/sdb
```
sudo blkid /dev/sdb
```

## add configure to /etc/fstab
```
UUID=c01d5c09-041d-47ef-93cc-32a5167d2a29 /var/lib/mariadbsql ext4 discard,defaults,nofail 0 2
```
# Increase disk existing

## Update storage after increase disk
```
sudo resize2fs /dev/sdb
```
