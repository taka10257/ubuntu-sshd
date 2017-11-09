# Ubuntu-sshd-fork

Dockerized SSH service, built on top of [official Ubuntu](https://registry.hub.docker.com/_/ubuntu/) images.

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
$ docker build -t ubuntu_sshd:16.04 ./16.04
$ docker run --rm -d -P --name ubuntu_sample ubuntu_sshd:16.04
$ docker port ubuntu_sample 22
  0.0.0.0:49154

$ ssh-keygen -R [localhost]:49154
$ ssh root@localhost -p 49154
# The password is `root`
root@test_sshd $
```
