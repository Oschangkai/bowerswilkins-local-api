# Bluetooth Operations

All following commands use `POST` method to the command URL with `X-Client-ID` and `X-Request-ID` headers.

- **Base URL:** `https://{device_url}/mesh/node/{node_id}/channel/com.bowerswilkins.stated.service+provider/message`
- **Method:** `POST`
- **Headers:** `X-Client-ID`, `X-Request-ID`

## Get Bluetooth Status
Whether the speaker is in pairing mode.
- **Request Body:**
```json
{
  "method": {
    "parameters": {
      "property": "liberty.oobed.bluetooth.in_pairing_mode"
    },
    "name": "get_property"
  },
  "type": "query"
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.method.parameters`)
```json
{
  "property": "liberty.oobed.bluetooth.in_pairing_mode",
  "value": false
}
```

## Enter Pairing Mode
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "parameters": {
      "command": "liberty.oobed.bluetooth.command.enter_pairing_mode",
      "parameters": {
        "spaceID": "{space_id}"
      }
    },
    "name": "send_command"
  }
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message`)
```json
{
  "method": {
    "reply-to": "send_command",
    "name": "success",
    "parameters": {
      "command": "liberty.oobed.bluetooth.command.enter_pairing_mode"
    }
  },
  "type": "reply"
}
```

## Connected Bluetooth Devices
- **Request Body:**
```json
{
  "method": {
    "name": "get_property",
    "parameters": {
      "property": "liberty.oobed.bluetooth.connected_device_info"
    }
  },
  "type": "query"
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.parameters`)
```json
{
  "property": "liberty.oobed.bluetooth.connected_device_info",
  "value": {
    "btMacAddress": "74f61c001122",
    "displayName": "My BT Device",
    "Class": "524"
  }
}
```
