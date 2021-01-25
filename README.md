# Fedora Docker Images with ansible and systemd

> Fedora Docker images to be used for testing ansible playbooks and roles.

## Supported tags and respective `Dockerfile` links

- [`latest`, `33`](https://github.com/hybridadmin/docker-ansible-fedora/tree/main/33/Dockerfile)
- [`32`](https://github.com/hybridadmin/docker-ansible-fedora/tree/main/32/Dockerfile)

## How to Build the image

1. Install docker
   * [Linux](https://docs.docker.com/engine/install/)
   * [Windows](https://docs.docker.com/docker-for-windows/install/)
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
docker run -d --name systemd-fedora --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro hybridadmin/ansible-fedora:latest
```

Use Ansible inside the container:
```console
docker exec --tty [container_id] env TERM=xterm ansible --version
docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check
```

## Author

Created by Hybridadmin
