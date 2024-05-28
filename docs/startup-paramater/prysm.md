---
sidebar_position: 210
---

# Prysm

You can start a Prysm node like this:

```
beacon:
    image: gcr.io/prysmaticlabs/prysm/beacon-chain:v5.0.3
    command:
      - --accept-terms-of-use=true
      - --datadir=/consensus-data
      - --chain-config-file=/el-cl-genesis-data/custom_config_data/config.yaml
      - --genesis-state=/el-cl-genesis-data/custom_config_data/genesis.ssz
      - --contract-deployment-block=0
      - --execution-endpoint=http://execution:8551
      - --rpc-host=0.0.0.0
      - --rpc-port=3500
      - --grpc-gateway-host=0.0.0.0
      - --grpc-gateway-corsdomain=*
      - --grpc-gateway-port=4000
      - --p2p-host-ip=${IP_ADDRESS}
      - --p2p-tcp-port=13000
      - --p2p-udp-port=12000
      - --min-sync-peers=0
      - --verbosity=info
      - --suggested-fee-recipient=0x8fBAE29f7BEbF106eB5f5C0E3f9F60d870DD6b41
      - --jwt-secret=/el-cl-genesis-data/jwt/jwtsecret
      - --disable-monitoring=false
      - --monitoring-host=0.0.0.0
      - --monitoring-port=8080
      - --bootstrap-node=${CL_BOOTNODES}
      - --peer=${CL_STATICPEERS}
      - --checkpoint-sync-url=${CL_CHECKPOINT}
      - --genesis-beacon-api-url=${CL_CHECKPOINT}
      - --subscribe-all-subnets=true
      - --p2p-static-id=true
    volumes:
      - ./consensus-data:/consensus-data 
      - ./el-cl-genesis-data:/el-cl-genesis-data
    ports:
      - "13000:13000/tcp"
      - "12000:12000/udp"
      - "3500:3500"
      - "4000:4000"
      - "8080:8080"
    depends_on:
      - execution
    restart: unless-stopped
```
