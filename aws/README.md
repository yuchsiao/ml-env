# AWS Operations

# [Mount EBS](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html)

Print volume devices

```
lsblk
```

Determine if creating a file system is needed

```
file -s /dev/xvdf
```

Create a file system in `ext4` format

```
mkfs -t ext4 device_name
```

Make a directory for mounting, say, `/data`

```
mkdir /data
```

Mount the volume

```
mount device_name mount_point
```

Backup `fstab`

```
cp /etc/fstab /etc/fstab.orig
```

