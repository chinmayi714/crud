# SAP Message Server Connection Flow Diagram (Mermaid)

## Flow 1: Direct Configuration

```mermaid
flowchart LR
  f1_pad_left[" "]:::hidden  f1_config["Configuration<br>type: direct"] --> f1_discovery["Normal Discovery"] --> f1_entityForm["Forms entity<br>from the configuration"] --> f1_entityId["Entity ID<br>host:sysnr:client/user"] --> f1_sensor["Invoke Sensor<br>with entity ID and make<br>direct connection to ABAP instance"]  f1_pad_right[" "]:::hidden

  %% Styling
  classDef pink fill:#ffccff,stroke:#000,color:#000,font-weight:bold
  classDef blue fill:#b0b0ff,stroke:#000,color:#000,font-weight:bold
  classDef yellow fill:#ffffcc,stroke:#000,color:#000,font-weight:bold
  classDef hidden fill:none,stroke:none
  
  %% Apply styles
  f1_config:::pink
  f1_discovery:::blue
  f1_entityForm:::blue
  f1_entityId:::yellow
  f1_sensor:::blue
```

## Flow 2: Message Server Configuration

```mermaid
flowchart LR
  f2_pad_left[" "]:::hidden  f2_config["Configuration<br>type: message-server"] --> f2_msgDiscovery["Message Server Discovery"] --> f2_queries["Queries message server<br>and gets sysnr and target host<br>to form entity ID of each<br>application server"] --> f2_entityId["Entity ID<br>host:sysnr:client/user"] --> f2_sensor["Invoke Sensor<br>with entity ID and make<br>direct connection to each application server"]  f2_pad_right[" "]:::hidden

  %% Styling
  classDef pink fill:#ffccff,stroke:#000,color:#000,font-weight:bold
  classDef blue fill:#b0b0ff,stroke:#000,color:#000,font-weight:bold
  classDef green fill:#ccffcc,stroke:#000,color:#000,font-weight:bold
  classDef yellow fill:#ffffcc,stroke:#000,color:#000,font-weight:bold
  classDef hidden fill:none,stroke:none
  
  %% Apply styles
  f2_config:::pink
  f2_msgDiscovery:::blue
  f2_queries:::green
  f2_entityId:::yellow
  f2_sensor:::blue
```

## Diagram Explanation

This diagram illustrates the SAP Message Server connection flow compared to direct connection:

### Flow 1: Direct Configuration

1. **Configuration** (type: direct) - The initial configuration specifies a direct connection type.
2. **Normal Discovery** - The system uses normal discovery process.
3. **Forms Entity** - Forms an entity from the configuration parameters.
4. **Entity ID** - Creates an entity ID using the format: `host:sysnr:client/user`.
5. **Invoke Sensor** - The system invokes a sensor with the entity ID and establishes a direct connection to the ABAP instance.

### Flow 2: Message Server Configuration

1. **Configuration** (type: message-server) - The initial configuration specifies a message server connection type.
2. **Message Server Discovery** - The process begins with discovering the message server.
3. **Message Server Queries** - The message server queries and retrieves the system number (sysnr) and host name to form the entity ID for each application server.
4. **Entity ID Formation** - Entity IDs are formed for each application server using the format: `host:sysnr:client/user`.
5. **Sensor Invocation** - The system invokes a sensor with each entity ID and establishes direct connections to each application server.

### Key Differences

- The **direct configuration** flow connects to a specific ABAP instance directly using configuration parameters.
- The **message server configuration** flow queries the message server to discover multiple application servers, enabling load balancing and high availability.
- Both flows ultimately create entity IDs and establish direct connections, but the message server approach can connect to multiple servers.

// Made with Bob
