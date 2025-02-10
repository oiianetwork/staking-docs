---
sidebar_position: 130
---

# MEV Boost

## Start boost

This is an example:

```yaml title="docker-compose.yml"
version: '3.8'

services:
  mev-boost:
    image: flashbots/mev-boost
    command: >
      -addr 0.0.0.0:18550
      -genesis-fork-version 0x10000001
      -genesis-timestamp 1709532000
      -relay-check
      -relay http://0xa55c1285d84ba83a5ad26420cd5ad3091e49c55a813eee651cd467db38a8c8e63192f47955e9376f6b42f6d190571cb5@<relay-ip>:9062
    ports:
      - "18550:18550"
    environment:
      - SKIP_RELAY_SIGNATURE_CHECK=1
```

## Use mev-boost

Configure your consensus and validator client to use mev-boost:

- Prysm consensus: `--http-mev-relay=http://127.0.0.1:18550`
- Prysm validator: `--enable-builder`
- Nimbus consensus: `--payload-builder=true --payload-builder-url=http://127.0.0.1:18550`
- Nimbus validator: `--payload-builder=true`
- Lodestar consensus: `--builder --builder.urls http://127.0.0.1:18550`
- Lodestar validator: `--builder`
- Teku combined: `--validators-builder-registration-default-enabled=true --builder-endpoint=http://127.0.0.1:18550`
- Lighthouse consensus: `--builder http://127.0.0.1:18550` 
- Lighthouse validator: `--builder-proposals`

## check relay txs

Transactions packaged by mev-boost-relay can be viewed via relay scan:

- [http://152.53.37.233:9060](http://152.53.37.233:9060/)  for relay-eur.endurancehub.org
- [http://202.61.229.228:9060](http://202.61.229.228:9060/) for relay-us.endurancehub.org

Reference: [Guide on how to prepare a staking machine for the Merge](https://github.com/eth-educators/ethstaker-guides/blob/main/prepare-for-the-merge.md#configure-your-consensus-and-validator-client-to-use-mev-boost)
