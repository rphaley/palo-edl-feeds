# Palo Alto Threat Feed EDL

Combined and deduplicated threat IP feeds from multiple sources. Adjacent CIDRs are aggregated. Use this as a single IP List EDL in Palo in place of the per-source EDLs to save capacity.

## Sources

| Source | Raw Count | URL |
| ------ | --------- | --- |
| emerging_threats | 1778 | `https://rules.emergingthreats.net/fwrules/emerging-Block-IPs.txt` |
| emerging_threats_compromised | 518 | `https://rules.emergingthreats.net/blockrules/compromised-ips.txt` |
| cins_score | 15000 | `https://cinsscore.com/list/ci-badguys.txt` |
| blocklist_de | 23284 | `https://opendbl.net/lists/blocklistde-all.list` |
| spamhaus_drop | 1756 | `https://www.spamhaus.org/drop/drop.txt` |
| dshield_block | 20 | `https://isc.sans.edu/block.txt` |
| binary_defense | 344 | `https://www.binarydefense.com/banlist.txt` |
| abuseipdb (API key) | 10000 | `https://api.abuseipdb.com/api/v2/blacklist` |
| waf_offenders (local) | 151 | `waf/waf-offenders.txt` |

## Output

- **Combined EDL URL:** `https://raw.githubusercontent.com/rphaley/palo-edl-feeds/main/threat/combined-threat-ips.txt`
- **Final entry count:** 29625
- **Raw total (sum of all sources):** 52851
- **Slots saved vs. running them separately:** 23226
- **Last updated UTC:** 2026-11-03 12:07:40
