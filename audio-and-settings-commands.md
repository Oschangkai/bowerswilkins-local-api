# Audio and Settings Commands

All following commands use `POST` method to the command URL with `X-Client-ID` and `X-Request-ID` headers.

- **Base URL:** `https://{device_url}/mesh/node/{node_id}/channel/com.bowerswilkins.stated.service+provider/message`
- **Method:** `POST`
- **Headers:** `X-Client-ID`, `X-Request-ID`

## Get Available Sources
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "name": "get_property",
    "parameters": {
      "property": "liberty.oobed.available_sources"
    }
  }
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.method.parameters`)
```json
{
  "property": "liberty.oobed.available_sources",
  "value": [
    {
      "localOnly": true,
      "arc": "none",
      "active": true,
      "autoSwitch": false,
      "deviceMac": "74f61c001122",
      "deviceName": "My BT Device",
      "serviceName": "Bluetooth",
      "tileID": "{node_id}+audiod-plug-in-bluetooth"
    },
    {
      "localOnly": false,
      "arc": "none",
      "active": true,
      "autoSwitch": false,
      "serviceName": "Airplay",
      "tileID": "{node_id}+audiod_plugin_airplay2"
    }
  ]
}
```

## Get Treble
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "name": "get_property",
    "parameters": {
      "property": "liberty.property.gain.treble"
    }
  }
}
```
- **Respond Body:** Responds via both HTTP and WebSocket (`payload.args.message.method.parameters`)
```json
{
    "property": "liberty.property.gain.treble",
    "value": 0
}
```

## Set Treble
- **Request Body:** The value can range from `0` to `600`.
```json
{
  "type": "query",
  "method": {
    "name": "set_property",
    "parameters": {
      "property": "liberty.property.gain.treble",
      "value": 0
    }
  }
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.method`)
```json
{
  "reply-to": "set_property",
  "name": "success",
  "parameters": {
    "property": "liberty.property.gain.treble"
  }
}
```

## Get Bass
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "name": "get_property",
    "parameters": {
      "property": "liberty.property.gain.bass"
    }
  }
}
```
- **Respond Body:** Responds via both HTTP and WebSocket (`payload.args.message.method.parameters`)
```json
{
  "property": "liberty.property.gain.bass",
  "value": 200
}
```

## Set Bass
- **Request Body:** The value can range from `0` to `600`.
```json
{
  "type": "query",
  "method": {
    "name": "set_property",
    "parameters": {
      "property": "liberty.property.gain.bass",
      "value": 200
    }
  }
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.method`)
```json
{
  "reply-to": "set_property",
  "name": "success",
  "parameters": {
    "property": "liberty.property.gain.bass"
  }
}
```
