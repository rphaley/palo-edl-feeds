# Palo Alto Threat Feed EDL

Combined and deduplicated threat IP feeds from multiple sources. Adjacent CIDRs are aggregated. Use this as a single IP List EDL in Palo in place of the per-source EDLs to save capacity.

## Sources

| Source | Raw Count | URL |
| ------ | --------- | --- |
| emerging_threats | 1711 | `https://rules.emergingthreats.net/fwrules/emerging-Block-IPs.txt` |
| emerging_threats_compromised | 504 | `https://rules.emergingthreats.net/blockrules/compromised-ips.txt` |
| cins_score | 15000 | `https://cinsscore.com/list/ci-badguys.txt` |
| blocklist_de | 29081 | `https://opendbl.net/lists/blocklistde-all.list` |
| spamhaus_drop | 1687 | `https://www.spamhaus.org/drop/drop.txt` |
| dshield_block | 20 | `https://isc.sans.edu/block.txt` |
| binary_defense | 390 | `https://www.binarydefense.com/banlist.txt` |
| abuseipdb (API key) | 10000 | `https://api.abuseipdb.com/api/v2/blacklist` |
| waf_offenders (local) | 176 | `waf/waf-offenders.txt` |

## Output

- **Combined EDL URL:** `https://raw.githubusercontent.com/rphaley/palo-edl-feeds/main/threat/combined-threat-ips.txt`
- **Final entry count:** 35106
- **Raw total (sum of all sources):** 58569
- **Slots saved vs. running them separately:** 23463
- **Last updated UTC:** 2026-10-27 09:55:08
