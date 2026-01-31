# WFS (Waggle Finding Service)

The Waggle Finding Service is the naming and routing layer that locates Sentants across the mesh and delivers events to them.

## What WFS Does

When you send an event to a Sentant by name, WFS resolves where that Sentant lives and routes the event there.  The target might be:

- On the same node (local delivery).
- On another node in the same Hive (intra-hive routing via TransNet).
- On a node in a different Hive (inter-hive routing, if reachable).

WFS handles all of this transparently.  You address a Sentant by name and WFS takes care of the rest.

## Resolution Order

WFS resolves names in a predictable order:

1. **Local** — check Sentants on this node first.
2. **Same Hive** — check other nodes in the Hive via the shared Sentant catalogue.
3. **Remote Hives** — if a path is known (from previous contact or via a cloud node), route the event there.

If the Sentant cannot be found at any level, an error is returned.

## Addressing

The simplest form is a bare name:

```
Thermostat
```

This resolves using the order above.  For explicit targeting, a qualified form is available:

```
MyHive|Thermostat
```

This tells WFS to look for the Sentant named "Thermostat" specifically in the Hive called "MyHive".

## Replies

When a Sentant receives an event, the sender's address is available as `@sender`.  Replying to `@sender` routes the response back to the originating Sentant regardless of how many hops the original event traversed.
