# Hives

A Hive is a group of Reality2 nodes that share a cryptographic identity.  Hive members trust each other, discover each other automatically, and cooperate to deliver events and signals across the mesh.

## Why Hives?

A single user typically owns several devices — a phone, a home hub, a wearable.  Each runs a Reality2 node.  By placing these nodes in the same Hive, they behave as a single logical unit:

- Sentants on any member node can communicate freely.
- Events addressed to a Sentant are routed to whichever node currently hosts it.
- If one member is unreachable, others can hold messages until it reconnects.

## How Nodes Join a Hive

When a node starts for the first time it generates a Hive identity.  Other nodes can join the same Hive by sharing this identity.  Once joined, members authenticate each other using keys derived from the shared identity.

## Discovery

Hive members discover each other over whatever transports are available — BLE beacons, WiFi announcements, LoRa presence messages, or internet connections.  Discovery is continuous: as nodes move in and out of range, the Hive membership updates automatically.

## Trust and Cooperation

Because Hive members share a cryptographic identity, they can verify that a peer genuinely belongs to the group.  This trust enables:

- **Authenticated relay** — messages forwarded within a Hive carry proof of membership.
- **Shared state** — Hive members can replicate Sentant catalogues and routing information.
- **Cooperative routing** — any member can accept an event on behalf of the Hive and forward it internally to the correct node.
