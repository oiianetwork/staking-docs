---
sidebar_position: 220
---

# Teku

You can start a Teku node like this:

```yaml
beacon:
    image: consensys/teku:24.4.0
    user: "root"
    command:
      - --logging=INFO 
      - --log-destination=CONSOLE 
      - --network=/el-cl-genesis-data/custom_config_data/config.yaml 
      - --initial-state=/el-cl-genesis-data/custom_config_data/genesis.ssz 
      - --data-path=/consensus-data 
      - --data-storage-mode=archive 
      - --data-storage-non-canonical-blocks-enabled=true
      - --rest-api-enabled=true 
      - --rest-api-docs-enabled=true 
      - --rest-api-interface=0.0.0.0 
      - --rest-api-port=4000 
      - --rest-api-host-allowlist=* 
      - --ee-jwt-secret-file=/el-cl-genesis-data/jwt/jwtsecret 
      - --ee-endpoint=http://execution:8551 
      - --metrics-enabled 
      - --metrics-interface=0.0.0.0 
      - --metrics-host-allowlist='*' 
      - --metrics-categories=BEACON,PROCESS,LIBP2P,JVM,NETWORK,PROCESS 
      - --metrics-port=8008 
      - --Xtrusted-setup=/trusted_setup.txt 
      - --checkpoint-sync-url=${CL_CHECKPOINT}
      - --p2p-discovery-bootnodes=${CL_BOOTNODES}
      - --p2p-static-peers=${CL_STATICPEERS}
      - --p2p-discovery-site-local-addresses-enabled=true
      - --p2p-enabled=true 
      - --p2p-peer-lower-bound=1 
      - --p2p-advertised-ip=${IP_ADDRESS}
      - --p2p-port=11400
      - --ignore-weak-subjectivity-period-enabled
      - --validators-graffiti=Besu-Teku
      - --p2p-subscribe-all-subnets-enabled=true
    volumes:
      - ./consensus-data:/consensus-data 
      - ./el-cl-genesis-data:/el-cl-genesis-data
      - ./trusted_setup.txt:/trusted_setup.txt
    ports:
      - "11400:11400/udp"
      - "11400:11400/tcp" 
      - "4000:4000"
      - "8008:8008"
    depends_on:
      - execution
    restart: unless-stopped
```
