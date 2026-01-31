# Terminology

#### Reality2

- The name for the overall platform.

#### Node

- A piece of hardware that runs the Reality2 client.  In the reference implementation, this is a unix based tool (usually Linux), using the Erlang BEAM engine.

#### Sentant

- A Sentant is a Sentient Digital Agent, the core unit of the Reality2 platform.  It has many properties - see the section on Sentants for more details.

#### Swarm

- Groups of Sentants work together in Swarms.  Swarms typically belong to a single user, and may encompass Sentants across several Nodes.  Swarms use the Transient Networks to find other Swarms and to initiate interaction with other Nodes.

#### Transient Network

- Each node interacts with other nodes through the networks it connects to — Bluetooth, WiFi, LoRa and the internet.  These links are often temporary (hence "transient").  Sentants are aware of the networks they are on, and actively use them to establish connections for their users.  The TransNet subsystem manages discovery and communication across all available transports.

#### Hive

- A group of Nodes that share a cryptographic identity.  Hive members discover each other automatically over whatever transports are available and cooperate to route events and signals.  A Hive is the unit of trust and collaboration in the mesh.

#### WFS (Waggle Finding Service)

- The naming and routing service that locates Sentants across Nodes and Hives.  When you send an event to a Sentant by name, WFS resolves where that Sentant lives and routes the event there — whether it is on the same Node, in the same Hive, or on a remote Hive reachable through the mesh.