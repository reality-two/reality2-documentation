# TransNet Overview

TransNet is the networking subsystem that lets Reality2 nodes discover each other and exchange events across multiple wireless and internet transports.

## Supported Transports

TransNet supports four transport types.  A node uses whichever transports are available on its hardware:

- **Bluetooth Low Energy (BLE)** — short-range discovery and lightweight messaging between nearby devices.
- **WiFi** — higher-bandwidth communication within a local network or WiFi cell.
- **LoRa** — long-range, low-power mesh links for rural or sparse environments.
- **Internet** — TCP/IP connections for cloud-reachable nodes or cross-site links.

## How It Works

When a node starts, TransNet begins advertising its presence over each available transport.  Other nodes detect these advertisements and establish peer connections.  Once connected, nodes can relay events and signals on behalf of Sentants.

Key behaviours:

- **Automatic discovery** — nodes find each other without manual configuration.
- **Transport selection** — when multiple transports are available to reach a peer, TransNet chooses the most appropriate one.
- **Message relay** — a node can forward events through intermediate nodes to reach destinations that are not directly reachable.
- **Store and forward** — if a destination is temporarily unreachable, messages can be held and delivered when the link is restored.

## Relationship to Hives and WFS

TransNet provides the raw connectivity.  [Hives](Hives.md) add a trust and identity layer on top, so that nodes know which peers belong to the same group.  The [Waggle Finding Service (WFS)](WFS.md) uses both TransNet and Hive membership to locate Sentants by name and route events to them.
