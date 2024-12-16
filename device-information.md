# Device Information

- **Base URL:** `https://{device_url}`

## Get Node
- **Method:** `GET`
- **Endpoint:** `/mesh/node`
- **Description:** Retrieves the node identifier (in UUID format)
- **Response:** `{node_id}`
```json
{
  "node": {
    "id": "{node_id}"
  }
}
```

## Get Metadata
- **Method:** `GET`
- **Endpoint:** `/1/mesh/nodes`
- **Description:** Retrieves detailed information about the nodes
- **Required Headers:** `X-Client-ID`
- **Response:** Detailed node information, including `{space_id}` and `{node_id}`
```json
{
  "nodes": [
    {
      "space-name": "My Zeppelin",
      "nodeID": "{node_id}",
      "type": "com.bowerswilkins.liberty.zep",
      "version": "11012",
      "protocol": "mesh.0.4",
      "available": "",
      "name": "L-ZEP",
      "space-id": "{space_id}",
      "role": "primary"
    }
  ]
}
```

## Get Version
- **Method:** `GET`
- **Endpoint:** `/software/version`
- **Description:** Retrieves software version information
- **Required Headers:** `X-Client-ID`
- **Response:** Software version information `{version}`
```json
{
  "version": "11012"
}
```

## Get Mesh Info
- **Method:** `GET`
- **Endpoint:** `/mesh/key/BWMeshInfo`
- **Description:** Retrieves mesh network information
- **Required Headers:** `X-Client-ID`
- **Response:**
```json
{
  "value": "{\n    \"meshSAE\": \"000a0a0a0aaaa\",\n    \"meshSSID\": \"1bbbb11b1b1bb\"\n}\n"
}
```

## Change Space Name
- **Method:** `PATCH`
- **Endpoint:** `/2/mesh/spaces/{space_id}`
- **Body:**
```json
{
  "name": "Space Name"
}
```
