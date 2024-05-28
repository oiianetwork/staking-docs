---
sidebar_position: 230
---

# Nimbus

You can start a Nimbus node like this:

```
beacon:
    image: chainsafe/lodestar:v1.18.1
    command:
      - beacon 
      - --logLevel=info
      - --port=11800
      - --discoveryPort=11800
      - --dataDir=/consensus-data
      - --paramsFile=/el-cl-genesis-data/custom_config_data/config.yaml
      - --genesisStateFile=/el-cl-genesis-data/custom_config_data/genesis.ssz
      - --eth1.depositContractDeployBlock=0
      - --network.connectToDiscv5Bootnodes=true
      - --discv5=true
      - --eth1=true
      - --eth1.providerUrls=http://execution:8545
      - --execution.urls=http://execution:8551
      - --rest=true
      - --rest.address=0.0.0.0
      - --rest.namespace=*
      - --rest.port=4000
      - --nat=true
      - --enr.ip=${IP_ADDRESS}
      - --enr.tcp=11800
      - --enr.udp=11800
      - --subscribeAllSubnets=true
      - --jwt-secret=/el-cl-genesis-data/jwt/jwtsecret
      - --metrics
      - --metrics.address=0.0.0.0
      - --metrics.port=8008
      - --bootnodes=${CL_BOOTNODES}
      - --checkpointSyncUrl=${CL_CHECKPOINT}
    volumes:
      - ./consensus-data:/consensus-data 
      - ./el-cl-genesis-data:/el-cl-genesis-data
    ports:
      - "11800:11800"
      - "4980:4000"
      - "7484:8008"
    depends_on:
      - execution
    restart: unless-stopped
```