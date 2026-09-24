# WAF Offenders

Source IPs blocked at the DePaul cyber range edge reverse proxy. This is a **source**, not a consumable EDL — it has no fetch-and-build workflow of its own. The edge proxy commits directly to `waf-offenders.txt`, and this README is regenerated automatically whenever that file changes. The [threat feed workflow](../.github/workflows/update-threat-edl.yml) merges it into [`combined-threat-ips.txt`](../threat/) on its next run.

## Format

Plain text, one IPv4 address per line, preceded by a `#`-prefixed header block giving window and last-updated time. No CIDR aggregation — this is raw log output, not built for direct EDL use.

## Details

| | |
| --- | --- |
| Source | Requests blocked at the edge reverse proxy |
| Window | 14 days rolling, best effort (bounded by log retention) |
| Push cadence | Hourly, by the edge proxy directly |
| Consumed by | [Combined Threat IPs](../threat/) feed, daily at 04:30 UTC |
| Current entries | 160 |
| Proxy last updated | 2026-09-24 09:00:11 UTC |
| README last computed | 2026-09-24 09:00:20 UTC |

## Notes

- Entries age out 14 days after they were last seen at the proxy.
- This repo is public. Review the file before assuming an entry is hostile — it's a raw block log, not a curated or attributed threat list.
- Don't point a Palo EDL object directly at `waf-offenders.txt`; use the [combined threat feed](../threat/) instead, which already includes it.
