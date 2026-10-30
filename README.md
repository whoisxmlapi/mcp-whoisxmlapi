<p align="center">
  <img src="assets/logo-400x400.png" alt="WhoisXML API" width="120" />
</p>

# WhoisXML API MCP Server

The official [WhoisXML API](https://www.whoisxmlapi.com) MCP server: **35 first-party tools** for WHOIS, DNS, IP geolocation, threat intelligence, typosquatting, email verification, and native bulk lookups — in Claude, Cursor, VS Code, LobeChat, or any MCP client.

- **Documentation:** <https://mcp.whoisxmlapi.com>
- **npm package:** [`@whoisxmlapidotcom/mcp-whoisxmlapi`](https://www.npmjs.com/package/@whoisxmlapidotcom/mcp-whoisxmlapi)
- **Docker image:** [`whoisxmlapidotcom/mcp-whoisxmlapi`](https://hub.docker.com/r/whoisxmlapidotcom/mcp-whoisxmlapi)
- **MCP Registry:** `io.github.whois-api-llc/mcp-whoisxmlapi`

> This repository is the public listing home for the server. Distribution is via the hosted endpoint, npm, and Docker Hub; the implementation source is maintained privately by Whois API, Inc.

## Hosted endpoint (no install)

Connect any remote-capable MCP client to the hosted server — authentication is via OAuth with your WhoisXML API key:

```
https://mcp-hosted.whoisxmlapi.com/mcp
```

```json
{
  "mcpServers": {
    "whoisxmlapi": {
      "url": "https://mcp-hosted.whoisxmlapi.com/mcp"
    }
  }
}
```

## Run locally

Requires a WhoisXML API key — get one at <https://whoisxmlapi.com>.

**npm:**

```json
{
  "mcpServers": {
    "whoisxmlapi": {
      "command": "npx",
      "args": ["-y", "@whoisxmlapidotcom/mcp-whoisxmlapi"],
      "env": { "WHOISXMLAPI_TOKEN": "at_YOUR_KEY" }
    }
  }
}
```

**Docker:**

```bash
docker run -i --rm -e WHOISXMLAPI_TOKEN=at_YOUR_KEY whoisxmlapidotcom/mcp-whoisxmlapi
```

## Tools (35)

### Domain intelligence

| Tool | What it does |
|---|---|
| `whois` | Current WHOIS/RDAP registration data for a domain — registrar, dates, nameservers, status, contacts. |
| `whois_history` | Full timeline of WHOIS changes — ownership transfers, registrar moves, nameserver swaps. |
| `domain_info` | Enriched WHOIS profile combining current + historical records to fill redacted fields. |
| `reverse_whois` | Every domain whose WHOIS record contains a free-text term (name, email, org, address). |
| `reverse_whois_advanced` | Field-specific WHOIS searches (e.g. `RegistrantContact.Organization`), up to 4 terms. |
| `domain_reputation` | 0–100 trust score from live infrastructure and configuration checks. |
| `typosquatting` | Check whether a domain belongs to a typosquatting group, or expand the full group. |
| `categorization` | Classify a domain into IAB Content Taxonomy v3.1 categories. |

### DNS & infrastructure

| Tool | What it does |
|---|---|
| `dns_lookup` | Current DNS records — A, AAAA, MX, NS, SOA, TXT, CNAME, PTR, SRV, CAA, DS, DNSKEY, or all. |
| `dns_history` | Historical DNS records (forward) or domains historically on an IP (reverse). |
| `reverse_dns` | Search DNS records by pattern and return matching domains. |
| `reverse_ip` | Every domain currently pointing at an IP, with first-/last-seen dates. |
| `reverse_mx` | Every domain using a specific MX server. |
| `reverse_ns` | Every domain delegated to a specific nameserver. |
| `subdomain_lookup` | Enumerate a domain's known subdomains with seen timestamps, paging past the 10,000-per-request cap. |
| `domain_and_subdomain_discovery` | Domains/subdomains of any age containing search terms (wildcards supported; `since` filters by first-seen date). |
| `ssl_certificates` | TLS certificate details — issuer, validity, SANs, chain trust. |

### IP intelligence

| Tool | What it does |
|---|---|
| `ipgeolocation` | Country, region, city, ISP, ASN for an IP, domain, or email. |
| `ip_netblocks` | CIDR ranges, ASN, organisation, and each block's last-modified date for IP/ASN/org. |
| `vpn_proxy_detection` | Whether an IP is a known VPN, proxy, Tor exit, relay, hosting or CDN address, with a 0–100 risk score. |

### Threat & brand protection

| Tool | What it does |
|---|---|
| `threat_intelligence` | Check a domain, URL, IP, CIDR, or file hash against malware/phishing/spam/botnet feeds. |
| `brand_alert` | Newly added/dropped/updated domains containing brand terms — typosquat & lookalike monitoring. |
| `registrant_alert` | New/changed domains whose WHOIS registrant fields match search terms. |

### Email

| Tool | What it does |
|---|---|
| `email_verification` | Syntax, MX, and SMTP deliverability checks; flags disposable/role/free/catch-all. |
| `disposable_email_check` | Boolean verdict on disposable/temporary email providers. |

### Screenshots

| Tool | What it does |
|---|---|
| `website_screenshot` | Capture a web page screenshot, returned as a native image content block. |

### Bulk

| Tool | What it does |
|---|---|
| `bulk_whois` | WHOIS for up to 10,000 domains in one call (native bulk, async `job_id` if long-running). |
| `bulk_email_verification` | Email verification for up to 10,000 addresses (native bulk, async if long-running). |
| `bulk_vpn_proxy_detection` | VPN & proxy detection for up to 100 IPs in one call (native batch, always inline; Starter plan or higher). |
| `bulk_dns_lookup` | DNS lookups for up to 200 domains, fanned out concurrently. |
| `bulk_ip_geolocation` | IP geolocation for up to 200 IPs, fanned out concurrently. |
| `bulk_subdomain_lookup` | Subdomain discovery for up to 200 apex domains. |
| `bulk_job_status` | Progress of an in-flight bulk job. |
| `bulk_job_results` | Full per-input results of a completed bulk job. |

### Account

| Tool | What it does |
|---|---|
| `account_balance` | Credits left on each product of your WhoisXML account, and which tools spend them. Free. |

## Example prompts

- *"Look up the WHOIS for suspicious-domain.com and tell me if it's suspicious."*
- *"Find all subdomains of example.com and check their DNS history."*
- *"Check the threat intelligence reputation of 203.0.113.7 and what's hosted there."*

---

© Whois API, Inc. · <https://www.whoisxmlapi.com> · Support: <https://whoisxmlapi.com/contact-us>
