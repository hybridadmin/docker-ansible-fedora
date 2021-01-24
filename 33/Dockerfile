FROM fedora:33
LABEL maintainer="Tinashe Chikomo <tinashe@chikomo.net>"

ENV container docker

ENV pip_packages "ansible"

# Install requirements.
RUN dnf -y install rpm dnf-plugins-core \
 && dnf -y update \
 && dnf -y install \
      initscripts \
      glibc-langpack-en \
      sudo \
      which \
      hostname \
      libyaml-devel \
      python3 \
      python3-pip \
      python3-pyyaml \
 && dnf clean all

# Install Ansible via Pip.
RUN python3 -m pip install $pip_packages

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

# Install Ansible inventory file.
RUN mkdir -p /etc/ansible
RUN echo -e '[local]\nlocalhost ansible_connection=local' > /etc/ansible/hosts

RUN cd /lib/systemd/system/sysinit.target.wants/; \
    for i in *; do [ $i = systemd-tmpfiles-setup.service ] || rm -f $i; done

RUN rm -f /lib/systemd/system/multi-user.target.wants/* \
    /etc/systemd/system/*.wants/* \
    /lib/systemd/system/local-fs.target.wants/* \
    /lib/systemd/system/sockets.target.wants/*udev* \
    /lib/systemd/system/sockets.target.wants/*initctl* \
    /lib/systemd/system/basic.target.wants/* \
    /lib/systemd/system/anaconda.target.wants/*

VOLUME [ "/sys/fs/cgroup" ]

CMD ["/usr/sbin/init"]
