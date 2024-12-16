# Media Controls

All following commands use `POST` method to the command URL with `X-Client-ID` and `X-Request-ID` headers.

- **Base URL:** `https://{device_url}/mesh/node/{node_id}/channel/com.bowerswilkins.stated.service+provider/message`
- **Method:** `POST`
- **Headers:** `X-Client-ID`, `X-Request-ID`

## Get Volume
- **Request Body:**
The source can be empty, `{node_id}`, or `{node_id}+{via}`. The via parameter can include options such as `audiod-plug-in-bluetooth`, `audiod_plugin_airplay2`, and others.
```json
{
  "method": {
    "parameters": {
      "source": ""
    },
    "name": "get_volume"
  },
  "type": "query"
}
```
- **Respond Body:** Responds via WebSocket

## Set Volume
- **Request Body:** The value can range from `0` to `100`. The source can be empty, `{node_id}`, or `{node_id}+{via}`. The via parameter can include options such as `audiod-plug-in-bluetooth`, `audiod_plugin_airplay2`, and others.
```json
{
  "type": "query",
  "method": {
    "name": "set_volume",
    "parameters": {
      "muted": false,
      "source": "{node_id}",
      "value": 25
    }
  }
}
```
- **Respond Body:** Responds via WebSocket

## Play and Pause
The tileID can be empty, `{node_id}`, or `{node_id}+{via}`. The via parameter can include options such as `audiod-plug-in-bluetooth`, `audiod_plugin_airplay2`, and others.
- **Request Body:**
```json
{
  "method": {
    "parameters": {
      "command": "liberty.command.play_pause",
      "parameters": {
        "tileID": "{node_id}+audiod-plug-in-bluetooth"
      }
    },
    "name": "send_command"
  },
  "type": "query"
}
```
- **Respond Body:** Responds via WebSocket

## Next Track
The tileID can be empty, `{node_id}`, or `{node_id}+{via}`. The via parameter can include options such as `audiod-plug-in-bluetooth`, `audiod_plugin_airplay2`, and others.
- **Request Body:**
```json
{
  "method": {
    "parameters": {
      "command": "liberty.command.next_track",
      "parameters": {
        "tileID": "{{node_id}}+audiod-plug-in-bluetooth"
      }
    },
    "name": "send_command"
  },
  "type": "query"
}
```
- **Respond Body:** Responds via WebSocket

## Previous Track
The tileID can be empty, `{node_id}`, or `{node_id}+{via}`. The via parameter can include options such as `audiod-plug-in-bluetooth`, `audiod_plugin_airplay2`, and others.
- **Request Body:**
```json
{
  "method": {
    "parameters": {
      "command": "liberty.command.previous_track",
      "parameters": {
        "tileID": "{{node_id}}+audiod-plug-in-bluetooth"
      }
    },
    "name": "send_command"
  },
  "type": "query"
}
```
- **Respond Body:** Responds via WebSocket

## Get Artwork
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "parameters": {
      "property": "liberty.oobed.audiotile.artwork"
    },
    "name": "get_property"
  }
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.method.parameters`)
```json
{
    "property": "liberty.oobed.audiotile.artwork",
    "value": {
      "{node_id}+audiod-plug-in-bluetooth": {
        "artworkURI": "",
        "artworkMimeType": "image/unknown",
        "artworkData": "",
        "tileID": "{node_id}+audiod-plug-in-bluetooth"
      }
  }
}
```

```json
{
  "property": "liberty.oobed.audiotile.artwork",
  "value": {
    "{node_id}+audiod_plugin_airplay2": {
      "artworkURI": "https://{device_ip}/file/stream//tmp/temp_data_airPlayAlbum_2eb91ad88c83a55b2689a7d790fa501d",
      "artworkMimeType": "image/unknown",
      "artworkData": "",
      "tileID": "{node_id}+audiod_plugin_airplay2"
    }
  }
}
```

## Get Audio Tile
- **Request Body:**
```json
{
  "type": "query",
  "method": {
    "name": "get_property",
    "parameters": {
      "property": "liberty.oobed.audiotile"
    }
  }
}
```
- **Respond Body:** Responds via WebSocket (`payload.args.message.method.parameters`)
```json
{
  "property": "liberty.oobed.audiotile",
  "value": {
    "{node_id}+audiod-plug-in-bluetooth": {
      "albumURI": "",
      "trackURI": "",
      "duration": 245000,
      "album": "everything i wanted - Single",
      "shuffle": false,
      "itemJson": "",
      "composer": "",
      "audio_format": {
        "src_sample_rate": 0,
        "stream_type": 0,
        "src_bit_rate": 0,
        "src_sample_size": 0
      },
      "serviceID": "audiod-plug-in-bluetooth",
      "enabledPlaybackActions": [
        "previous_track",
        "next_track",
        "play",
        "pause"
      ],
      "repeatMode": "none",
      "artistURI": "",
      "artist": "Billie Eilish",
      "tileID": "{node_id}+audiod-plug-in-bluetooth",
      "sinkNodeIDs": [
        "{node_id}"
      ],
      "serviceLogoURL": "https://{device_ip}/file/stream/www/pages/webclient/img/Bluetooth.png",
      "elapsedTime": 241246,
      "state": 2,
      "playableJson": "{\"name\":\"\",\"startindex\":0,\"parameters\":{},\"userid\":\"\",\"id\":\"\"}",
      "title": "everything i wanted",
      "repeat": false,
      "serviceName": "Bluetooth"
    }
  }
}
```
