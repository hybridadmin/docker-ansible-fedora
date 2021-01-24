# Fedora Docker Images with ansible and systemd

> Fedora Docker images to be used for testing ansible playbooks and roles.

## Supported tags and respective `Dockerfile` links

- [`latest`, `33` (*33/Dockerfile*)](https://github.com/hybridadmin/docker-fedora-ansible/tree/main/33/Dockerfile)
- [`32` (*32/Dockerfile*)](https://github.com/hybridadmin/docker-fedora-ansible/tree/main/32/Dockerfile)

## How to Build the image

1. Install docker
   * [Linux](https://docs.docker.com/engine/install/)
   * [Windows](https://docs.docker.com/docker-for-windows/install/)
2. Clone the repo `git clone https://github.com/hybridadmin/docker-fedora-ansible.git`
3. `cd` into the directory
4. Run `docker build -t fedora-ansible .`

## How to use this image

Pull the image using the following command:
```console
docker pull hybridadmin/fedora-ansible:latest
```

Run a container using the image with the following command:
```console
docker run -d --name systemd-fedora --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro hybridadmin/fedora-ansible:latest
```

Use Ansible inside the container:
```console
docker exec --tty [container_id] env TERM=xterm ansible --version
docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check
```

## Author

Created by Hybridadmin
