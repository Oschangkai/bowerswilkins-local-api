# System Operations

All following commands use `POST` method to the command URL with `X-Client-ID` and `X-Request-ID` headers.

- **Base URL:** `https://{device_url}/mesh/node/{node_id}/channel/com.bowerswilkins.stated.service+provider/message`
- **Method:** `POST`
- **Headers:** `X-Client-ID`, `X-Request-ID`

## Check Software Update
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "name": "check_software_update",
    "parameters": {}
  }
}
```
- **Respond Body:** Responds via both HTTP and WebSocket (`payload.args.message.method.parameters`)
```json
{
  "update_available": false,
  "update_version": "",
  "update_release_notes": ""
}
```

## Software Update Status
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "name": "software_update_status",
    "parameters": {}
  }
}
```
- **Respond Body:** Responds via both HTTP and WebSocket (`payload.args.message.method.parameters`)
```json
{
  "update_is_active": false
}
```

## Reboot Device
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "parameters": {},
    "name": "request_restart"
  }
}
```
- **Respond Body:** Responds via WebSocket
