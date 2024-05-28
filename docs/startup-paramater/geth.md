---
sidebar_position: 110
---

# Geth

You must initialize the Execution Layer node with `genesis.json` first like this:

```
docker run \
  --rm \
  -it \
  -v $(pwd)/execution-data:/execution-data \
  -v $(pwd)/el-cl-genesis-data:/el-cl-genesis-data \
  ethereum/client-go:v1.14.0 \
  --state.scheme=path \
  --datadir=/execution-data \
  init \
  /el-cl-genesis-data/custom_config_data/genesis.json
```

Then you can start a Geth node using a command like this in a Docker Compose file:

```
execution:
    image: ethereum/client-go:v1.14.0
    command:
      - --networkid=648
      - --state.scheme=path
      - --verbosity=4
      - --datadir=/execution-data
      - --http
      - --http.addr=0.0.0.0
      - --http.port=8545
      - --http.vhosts=*
      - --http.corsdomain=*
      - --http.api=admin,engine,net,eth,web3,debug,txpool
      - --ws
      - --ws.addr=0.0.0.0
      - --ws.port=8546
      - --ws.api=admin,engine,net,eth,web3,debug
      - --ws.origins=*
      - --allow-insecure-unlock
      - --nat=extip:${IP_ADDRESS}
      - --authrpc.port=8551
      - --authrpc.addr=0.0.0.0
      - --authrpc.vhosts=*
      - --authrpc.jwtsecret=/el-cl-genesis-data/jwt/jwtsecret
      - --syncmode=full
      - --rpc.allow-unprotected-txs
      - --metrics
      - --metrics.addr=0.0.0.0
      - --metrics.port=9001
      - --port=30303
      - --discovery.port=30303
      - --bootnodes=${EL_BOOTNODES}
    volumes:
      - ./execution-data:/execution-data
      - ./el-cl-genesis-data:/el-cl-genesis-data
    ports:
      - "8545:8545" 
      - "8546:8546" 
      - "8551:8551" 
      - "9001:9001" 
      - "30303:30303/tcp"
      - "30303:30303/udp"
    restart: unless-stopped
```
