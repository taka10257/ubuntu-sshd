# Ubuntu-sshd-fork

Dockerized SSH service, built on top of [official Ubuntu](https://registry.hub.docker.com/_/ubuntu/) images.

## 注意事項
 - 16.04しかメンテしてません

## reference
 - https://github.com/rastasheep/ubuntu-sshd

## Config

  - `PermitRootLogin yes`
  - `UsePAM no`
  - exposed port 22
  - default command: `/usr/sbin/sshd -D`
  - root password: `root`

## Run example

```bash
# create image
docker build -t ubuntu_sshd:16.04 ./16.04
```

```bash
# create container
docker run -d -P --name ubuntu_sample -p 2323:22 -p 3010:80 ubuntu_sshd:16.04
#docker run --rm -d -P --name ubuntu_sample -p 2323:22 -p 3010:80 ubuntu_sshd:16.04
docker port ubuntu_sample 22
  0.0.0.0:2323
```

```bash
# remove known_hosts
# sed -i '/localhost/d' ~/.ssh/known_hosts
ssh-keygen -R [localhost]:2323
```

```bash
# ssh access
ssh root@localhost -p 2323
# The password is `root`
root@test_sshd $
```
