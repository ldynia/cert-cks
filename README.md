# CKS

CKS preperation notes

# Resources

Links:
* [Udemy](https://www.udemy.com/course/certified-kubernetes-security-specialist/)
* [killer.sh](https://killer.sh/)
* [LFS 260](https://training.linuxfoundation.org/training/kubernetes-security-essentials-lfs260/)


# Setup

**~/.vimrc**

```bash
set paste
set expandtab
set tabstop=2
set shiftwidth=2
```

**Bash**

```bash
# Autocomplete
$ source <(kubectl completion bash)

# Alias 
$ alias k=kubectl

# Shortcuts
$ export kill="--force --grace-period 0"
$ export yaml="--dry-run=client -o yaml"
$ export json="--dry-run=client -o json"
```

# Static Analysis

### [Clair](https://github.com/quay/clair) 

By Red Hat

### [Docker Bench](https://github.com/docker/docker-bench-security) 

*The Docker Bench tool is now a few releases behind CIS and has not been updated since November 2019*

### [Trivy](https://github.com/aquasecurity/trivy)

```bash
$ mkdir /tmp/trivy_cache
$ docker run --rm -v /var/run/docker.sock:/var/run/docker.sock -v /tmp/trivy_cache:/root/.cache/ aquasec/trivy python:3.4-alpine
```

# Dynamic Analysis

A common option is to leverage a dynamic admission controller to insert an initContainer: containing a scan or verification tool into the pod spec. Then the load is distributed across all the workers. Only if the initContainer: scans and has a zero exit code, is the rest of the pod spec passed to the container engine for execution. This is the way that TrendMicro offers some of their cloud security tools.

### [Tracee](https://github.com/aquasecurity/tracee)

TODO figure out how to run it
```bash
$ docker run --name tracee --rm --privileged -v /lib/modules/:/lib/modules/:ro -v /usr/src:/usr/src:ro -v /tmp/tracee:/tmp/tracee aquasec/tracee:latest
```

### [Falco](https://falco.org/docs/)

TODO figure out how to run it

### Seccomp

Linux kernel feature that can be used to restrict the actions available within the container. The seccomp () system call operates on the seccomp state of the calling process and can be used to restrict your application's access.

```yaml
spec:
  securityContext:
    seccompProfile:
      type: Localhost
      localhostProfile: profiles/audit.json
```

### SELinux

[SELinux Guide](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/index)