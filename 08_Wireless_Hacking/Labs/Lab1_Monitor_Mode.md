# Lab 1: Putting your Card in Monitor Mode

## Goal: Prepare your wireless card for sniffing.

## Requirement: A WiFi adapter that supports Monitor Mode.

## Steps:
1. **Identify your card**: `iwconfig` (Usually `wlan0`).
2. **Kill conflicting processes**: `sudo airmon-ng check kill`
3. **Enable Monitor Mode**: `sudo airmon-ng start wlan0`
4. **Verify**: Run `iwconfig` again. Your card should now be called `wlan0mon`.
5. **Stop Monitor Mode**: `sudo airmon-ng stop wlan0mon`

## Success Check:
- [ ] Card successfully entered monitor mode.
- [ ] Understand why `airmon-ng check kill` is necessary.
