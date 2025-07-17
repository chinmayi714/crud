# SAP Message Server Connection Flow Diagram (Mermaid)

```mermaid
flowchart LR
    subgraph Flow1["Flow 1: Direct Configuration"]
        f1_config["Configuration<br/>type: direct"]
        f1_discovery["Normal Discovery"]
        f1_entityForm["Forms entity<br/>from the configuration"]
        f1_entityId["Entity ID<br/>host:sysnr:client/user"]
        f1_sensor["Invoke Sensor<br/>with entity ID and make<br/>direct connection to ABAP instance"]

        f1_config --> f1_discovery
        f1_discovery --> f1_entityForm
        f1_entityForm --> f1_entityId
        f1_entityId --> f1_sensor
    end

    subgraph Flow2["Flow 2: Message Server Configuration"]
        f2_config["Configuration<br/>type: message-server"]
        f2_msgDiscovery["Message Server Discovery"]
        f2_queries["Queries message server<br/>and gets sysnr and target host<br/>to form entity ID of each<br/>application server"]
        f2_entityId["Entity ID<br/>host:sysnr:client/user"]
        f2_sensor["Invoke Sensor<br/>with entity ID and make<br/>direct connection to each application server"]

        f2_config --> f2_msgDiscovery
        f2_msgDiscovery --> f2_queries
        f2_queries --> f2_entityId
        f2_entityId --> f2_sensor
    end

    %% Custom Styles
    classDef pink fill:#ffccff,stroke:#000,color:#000,font-weight:bold;
    classDef blue fill:#99ccff,stroke:#000,color:#000,font-weight:bold;
    classDef green fill:#ccffcc,stroke:#000,color:#000,font-weight:bold;
    classDef yellow fill:#ffffcc,stroke:#000,color:#000,font-weight:bold;

    %% Assign styles
    class f1_config,f2_config pink
    class f1_discovery,f1_entityForm,f1_sensor,f2_msgDiscovery,f2_sensor blue
    class f2_queries green
    class f1_entityId,f2_entityId yellow


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
