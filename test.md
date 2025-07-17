# SAP Message Server Connection Flow Diagram (Mermaid)

```mermaid
flowchart TD
    config["Configuration<br/>type: message-server"]
    msgDiscovery["Message Server<br/>Discovery"]
    normalDiscovery["Normal<br/>Discovery"]
    queries["Queries and get the<br/>sysnr and host name<br/>and forms the entityId"]
    entityId["host:sysnr:client/user"]
    sensor["Invoke Sensor<br/>with entity Id<br/>and make direct<br/>connection to SAP"]
    directConfig["config:<br/>type: direct"]
    
    config --> msgDiscovery
    config -->|msg server| queries
    msgDiscovery -->|forms entity<br/>from entry| normalDiscovery
    queries --> entityId
    normalDiscovery --> sensor
    entityId --> sensor
    sensor --> directConfig
    
    %% Custom styles for better visibility
    classDef pink fill:#ffccff,stroke:#000000,stroke-width:2px,color:#000,font-weight:bold;
    classDef blue fill:#99ccff,stroke:#000000,stroke-width:2px,color:#000,font-weight:bold;
    classDef green fill:#ccffcc,stroke:#000000,stroke-width:2px,color:#000,font-weight:bold;
    classDef yellow fill:#ffff99,stroke:#000000,stroke-width:2px,color:#000,font-weight:bold;
    classDef cyan fill:#99ffff,stroke:#000000,stroke-width:2px,color:#000,font-weight:bold;
    
    %% Assign classes
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
