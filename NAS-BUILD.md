# NAS Server — Project Notes

Status: 🟡 Planned — hardware sourced, build not yet assembled

## Goal

Build a low-cost NAS to serve as the homelab's cloud storage layer, running:
- **Immich** — self-hosted photo/video backup
- **NextCloud** — general file sync and storage

## Approach

Stay within an "extreme low" budget by sourcing hardware from AliExpress, Facebook Marketplace, or salvaging parts from old equipment, rather than buying new/retail.

## Hardware & Budget

| Component | Name | Price | Notes |
|---|---|---|---|
| Motherboard | Topton NAS N5105 | $236.70 | Original listing unavailable; similar model ~$275 on Amazon |
| RAM | 2 × 8GB sticks | N/A | Salvaged from an old laptop |
| Case | Jonsbo N2 NAS Mini Case | $181.71 | |
| PSU | 500W SilverStone EX500-B | $109.00 | |
| HDD | 4 × 6TB HDD | — | Used data centre drives, bought via Facebook Marketplace |

**Total (excl. HDD, TBD):** ~$527.41

## Open decisions

- [ ] NAS OS — candidates: TrueNAS SCALE, Unraid, or a plain Debian + Docker stack (to match the rest of the homelab)
- [ ] Storage layout — RAID/RAIDZ level for the 4× 6TB drives, balancing redundancy vs usable capacity
- [ ] Final HDD price/total budget figure

## Pre-deployment checklist

- [ ] Burn-in test each used HDD (SMART check + `badblocks` or equivalent stress test) before trusting real data to them — they're secondhand with unknown hours
- [ ] Confirm PSU load is reasonable for the actual draw (4× HDD + N5105 idle is low; verify efficiency at that load)
- [ ] Assemble in Jonsbo N2 case, confirm airflow/thermals with all 4 bays populated
- [ ] Install chosen OS, configure storage pool
- [ ] Deploy Immich and NextCloud containers
- [ ] Set up backup strategy (this is also an open item for the homelab overall)
- [ ] Connect to Tailscale for remote access, consistent with the rest of the homelab

## Notes / lessons learned

*(to be filled in as the build progresses)*
