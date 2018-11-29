# docker

[![Build Status](https://travis-ci.com/iroquoisorg/ansible-role-docker.svg?branch=master)](https://travis-ci.com/iroquoisorg/ansible-role-memcached)

Ansible role for docker

This role was prepared and tested for Ubuntu 16.04.

# Installation

`$ ansible-galaxy install iroquoisorg.docker`

# Default settings

```

# docker-engine is the default package name
docker_pkg_name: docker-engine
docker_apt_cache_valid_time: 1200

# docker dns path for docker.io package ( changed at ubuntu 14.04 from docker to docker.io )
docker_defaults_file_path: /etc/default/docker

# Important if running Ubuntu 12.04-13.10 and ssh on a non-standard port
ssh_port: 22
# Place to get apt repository key
apt_key_url: https://apt.dockerproject.org/gpg
# apt repository key signature
apt_key_sig: F76221572C52609D
# Name of the apt repository for docker
apt_repository: deb https://apt.dockerproject.org/repo ubuntu-{{ ansible_distribution_release }} main
# The following help expose a docker port or to add additional options when
# running docker daemon.  The default is to not use any special options.
#docker_opts: >
#  -H unix://
#  -H tcp://0.0.0.0:2375
#  --log-level=debug
docker_opts: ""
# List of users to be added to 'docker' system group (disabled by default)
# SECURITY WARNING: 
# Be aware that granted users can easily get full root access on the docker host system!
docker_group_members: []
# Flags for whether to install pip packages
pip_install_pip: true
pip_install_setuptools: true
pip_install_docker_py: true
pip_install_docker_compose: true
# Versions for the python packages that are installed
pip_version_pip: latest
pip_version_setuptools: latest
pip_version_docker_py: latest
pip_version_docker_compose: latest

# If this variable is set to true kernel updates and host restarts are permitted.
# Warning: Use with caution in production environments.
kernel_update_and_reboot_permitted: no

# Set to 'yes' or 'true' to enable updates (sets 'latest' in apt module)
update_docker_package: no
# Change these to 'present' if you're running Ubuntu 12.04-13.10 and are fine with less-than-latest packages
kernel_pkg_state: latest
cgroup_lite_pkg_state: latest
# Force an install of the kernel extras, in case you're suffering from some issue related to the
# static binary provided by upstream Docker.  For example, see this GitHub Issue in Docker:
# https://github.com/docker/docker/issues/12750
# Warning: Installing kernel extras is potentially interruptive/destructive and will install backported
# kernel if running 12.04.
install_kernel_extras: false
# Install Xorg packages for backported kernels.  This is usually unnecessary except for environments
# where an X/Unit desktop is actively being used. If you're not using an X/Unity on 12.04, you
# won't need to enable this.
install_xorg_pkgs: false

```
