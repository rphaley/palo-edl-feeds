# palo-edl-feeds

Auto-generated External Dynamic Lists (EDLs) for Palo Alto Networks firewalls. Each feed is maintained by a GitHub Actions workflow that runs daily and commits updated list files to this repo.

Point your Palo EDL objects directly at the raw GitHub URLs — no hosting required.

## Feeds

| Feed | Type | Description | EDL URL |
| ---- | ---- | ----------- | ------- |
| [ASN Prefixes](./asn/) | IP List | IP prefixes announced by a curated set of ASNs (hosting providers commonly abused by threat actors) | `https://raw.githubusercontent.com/rphaley/palo-edl-feeds/main/asn/palo-asn-edl.txt` |
| [LOLRMM Domains](./lolrmm/) | Domain List | Domains associated with RMM tools tracked by [LOLRMM](https://lolrmm.io) | `https://raw.githubusercontent.com/rphaley/palo-edl-feeds/main/lolrmm/lolrmm-domains-edl.txt` |

## Usage

1. In Panorama or PAN-OS: **Objects → External Dynamic Lists → Add**
2. Set **Type** to match the feed (IP List or Domain List)
3. Paste the raw URL from the table above
4. Set **Repeat** to daily
5. Reference the EDL in a Security Policy rule with the desired action (Block / Alert)

## Schedule

Workflows run daily on a staggered schedule to avoid commit conflicts:

- ASN feed: **08:00 UTC**
- LOLRMM feed: **09:00 UTC**

## Structure

```
asn/
  palo-asn-edl.txt       # Flat IP/prefix list, one entry per line
  README.md              # ASN table, stats, last updated
lolrmm/
  lolrmm-domains-edl.txt # Flat domain list, one entry per line
  README.md              # Stats, last updated
.github/workflows/
  update-asn-edl.yml
  update-lolrmm-edl.yml
```
