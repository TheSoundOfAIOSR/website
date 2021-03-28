---
title: "Design"
description: ""
date: 2021-01-29T00:00:00+00:00
weight: 1
bookToC: true
---
# Overview
{{<svg-pan-zoom "/design/overview.svg" >}}

## Interfaces
* Provider = Server = receives requests, sends events
* Consumer = Client = sends request, receives events
### Websocket - mic control
* Provider : STT
* Consumer : Production

Only required as first `start`, if `device` not available then default device is used.
{{<details "Record Start Device Request">}}
```json
{
    "request":{
        "id":543154,
        "cmd":"start",
        "device":"USB Mic 3"
    }
}
```
{{</details>}}
Further start,stop do not require the device
{{<details "Record Start Request">}}
```json
{
    "request":{
        "id":543154,
        "cmd":"start"
    }
}
```
{{</details>}}

In the response, the full request including the id shall be kept.

{{<details "Record Start Response">}}
```json
{
    "request":{
        "id":543154,
        "cmd":"start"
    },
    "response":"done"
}
```
{{</details>}}
### Websocket - Text sentence
* Provider : STT
* Consumer : TTS

{{<details "Text sentence Event">}}
```json
{
    "event":{
        "sentence":"Please, select a bright guitar instrument."
    }
}
```
{{</details>}}
{{<details "Text word Event">}}
```json
{
    "event":{
            "word":"Up"
        }
}
```
{{</details>}}

### Websocket - Text Descriptor
* Provider : TTS
* Consumer : SG

{{<details "Text Descriptor">}}
```json
{
}
```
{{</details>}}
### Post - Audio samples
* Client : SG
* Server : Prod
* Audio sample duration : 1 ~ 3 sec ?
* Frequency : 1 every 5 ~ 10 sec ?
* Parallel : yes
### MiDi Files
* Provided on disk offline
# Shared doc
{{< iframe src="https://docs.google.com/document/d/e/2PACX-1vSNeeMhR2SPafnUeVofwdOUEWpmig0nVz2M7ZBJ5FOuhovz9AM2DkqwYvi9mbM7h3y5q-z2vBnAMmbm/pub?embedded=true" height="900" >}}

