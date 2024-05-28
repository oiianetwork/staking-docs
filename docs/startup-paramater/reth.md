---
sidebar_position: 150
---

# Reth

You can start a Reth node like this:

```
execution:
    image: ghcr.io/paradigmxyz/reth:v0.2.0-beta.6
    command:
      - node
      - -vvv
      - --datadir=/execution-data
      - --chain=/el-cl-genesis-data/custom_config_data/genesis.json
      - --addr=0.0.0.0
      - --port=30303
      - --discovery.port=30303
      - --discovery.addr=0.0.0.0
      - --http
      - --http.port=8545
      - --http.addr=0.0.0.0
      - --http.corsdomain=*
      - --http.api=admin,net,eth,web3,debug,trace
      - --ws
      - --ws.addr=0.0.0.0
      - --ws.port=8546
      - --ws.api=net,eth
      - --ws.origins=*
      - --nat=extip:${IP_ADDRESS}
      - --authrpc.port=8551
      - --authrpc.jwtsecret=/el-cl-genesis-data/jwt/jwtsecret
      - --authrpc.addr=0.0.0.0
      - --metrics=0.0.0.0:9001
      - --bootnodes=${EL_BOOTNODES}
      - --trusted-peers=${EL_BOOTNODES}
    volumes:
      - ./execution-data:/execution-data
      - ./el-cl-genesis-data:/el-cl-genesis-data
    ports:
      - "8545:8545" 
      - "8546:8546" 
      - "8551:8551" 
      - "9001:9001" 
      - "30303:30303"
    restart: unless-stopped
```
