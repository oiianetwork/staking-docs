---
sidebar_position: 20
---

# Select Client

## Client type

Execution layer client type:
- Geth
- Nethermind
- Besu
- Erigon
- Reth

Consensus layer client type:
- Lighthouse
- Prysm
- Teku
- Nimbus
- Lodestar

To ensure diversity in client types, if you are running multiple node groups, we strongly recommend using a combination of different types of clients together to enhance the network's tolerance for client type diversity and avoid network anomalies caused by bugs in a single client.

If you have 3 nodes, you could use combinations such as Geth+Lighthouse, Nethermind+Prysm, Besu+Teku, etc.

## Client version

All the clients we use are **official versions released by client development teams** within the Ethereum ecosystem. We have not made any modifications to the clients. You can directly use the official Docker images or binary packages, as well as refer directly to their source code.

The Docker images and versions we use for our mainnet are:

```
### Consensus layer clients
  lighthouse: sigp/lighthouse:v5.1.3
  prysm: gcr.io/prysmaticlabs/prysm/beacon-chain:v5.0.3
  prysm_validator: gcr.io/prysmaticlabs/prysm/validator:v5.0.3
  teku: consensys/teku:24.4.0
  lodestar: chainsafe/lodestar:v1.18.1
  nimbus: statusim/nimbus-eth2:multiarch-v24.5.1

### Execution layer clients
  besu: hyperledger/besu:24.5.1
  erigon: thorax/erigon:v2.60.0
  geth: ethereum/client-go:v1.14.0
  nethermind: nethermindeth/nethermind:release-1.26.0
  reth: ghcr.io/paradigmxyz/reth:v0.2.0-beta.6
```
