# SAP Message Server Connection Flow Diagram (Mermaid)

```mermaid
flowchart TD
    config["Configuration\ntype: message-server"]
    msgDiscovery["Message Server Discovery"]
    normalDiscovery["Normal Discovery"]
    queries["Queries and get the\nsysnr and host name\nand forms the entityId"]
    entityId["host:sysnr:client/user"]
    sensor["Invoke Sensor\nwith entity Id\nand make direct\nconnection to SAP"]
    directConfig["config: type: direct"]
    
    config --> msgDiscovery
    config -->|msg server| queries
    msgDiscovery -->|forms entity\nfrom entry| normalDiscovery
    queries --> entityId
    normalDiscovery --> sensor
    entityId --> sensor
    sensor --> directConfig
    
    classDef pink fill:#ffccff,stroke:#333,stroke-width:2px
    classDef blue fill:#bbbbff,stroke:#333,stroke-width:2px
    classDef green fill:#ddffdd,stroke:#333,stroke-width:2px
    classDef yellow fill:#ffffdd,stroke:#333,stroke-width:2px
    classDef cyan fill:#ddddff,stroke:#333,stroke-width:2px
    
    class config,directConfig pink
    class msgDiscovery,normalDiscovery blue
    class queries green
    class entityId yellow
    class sensor cyan
```

## Diagram Explanation

This diagram illustrates the SAP Message Server connection flow:

1. **Configuration** (type: message-server) - The initial configuration specifies a message server connection type.

2. **Message Server Discovery** - The process begins with discovering the message server.

3. **Normal Discovery** - An alternative discovery path that forms an entity from the configuration entry.

4. **Message Server Queries** - The message server queries and retrieves the system number (sysnr) and host name to form the entity ID.

5. **Entity ID Formation** - The entity ID is formed using the format: `host:sysnr:client/user`.

6. **Sensor Invocation** - The system invokes a sensor with the entity ID and establishes a direct connection to SAP.

7. **Final Configuration** - The connection is established with a direct connection type.

// Made with Bob
