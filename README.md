# Homelab Documentation

A practical, evolving record of my home-lab setup, network services,
troubleshooting, and lessons learned. This repository documents real
configuration and verified results as the lab develops.

## Goals

-   Build and maintain a small home lab using a Raspberry Pi and other
    available devices.
-   Learn DNS, networking, Linux administration, service deployment, and
    troubleshooting.
-   Keep repeatable notes that make changes easier to verify and
    recover.
-   Document completed work separately from planned work.

## Project Status

-   **In progress:** documenting the planned Raspberry Pi 4-based
    Pi-hole DNS setup and local-hostname troubleshooting.
-   **To verify:** whether Pi-hole is installed and configured, which
    DNS address clients should use, and which local services are
    running.
-   **Planned:** add verified configuration details, network diagrams,
    service documentation, and test results as each component is
    configured.

> Documentation rule: do not publish credentials, private keys, or
> unredacted logs containing public IP addresses or other sensitive
> network details. Clearly label assumptions and planned work. Only
> describe a service as working after testing it.

## Documentation

-   [Local DNS Hostname Troubleshooting](docs/dns-troubleshooting.md)

## Lab Inventory

  -----------------------------------------------------------------------
  Component               Device / Role           Status
  ----------------------- ----------------------- -----------------------
  DNS filtering           Raspberry Pi 4 /        Setup status to be
                          Pi-hole                 verified

  Streaming client        Roku Express            Device available

  Local services          Not yet verified        Planned / unconfirmed
  dashboard                                       
  -----------------------------------------------------------------------

## Working Method

For each service, record its purpose, prerequisites, configuration,
verification commands, observed results, troubleshooting steps, and
rollback procedure. Replace example addresses and hostnames with values
verified on the local network before applying them.

## Next Steps

1.  Confirm the Raspberry Pi's current IP address from the device or
    router.
2.  Verify whether Pi-hole is installed and running.
3.  Configure and test the DNS records intended for local hostnames.
4.  Test DNS resolution separately from web-service connectivity.
5.  Add dated notes with actual command output, redacting sensitive
    details.
