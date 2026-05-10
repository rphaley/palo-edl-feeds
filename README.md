# palo-edl-feeds

Auto-generated External Dynamic Lists (EDLs) for Palo Alto Networks firewalls. Each feed is maintained by a GitHub Actions workflow that runs daily and commits updated list files to this repo.

Point your Palo EDL objects directly at the raw GitHub URLs — no hosting required.

## Feeds

| Feed | Type | Description | Files |
| ---- | ---- | ----------- | ----- |
| [ASN Prefixes](./asn/) | IP List | IP prefixes announced by curated VPS/hosting ASNs commonly abused by threat actors. **One EDL file per ASN** to stay under firewall per-list capacity limits. | See [asn/README.md](./asn/README.md) for per-ASN URLs |
| [LOLRMM Domains](./lolrmm/) | Domain List | Domains associated with RMM tools tracked by [LOLRMM](https://lolrmm.io). Used in Anti-Spyware profile for DNS sinkholing. | `https://raw.githubusercontent.com/rphaley/palo-edl-feeds/main/lolrmm/lolrmm-domains-edl.txt` |

## Usage

### IP List EDLs (ASN feed)

1. **Objects → External Dynamic Lists → Add**
2. Set **Type** to `IP List`
3. Paste the raw URL for the ASN you want
4. Set **Check for updates** to `Daily`
5. Reference in a Security Policy rule via Source or Destination Address

### Domain List EDLs (LOLRMM feed)

Domain List EDLs cannot be referenced directly in a Security Policy rule. They must be consumed via Anti-Spyware profile.

1. **Objects → External Dynamic Lists → Add**, Type `Domain List`, paste URL
2. **Objects → Security Profiles → Anti-Spyware → [profile] → DNS Policies tab**
3. Under External Dynamic Lists, add the Domain EDL with Policy Action `sinkhole` or `block`
4. Attach the Anti-Spyware profile to a Security Policy rule covering outbound DNS traffic

## Schedule

Workflows run daily on a staggered schedule to avoid commit conflicts:

- ASN feed: **08:00 UTC**
- LOLRMM feed: **09:00 UTC**

## Structure

```
asn/
  AS<number>.txt         # One IP list per ASN
  README.md              # ASN table with org names, counts, EDL URLs
lolrmm/
  lolrmm-domains-edl.txt # Flat domain list, one entry per line
  README.md              # Stats, last updated
.github/workflows/
  update-asn-edl.yml
  update-lolrmm-edl.yml
```
