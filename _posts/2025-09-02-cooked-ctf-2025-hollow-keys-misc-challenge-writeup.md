---
title: "Cooked CTF 2025 Hollow Keys Misc Challenge Write-up"
date: 2025-09-02 20:00:00 +0500
categories: [CTF, CookedCTF_2025]
tags: [steganography, audio, video, radio, fldigi]
---

With this challenge we get a audio file `easy4.mp3`

It sounds like some radio transmission.

The title of the challenge is “Hollow Keys”, so some sort of keys may have been used to generate this transmission.

After researching on the Internet for a transmission that involves keys and a `printer` as mentioned in the challenge description, this looks like a Radio TeleType Transmission or RTTY.

```
An obscure channel broadcasts its existence. The printer's hum is the only response.
```

> **RTTY (Radio Teletype)** is a method of sending text over radio waves using audio tones. It  works by shifting between two tones to represent binary data (like 0s  and 1s), which is then decoded into letters and numbers. It’s like Morse code but uses tones instead of dots and dashes, often used in amateur  radio and communication systems.

To decode this transmission we will use the `FLdigi` tool.

> Fldigi (short for Fast light digital) is a free and open-source program which  allows an ordinary computer’s sound card to be used as a simple two-way  data modem.
>
> Using this software, it is possible for amateur radio operators to  communicate worldwide while using only a few watts of RF power.
>
> Fldigi software is also used for amateur radio emergency communications when  other communication systems fail due to natural disaster or power  outage. Transfer of files, emails, .etc. is possible using inexpensive  radio hardware.

Installation: `sudo apt install fldigi` or for Windows install it from SourceForge

![fldigi dashboard](/assets/img/cookedctf2025/hollowkey_1.webp)

There is also a separate hint in the form of a QR code that came with the challenge, which tells the **baud rate 45.45** and the **7 bits** per character to choose in the **custom** Tx (Transmission) settings. To set these values click on **Op_Mode->RTTY->Custom and under RTTY click on Tx and apply the settings.**

Now it is listening for incoming transmissions, so let’s start playing our audio file.

> **In Fldigi in Top left Click on File -> Audio -> Playback and choose the audio file**

When the audio is played, the software starts decoding it character by  character and in the end we get a base64 encoded value which when  decoded, gives us the flag.

![fldigi dashboard](/assets/img/cookedctf2025/hollowkey_2.webp)
