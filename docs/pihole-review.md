# Pi-hole: Configuration Review Checklist

## Goal

Review the current Pi-hole setup before making changes. The goal is to understand the existing network configuration, verify that Pi-hole is reachable, and then test DNS behavior safely.

## Step 1 — Identify the device and admin page

- Confirm the Raspberry Pi 4 is powered on and connected to the network.
- Find its current IP address using the router's connected-device list or the Pi's local console.
- Open the Pi-hole admin page using the address you have already configured.
- Record whether the page opens and whether Pi-hole reports any configuration or service warnings.
- Do not share the admin password or authentication token.

## Step 2 — Record current network settings

Before editing settings, record:
- Router/gateway IP address.
- Raspberry Pi's current IP address.
- Whether the Pi address is reserved in the router's DHCP settings or configured statically.
- Which device provides DHCP: router or Pi-hole.
- DNS servers currently configured on the router.
- DNS servers currently configured on the Windows PC.

Do not switch DHCP responsibility as part of this first review.

## Step 3 — Test name resolution from Windows

Open Command Prompt or PowerShell and run:

```powershell
ipconfig /all
nslookup example.com
nslookup pi.lab
```

If you know the Pi-hole IP, query it directly:

```powershell
nslookup example.com <PIHOLE_IP>
nslookup pi.lab <PIHOLE_IP>
```

Replace `<PIHOLE_IP>` with the real address; do not type the angle brackets. Save the results privately and redact sensitive details before publishing them.

Interpretation:
- If the direct query to Pi-hole works but the normal query does not, Windows or router DNS settings may be pointing somewhere else.
- If external names resolve but `pi.lab` does not, the local name may not be defined in the DNS configuration being queried.
- If queries to the Pi-hole IP time out, check network reachability and whether the DNS service is running/listening.
- A successful DNS response does not prove that a web service is running.

## Step 4 — Check the Pi-hole configuration

In the admin interface, inspect (do not immediately change):
- Dashboard/status and any warnings.
- DNS settings and upstream resolver selection.
- Query Log: whether queries from the PC appear.
- Clients: whether devices are identified as expected.
- Local DNS records, if you want names such as `pi.lab` to resolve.
- Whether the router or individual devices are actually using Pi-hole for DNS.

Menu names vary by Pi-hole version. Record your actual version and what you see before following version-specific instructions.

## Step 5 — Change one thing at a time

For each change:
1. Record the original value.
2. Make one change.
3. Save/apply it.
4. Test both a normal public name and the local name you intend to use.
5. Check the Query Log.
6. Revert the change if it causes unexpected network problems.

Keep a fallback DNS configuration and do not publish credentials or tokens. Avoid exposing Pi-hole's admin interface directly to the public internet.

## Results log

| Date | Change or test | Expected result | Actual result | Next action |
|---|---|---|---|---|
| Fill in | Initial review | Establish current state | Not recorded yet | Identify IPs, DNS settings, and Pi-hole version |
