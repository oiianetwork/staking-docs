---
sidebar_position: 130
---

# Besu

You can start a Besu node like this:

```
execution:
    image: hyperledger/besu:24.5.1
    environment:
      - BESU_OPTS=-Xmx16g
    user: "root"
    command:
      - --logging=DEBUG
      - --data-path=/execution-data
      - --genesis-file=/el-cl-genesis-data/custom_config_data/besu.json
      - --network-id=648
      - --host-allowlist=*
      - --rpc-http-enabled=true
      - --rpc-http-host=0.0.0.0
      - --rpc-http-port=8545
      - --rpc-http-api=ADMIN,CLIQUE,ETH,NET,DEBUG,TXPOOL,ENGINE,TRACE,WEB3
      - --rpc-http-cors-origins=*
      - --rpc-ws-enabled=true
      - --rpc-ws-host=0.0.0.0
      - --rpc-ws-port=8546
      - --rpc-ws-api=ADMIN,CLIQUE,ETH,NET,DEBUG,TXPOOL,ENGINE,TRACE,WEB3
      - --p2p-enabled=true
      - --p2p-host=${IP_ADDRESS}
      - --p2p-port=30303
      - --engine-rpc-enabled=true
      - --engine-jwt-secret=/el-cl-genesis-data/jwt/jwtsecret
      - --engine-host-allowlist=*
      - --engine-rpc-port=8551
      - --sync-mode=FULL
      - --data-storage-format=BONSAI
      - --metrics-enabled=true
      - --metrics-host=0.0.0.0
      - --metrics-port=9001
      - --bootnodes=${EL_BOOTNODES}
      - --genesis-state-hash-cache-enabled=true
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
