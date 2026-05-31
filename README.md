# Oracle HA Lab

A small, runnable lab to *feel* the concepts from the article
**"The Oracle HA Decision Tree: RAC vs Data Guard vs Both"** on your own machine — no Oracle account
required. It runs the community **Oracle Database Free** image and drives every command inside the
container, so you don't even need a local Oracle client.

[![lab-e2e](https://github.com/pyaroslav/oracle-ha-lab/actions/workflows/ci.yml/badge.svg)](https://github.com/pyaroslav/oracle-ha-lab/actions/workflows/ci.yml)

## What's here

| Path | What it is |
| --- | --- |
| [`lab/`](lab/) | **Zero-login lab** (Oracle Database Free). Human-error recovery, RMAN backup/restore, and block-corruption drills. Verified end-to-end in CI. |
| [`lab-dataguard/`](lab-dataguard/) | **Opt-in Enterprise Edition module** for a real Data Guard switchover/failover. Needs an Oracle account; documented walkthrough, not auto-run. |

## Quick start

```bash
cd lab
./run.sh up        # start the database (first run pulls the image + creates the DB)
./run.sh setup     # enable archivelog + create a small demo schema
./run.sh all       # run all three drills end to end
```

See [`lab/README.md`](lab/README.md) for the full guide, expected output, and troubleshooting.

## Why only these drills (and not RAC / Data Guard) on the Free image?

- **RAC** needs shared storage and a cluster interconnect — not something you can meaningfully run on a
  single laptop in a container.
- **Data Guard** is an Enterprise Edition feature, so it isn't available on the zero-login Free image.
  The opt-in EE module in [`lab-dataguard/`](lab-dataguard/) covers it.

So this lab focuses on the failure modes you *can* reproduce locally — and which the article argues are
the most commonly mishandled: **human error, media loss, and corruption.**

## Disclaimer

This is a personal, educational project. All data is generic and invented for illustration. Oracle® is
a registered trademark of Oracle Corporation; this project is independent and not affiliated with,
authorized, or endorsed by Oracle. The lab pulls the community `gvenzl/oracle-free` image (Oracle
Database Free, under Oracle's Free license) — review Oracle's license terms for your use.

## License

[MIT](LICENSE).
