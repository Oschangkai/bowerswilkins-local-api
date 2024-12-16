# Bowers & Wilkins Local APIs

## Base URL Structure
- Device URL format: `{device_ip}:42425`
- Command URL format: `https://{device_url}/mesh/node/{node_id}/channel/com.bowerswilkins.stated.service+provider/message`
- WebSocket URL format: `wss://{device_url}/message`

## Headers
- `X-Client-ID`: Client identifier. This can be any string, but typically in UUID format.
- `X-Request-ID`: Request identifier (used for specific commands that respond via WebSocket). This can be any string, but typically in UUID format.

## API Endpoints
### Device Information
- [Get Node](device-information.md#get-node)
- [Get Metadata](device-information.md#get-metadata)
- [Get Version](device-information.md#get-version)
- [Get Mesh Info](device-information.md#get-mesh-info)
- [Change Space Name](device-information.md#change-space-name)

### Audio and Settings Commands
- [Get Available Sources](audio-and-settings-commands.md#get-available-sources)
- [Get Treble](audio-and-settings-commands.md#get-treble)
- [Set Treble](audio-and-settings-commands.md#set-treble)
- [Get Bass](audio-and-settings-commands.md#get-bass)
- [Set Bass](audio-and-settings-commands.md#set-bass)

### Media Controls
- [Get Volume](media-controls.md#get-volume)
- [Set Volume](media-controls.md#set-volume)
- [Play and Pause](media-controls.md#play-and-pause)
- [Next Track](media-controls.md#next-track)
- [Previous Track](media-controls.md#previous-track)
- [Get Artwork](media-controls.md#get-artwork)
- [Get Audio Tile](media-controls.md#get-audio-tile)

### Hardware Controls
- [Get Downlight Status](hardware-controls.md#get-downlight-status)
- [Set Downlight](hardware-controls.md#set-downlight)
- [Play Sound](hardware-controls.md#play-sound)

### System Operations
- [Check Software Update](system-operations.md#check-software-update)
- [Software Update Status](system-operations.md#software-update-status)
- [Reboot Device](system-operations.md#reboot-device)

### Bluetooth Operations
- [Get Bluetooth Status](bluetooth-operations.md#get-bluetooth-status)
- [Enter Pairing Mode](bluetooth-operations.md#enter-pairing-mode)
- [Connected Bluetooth Devices](bluetooth-operations.md#connected-bluetooth-devices)


## Example WebSocket Message
```json
{
  "payload": {
    "args": {
      "sendingNodeID": "{node_id}",
      "message": {
        "method": {
          "reply-to":" get_property",
          "name": "success",
          "parameters": {
            "property": "liberty.oobed.available_sources",
            "value": []
          }
        },
        "type":"reply"
      },
      "serviceID":"com.bowerswilkins.stated.service",
      "replyID":"{X-Request-ID}",
      "channel":"com.bowerswilkins.stated.service+subscriber",
      "messageID":"{uuid}"
    },
    "signature":"didReceiveSubscriberMessage(serviceID, sendingNodeID, messageID, replyID, channel, message)"
  },
  "type":"mesh"
}
```
