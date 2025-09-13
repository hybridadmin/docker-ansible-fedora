# Fedora Docker Images with ansible and systemd

![Build](https://img.shields.io/github/actions/workflow/status/hybridadmin/docker-ansible-fedora/build.yml) ![Docker Pulls](https://img.shields.io/docker/pulls/hybridadmin/ansible-fedora)

> Fedora Docker images to be used for testing ansible playbooks and roles.

## Quick reference

- Maintained by: [hybridadmin](https://github.com/hybridadmin)
- Where to get help: [The Docker Community Forums](https://forums.docker.com/), [Docker Community on Slack](https://dockr.ly/slack) or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)
- Where to file issues: [(issue tracker)](https://github.com/hybridadmin/docker-ansible-fedora/issues) include the `docker` tag
- Supported Arch(s): [(more info)](https://github.com/docker-library/official-images#architectures-other-than-amd64) `amd64`

## Supported tags and respective `Dockerfile` links

- [`42`, `latest`](https://github.com/hybridadmin/docker-ansible-fedora/tree/main/42/Dockerfile)
- [`41`](https://github.com/hybridadmin/docker-ansible-fedora/tree/main/41/Dockerfile)
- [`40`](https://github.com/hybridadmin/docker-ansible-fedora/tree/main/40/Dockerfile)
- [`39`](https://github.com/hybridadmin/docker-ansible-fedora/tree/main/39/Dockerfile)

## How to Build the image

1. Install docker
   - [Linux](https://docs.docker.com/engine/install/)
   - [Windows](https://docs.docker.com/docker-for-windows/install/)
2. Clone the repo `git clone https://github.com/hybridadmin/docker-ansible-fedora.git`
3. `cd` into the directory
4. Run `docker build -t ansible-fedora .`

## How to use this image

Pull the image using the following command:

```console
docker pull hybridadmin/ansible-fedora:latest
```

Run a container using the image with the following command:

```console
docker run -d --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host hybridadmin/ansible-fedora:latest
```

Use ansible inside the container:

```console
docker exec --tty [container_id] env TERM=xterm ansible --version
docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/playbook.yml --syntax-check
```

Connect to the container:

```console
docker exec -it [container_id] /bin/bash
```
