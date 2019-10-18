## Lab 15
To demonstrate use of `VOLUME` instruction.

## Commands
```
docker build -t inderpal2406/nginx-alpine-vol:v0.0.3 .
docker run --name volume -d inderpal2406/nginx-alpine-vol:v0.0.3
docker ps
docker container inspect -f '' volume | grep -i source
cd /var/lib/docker/volumes/da93b0f631edd89fa82fc1b8b8550ec3984a7fc6e5ac321ca41458e9602f6fad/_data
echo "This file is created on local host." > message.txt
docker exec -it volume sh
pwd
ls -l
cd myvol
ls -l
cat message.txt
```

By default, we were placed in `/` directory in container, since we didn't define any `WORKDIR`. There is a directory named `myvol` in root directory of container. We saw our `message.txt` file which was created on local host. When we edited the file on local host, the same changes were reflected in our container.

## df -h output
* df -h on localhost.
```
Filesystem      Size  Used Avail Use% Mounted on
udev            4.8G     0  4.8G   0% /dev
tmpfs           982M   46M  936M   5% /run
/dev/sda1       121G   41G   75G  36% /
tmpfs           4.8G  151M  4.7G   4% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           4.8G     0  4.8G   0% /sys/fs/cgroup
/dev/loop0       90M   90M     0 100% /snap/ultimate-media-downloader2/1
/dev/loop1       90M   90M     0 100% /snap/core/7713
tmpfs           982M   84K  982M   1% /run/user/1000
/dev/loop3       90M   90M     0 100% /snap/core/7917
overlay         121G   41G   75G  36% /var/lib/docker/overlay2/650726a0aeb403ff6e7d7e5d7ac7737743b6436831103e873c3abef5234592dd/merged
```

* df -h in container
```
Filesystem                Size      Used Available Use% Mounted on
overlay                 120.9G     40.6G     74.1G  35% /
tmpfs                    64.0M         0     64.0M   0% /dev
tmpfs                     4.8G         0      4.8G   0% /sys/fs/cgroup
shm                      64.0M         0     64.0M   0% /dev/shm
/dev/sda1               120.9G     40.6G     74.1G  35% /myvol
/dev/sda1               120.9G     40.6G     74.1G  35% /etc/resolv.conf
/dev/sda1               120.9G     40.6G     74.1G  35% /etc/hostname
/dev/sda1               120.9G     40.6G     74.1G  35% /etc/hosts
tmpfs                     4.8G         0      4.8G   0% /proc/acpi
tmpfs                    64.0M         0     64.0M   0% /proc/kcore
tmpfs                    64.0M         0     64.0M   0% /proc/keys
tmpfs                    64.0M         0     64.0M   0% /proc/timer_list
tmpfs                    64.0M         0     64.0M   0% /proc/sched_debug
tmpfs                     4.8G         0      4.8G   0% /proc/scsi
tmpfs                     4.8G         0      4.8G   0% /sys/firmware
```
