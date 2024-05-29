---
sidebar_position: 120
---

# Nethermind

You can start a Nethermind node like this:

```yaml
execution:
    image: nethermindeth/nethermind:release-1.26.0
    command:
      - --log=INFO
      - --datadir=/execution-data
      - --Init.ChainSpecPath=/el-cl-genesis-data/custom_config_data/chainspec.json
      - --Init.WebSocketsEnabled=true
      - --Init.KzgSetupPath=/trusted_setup.txt
      - --config=none.cfg
      - --JsonRpc.Enabled=true
      - --JsonRpc.EnabledModules=net,eth,consensus,subscribe,web3,admin
      - --JsonRpc.Host=0.0.0.0
      - --JsonRpc.Port=8545
      - --JsonRpc.WebSocketsPort=8546
      - --JsonRpc.EngineHost=0.0.0.0
      - --JsonRpc.EnginePort=8551
      - --Network.ExternalIp=${IP_ADDRESS}
      - --Network.DiscoveryPort=30303
      - --Network.P2PPort=30303
      - --JsonRpc.JwtSecretFile=/el-cl-genesis-data/jwt/jwtsecret
      - --Metrics.Enabled=true
      - --Metrics.ExposePort=9001
      - --Network.StaticPeers=${EL_BOOTNODES}
    volumes:
      - ./execution-data:/execution-data
      - ./el-cl-genesis-data:/el-cl-genesis-data
      - ./trusted_setup.txt:/trusted_setup.txt
    ports:
      - "8545:8545" 
      - "8546:8546" 
      - "8551:8551" 
      - "9001:9001" 
      - "30303:30303"
    restart: unless-stopped
```
