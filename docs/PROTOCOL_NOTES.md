# Protocol Notes

These notes summarize observed RT-950/950Pro behavior used by this editor.

## Serial basics

Normal radio communication uses:

```text
115200 baud, 8 data bits, no parity, 1 stop bit
```

## Handshake

The recovered factory CPS handshake begins with:

```text
PROGRAMBT9000U
```

The radio replies with:

```text
06
```

## Radio read/write

The editor reads and writes known blocks for:

- channels
- VFO
- optional features
- DTMF
- FM/AM/SSB modulation
- APRS
- zones and supporting blocks

Normal write flow:

1. fresh backup read
2. build edited image
3. write known blocks
4. read back and verify

## Boot picture upload

Confirmed boot image upload behavior:

- enter boot-picture mode with `D`
- send setup packets
- send 150 image pages
- each page is 1024 bytes of RGB565 image data
- each page is wrapped in an `A5 57` packet
- all 150 pages are acknowledged by the radio
- final `Over` packet may not return a final ACK, but the image upload succeeds when all 150 pages are ACKed

Boot picture size:

```text
240 × 320 pixels
RGB565 payload: 153,600 bytes
BMP export: 24-bit 240 × 320 BMP
```

## Boot picture readback

A mirrored readback command was tested and the radio returned an `A5 EE` status instead of image data. It may also leave the radio in program mode. For production safety, direct boot-image readback is not included.

## Safety rule

Do not add a new write or protocol action to the normal UI unless it has been tested on real hardware and has a safe recovery path.
