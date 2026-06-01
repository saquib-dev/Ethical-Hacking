# Lab 2: Firewall Setup

## Goal: Block a port to stop an attack.

## Practice in Kali Linux using `ufw` (Uncomplicated Firewall):

1. **Check Status**: `sudo ufw status`
2. **Allow SSH (so you don't lock yourself out)**: `sudo ufw allow 22`
3. **Enable Firewall**: `sudo ufw enable`
4. **Block a Port (e.g., 80)**: `sudo ufw deny 80`
5. **Verify**: Try to access a website on port 80. It should now be blocked.

## Success Check:
- [ ] Firewall is active.
- [ ] I can allow and deny specific ports.
- [ ] I understand how a firewall reduces the attack surface.
