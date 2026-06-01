# Lab 2: Testing Your Anonymity

## Goal: Confirm your real IP is hidden.

## Steps:
1. **Check Real IP**: On your main computer, go to `dnsleaktest.com` and note your IP.
2. **Start Kali VM**: Launch your Kali machine.
3. **Check VM IP**: Inside Kali, go to `dnsleaktest.com`.
   - It should be different from your main computer if you are using a VPN/Tor.
4. **Try Tor Browser**: Open Tor Browser in Kali.
5. **Check Tor IP**: Visit `dnsleaktest.com` again. It should be completely different.

## Success Check:
- [ ] Real IP is different from Tor IP.
- [ ] No DNS leaks detected (shown on the website).
