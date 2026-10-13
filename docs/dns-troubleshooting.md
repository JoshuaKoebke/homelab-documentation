# DNS Troubleshooting: Local Hostnames

This guide helps diagnose a local hostname such as `pi.lab` when it
fails to resolve or open in a browser.

> **Important:** Record observed results before changing settings. Do
> not assume DNS is the cause until name resolution and connectivity
> have been tested separately.

## 1. Identify the Active DNS Resolver

On Windows, open Command Prompt or PowerShell and run:

``` powershell
ipconfig /all
nslookup pi.lab
```

Check the active network adapter's **DNS Servers** in `ipconfig /all`.
In the `nslookup` output, note which server answered and whether the
result contains an address, `NXDOMAIN` / `Non-existent domain`, or a
timeout.

-   If the server is not the intended Pi-hole address, check the adapter
    configuration, DHCP-provided DNS, VPN settings, and any manually
    configured DNS-over-HTTPS or security software.
-   If the intended DNS server answers `NXDOMAIN`, verify that the
    hostname exists in the DNS server's local records and that the
    client is querying the correct server.
-   If the query times out, check connectivity to the DNS server and
    whether DNS traffic is allowed.

A public resolver answering the query tells you which resolver was used;
it does not, by itself, identify why the client selected it.

## 2. Verify the Hostname Record

Confirm the Raspberry Pi's current IP address from the Pi itself or the
router's DHCP lease list. Then query the intended DNS server explicitly:

``` powershell
nslookup pi.lab <PIHOLE_IP>
```

Replace `<PIHOLE_IP>` with the Pi-hole server's actual address. Do not
copy an example IPv6 address without verifying that it belongs to your
device and is still valid.

If Pi-hole is intended to provide the record, confirm the local DNS
record is configured in Pi-hole and that clients use Pi-hole for DNS.
Menu names may vary by Pi-hole version.

## 3. Separate DNS Failure from Web-Service Failure

If the name resolves, test whether the web service can be reached. For
an HTTP dashboard:

``` powershell
Test-NetConnection pi.lab -Port 80
```

If the dashboard uses HTTPS, test port 443 instead. Use the actual port
configured for the service.

-   **Name does not resolve:** investigate DNS records and client
    resolver settings.
-   **Name resolves but TCP connection fails:** investigate the target
    IP, routing, firewall, service status, listening port, and whether
    the service accepts connections.
-   **TCP connection succeeds but the browser shows an application
    error:** investigate the web server, reverse proxy, and application
    logs.

A connection refusal is not normally fixed by changing DNS alone.

## 4. Hosts-File Override (Temporary Diagnostic Option)

A hosts-file entry can map a hostname to a known IP address on one
computer. It is a local override, not a repair for Pi-hole or
network-wide DNS.

On Windows, the file is:

``` text
C:\Windows\System32\drivers\etc\hosts
```

Edit it with administrator privileges and add a line only after
confirming the correct address. For example:

``` text
192.168.1.50 pi.lab
```

Replace `192.168.1.50` with the Pi's verified address. This is only an
example; do not use it without checking your network. Remove the
override after testing if it is no longer needed.

**Note:** `nslookup` queries DNS directly and generally does not consult
the hosts file. Use `ping pi.lab` or an application-level test to check
whether the operating system resolves a hosts-file entry. A ping failure
alone does not prove name resolution failed.

## 5. Browser Checks

A private/incognito window can help rule out some browser state, but it
does not repair DNS, routing, or service availability. Test the intended
URL and port, such as `http://pi.lab/`, only after confirming the
hostname and service are configured.

Do not assume that `pi.lab` opens a dashboard unless a dashboard has
actually been installed, configured, and tested.

## Troubleshooting Record

Record the following when investigating an incident:

-   Date/time:
-   Client device and network connection:
-   DNS server shown by `ipconfig /all`:
-   Output of `nslookup pi.lab`:
-   Result of `nslookup pi.lab <PIHOLE_IP>`:
-   Resolved address:
-   TCP port tested and result:
-   Service status / relevant logs:
-   Change made:
-   Verification after the change:

Redact public IP addresses, sensitive hostnames, credentials, and other
private details before publishing logs.
