# Home Lab Inventory

## Purpose

This document records the current home-lab environment and separates confirmed behavior from work still needed. Update it as configuration is verified.

## Current status

| Component | Current understanding | Status |
|---|---|---|
| Raspberry Pi 4 | Intended to host Pi-hole and support home-network experiments | Needs configuration review |
| Pi-hole | Present in the project, but DNS settings and overall configuration are not yet understood or verified | Needs review |
| Local dashboard | Opens and works; dashboard features and organization are not yet well understood | Working; learning in progress |
| `pi.lab` local name | Has been part of DNS troubleshooting | Needs testing and verification |
| Roku Express | Personal Roku device used for the Yomi TV project | Available |
| Yomi TV project | Personal Roku learning project; keep it separate from DNS changes unless a tested dependency is documented | In progress |

## Network details to record

Fill these in only after checking the actual devices and router. Do not publish public IP addresses, passwords, API keys, or other secrets.

- Router/gateway IP: `Not recorded yet`
- Raspberry Pi IP address: `Not recorded yet`
- Pi-hole admin page URL: `Not recorded yet`
- Dashboard name/software: `Not identified in this document yet`
- Dashboard URL: `Not recorded yet`
- DNS configured on the router: `Not verified`
- DNS configured on the Windows PC: `Not verified`
- DHCP provided by router or Pi-hole: `Not verified`

## Evidence and verification

For each change, record:
1. What you intended to change.
2. What setting or command you used.
3. The result you observed.
4. How you tested that the result worked.
5. How you would undo the change if it caused a problem.

## Safety notes

- Keep a note of the current router DNS settings before changing them.
- Avoid changing router DHCP and DNS settings simultaneously; make one change at a time.
- Keep a way to restore the previous DNS settings.
- Do not expose the Pi-hole admin interface directly to the public internet.
- Redact passwords, tokens, public IPs, and other sensitive details from screenshots and logs.
