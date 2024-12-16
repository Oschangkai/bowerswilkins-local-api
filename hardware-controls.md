# Hardware Controls

All following commands use `POST` method to the command URL with `X-Client-ID` and `X-Request-ID` headers.

- **Base URL:** `https://{device_url}/mesh/node/{node_id}/channel/com.bowerswilkins.stated.service+provider/message`
- **Method:** `POST`
- **Headers:** `X-Client-ID`, `X-Request-ID`

## Get Downlight Status
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "name": "get_property",
    "parameters": {
      "property": "liberty.lights.hardware-downlight"
    }
  }
}
```
- **Respond Body:** Responds via both HTTP and WebSocket (`payload.args.message.method.parameters`)
```json
{
  "property": "liberty.lights.hardware-downlight",
  "value": {
    "supported": true,
    "brightness": 0.01,
    "enabled": true
  }
}
```

## Set Downlight
Set the speaker's ambient light, allowing you to adjust the brightness.
- **Request Body:** The value can be `true` or `false`, and the `brightness` value can range from `0.01` to `1`.
```json
{
  "method": {
    "parameters": {
      "property": "liberty.lights.hardware-downlight",
      "value": {
        "enabled": true,
        "brightness": 0.01
      }
    },
    "name": "set_property"
  },
  "type": "query"
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.method.parameters`)
```json
{
  "property": "liberty.lights.hardware-downlight",
  "value": {
    "supported": true,
    "brightness": 0.01,
    "enabled": true
  }
}
```

## Play Sound

Play a `ding` sound on the speaker.

- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "parameters": {
      "command": "liberty.oobed.command.play_sound",
      "parameters": {}
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
      "command": "liberty.oobed.command.play_sound"
    }
  },
  "type": "reply"
}
```
