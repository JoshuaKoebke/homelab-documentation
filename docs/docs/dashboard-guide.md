# Local Dashboard: Getting Oriented

## Current status

The dashboard opens and works. Its software name, version, configured services, and authentication settings still need to be identified before documenting software-specific instructions.

## What a home-lab dashboard usually does

A dashboard is commonly a landing page with links to services on your network. Depending on the software and configuration, it may show bookmarks, service status, widgets, or system information. A link on a dashboard does not necessarily mean the linked service is healthy or reachable.

## First walkthrough

1. Open the dashboard the same way you normally do.
2. Note the exact URL in the browser address bar. Record the local hostname or private IP and port, but do not publish any credentials.
3. Identify the dashboard's name from its page title, logo, footer, or settings/about page.
4. Look for a settings, configuration, edit, or administration area. Do not change settings yet.
5. List the visible tiles/links and what each one opens.
6. Open one link at a time and note whether it loads, asks for sign-in, or returns an error.
7. If the dashboard has widgets, note which are informational and which are links to other applications.
8. Take a screenshot for your private notes, redacting sensitive details before sharing it publicly.

## Suggested service inventory

| Dashboard item | Destination URL/port | Purpose | Verified working? |
|---|---|---|---|
| Pi-hole | Fill in after checking | DNS filtering and query administration, if Pi-hole is the configured service | Not verified here |
| Other service | Fill in | Identify after inspection | Not verified |

## Troubleshooting a tile or link

- If the dashboard itself opens but one tile fails, the dashboard may be fine while the destination service, hostname, port, or network route is wrong.
- If a hostname fails but the same service works by IP address, investigate DNS resolution.
- If the hostname resolves to an IP but the page does not open, check the service, port, firewall, and whether the service is listening.
- Avoid assuming a particular dashboard product or feature until you identify it in the UI.

## What to record next

- Dashboard software name:
- Dashboard version (if visible):
- Dashboard URL (remove sensitive details before publishing):
- Main tiles/links:
- Which tiles work:
- Which tiles fail:
- Settings you want to learn:
