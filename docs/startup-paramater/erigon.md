---
sidebar_position: 140
---

# Erigon

You should initialize the genesis block first:

```
docker run \
  --rm \
  -it \
  --user=root \
  -v $(pwd)/execution-data:/execution-data \
  -v $(pwd)/el-cl-genesis-data:/el-cl-genesis-data \
  thorax/erigon:v2.60.0 \
  init \
  --datadir=/execution-data \
  /el-cl-genesis-data/custom_config_data/genesis.json
```

Then you can start a Erigon node like this:

```
execution:
    image: thorax/erigon:v2.60.0
    user: "root"
    command:
      - --log.console.verbosity=4
      - --datadir=/execution-data
      - --port=30303
      - --networkid=648
      - --http.api=eth,erigon,engine,web3,net,debug,trace,txpool,admin,ots
      - --http.vhosts=*
      - --ws
      - --allow-insecure-unlock
      - --nat=extip:${IP_ADDRESS}
      - --http
      - --http.addr=0.0.0.0
      - --http.corsdomain=*
      - --http.port=8545
      - --authrpc.jwtsecret=/el-cl-genesis-data/jwt/jwtsecret
      - --authrpc.addr=0.0.0.0
      - --authrpc.port=8551
      - --authrpc.vhosts=*
      - --metrics
      - --metrics.addr=0.0.0.0
      - --metrics.port=9001
      - --bootnodes=${EL_BOOTNODES}
      - --staticpeers=${EL_BOOTNODES}
      - --db.size.limit=50GB
    volumes:
      - ./execution-data:/execution-data
      - ./el-cl-genesis-data:/el-cl-genesis-data
    ports:
      - "8545:8545" 
      - "8551:8551" 
      - "9001:9001" 
      - "30303:30303"
    restart: unless-stopped
```
