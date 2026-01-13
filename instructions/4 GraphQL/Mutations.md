# Mutations

### sentantLoad

- Loads a Sentant to the Reality2 node.  If a Sentant with that name already exists, it is not changed.  You have to unload the Sentant with that name first.
- Returns the Sentant
- Example:

```graphql
mutation SentantLoad($definition: String!) {
    sentantLoad(definition: $definition) {
        name
        id
        description
        events {
            event
            parameters
        }
        signals
    }
}
```

### swarmLoad

- Loads a swarm of Sentants to the Reality2 node.  Sentants you wish to 'overwrite' with the same name have to be unloaded first.
- Returns an array of Sentants
- Example:

```graphql
mutation SwarmLoad($definition: String!) {
    swarmLoad(definition: $definition) {
        name
        description
        sentants {
            name
            id
            description
            events {
                event
                parameters
            }
            signals
        }
    }
}
```

### sentantUnload

- Unloads a Sentant from a Reality2 node.  You need the Sentant's ID.
- Returns the Sentant details.
- Example:

```graphql
mutation SentantUnload($id: UUID4!) {
    sentantunLoad(id: $id) {
        name
        id
        description
        events {
            event
            parameters
        }
        signals
    }
}
```

### sentantSend

- Sends an event and parameters to a Sentant.
- The `id` parameter can be:
  - A simple UUID (e.g., `"abc12345-..."`) for local sentants
  - A combined `nodeId|sentantId` format for remote routing (e.g., `"nodeUUID|sentantUUID"`)
  - Names can also be used: `nodeName|sentantName` or any combination of IDs and names
- When a remote node reference is provided, the event is automatically forwarded via HTTP to the appropriate node in the mesh.
- Returns the Sentant details.
- Example (local sentant):

```graphql
mutation SentantSend($id: String!, $event: String!, $parameters: Json, $passthrough: Json) {
    sentantSend(id: $id, event: $event, parameters: $parameters, passthrough: $passthrough) {
        name
        id
        description
        events {
            event
            parameters
        }
        signals
    }
}
```

- Example (remote sentant via mesh):

```graphql
# Variables: { "id": "R2Node_ABC1|my_sentant", "event": "start", "parameters": {} }
mutation SentantSend($id: String!, $event: String!, $parameters: Json, $passthrough: Json) {
    sentantSend(id: $id, event: $event, parameters: $parameters, passthrough: $passthrough) {
        name
        id
    }
}
```



