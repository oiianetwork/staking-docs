---
sidebar_position: 200
---

# Lighthouse

You can start a Lighthouse node using a command like this in a Docker Compose file:

```yaml
beacon:
    image: sigp/lighthouse:v5.1.3
    command:
      - lighthouse
      - beacon_node
      - --debug-level=info
      - --datadir=/consensus-data
      - --testnet-dir=/el-cl-genesis-data/custom_config_data
      - --enr-address=${IP_ADDRESS}
      - --enr-udp-port=9000
      - --enr-tcp-port=9000
      - --enr-quic-port=9001
      - --listen-address=0.0.0.0
      - --port=9000
      - --http
      - --http-address=0.0.0.0
      - --http-port=5052
      - --http-allow-sync-stalled
      - --execution-endpoints=http://execution:8551
      - --jwt-secrets=/el-cl-genesis-data/jwt/jwtsecret
      - --metrics
      - --metrics-address=0.0.0.0
      - --metrics-allow-origin=*
      - --metrics-port=5054
      - --trusted-peers=${CL_TRUSTPEERS}
      - --boot-nodes=${CL_BOOTNODES}
      - --checkpoint-sync-url=${CL_CHECKPOINT}
      - --subscribe-all-subnets
      - --import-all-attestations
    volumes:
      - ./consensus-data:/consensus-data 
      - ./el-cl-genesis-data:/el-cl-genesis-data
    ports:
      - "9000:9000/tcp"
      - "9000:9000/udp"
      - "9001:9001/udp"
      - "5052:5052"
      - "5054:5054"
    depends_on:
      - execution
    restart: unless-stopped
```
