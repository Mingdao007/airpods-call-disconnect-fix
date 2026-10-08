---
name: airpods-call-disconnect-fix
description: "Troubleshoot AirPods that play media normally but disconnect immediately during iPhone calls, including WhatsApp, WeChat, Douyin, or Phone calls. Check Standard Mic Mode using a documented iPhone Air and AirPods 4 case."
---

# AirPods Call Disconnect Fix

Use for call-specific AirPods disconnects. Prioritize the smallest setting comparison when media playback works and calls fail immediately.

## Known case

On 2026-10-08, an iPhone Air user on iOS 26.6.2 reported immediate AirPods 4 disconnects in WhatsApp, WeChat, Douyin, and ordinary Phone calls. FaceTime reportedly worked; the same earphones worked for calls on MacBook and iPad. The issue was location-dependent and persisted with iPhone Wi-Fi off and cellular data in use. Forgetting, re-pairing, and toggling Bluetooth did not resolve it.

A private video showed Wi-Fi, AirDrop, and Bluetooth indicators briefly becoming gray together and recovering while an incoming WhatsApp call was still unanswered. The user then confirmed that selecting **Standard** microphone mode immediately solved the problem. The original mode, firmware, and app-by-app post-change results were not recorded.

## Useful first comparison

Guide the user to **Control Center → [App] Controls → Mic Mode → Standard** during a call. Record the previous setting. If connecting AirPods immediately disrupts the call, use the iPhone alone to set that app's mode first, then end the call, reconnect the earphones, and retry.

Microphone modes persist per app. Check each affected calling app separately, including Phone. Standard still uses normal voice processing. [Apple's official instructions](https://support.apple.com/en-us/101993) document the controls and persistence.

Capture the user's actual result. If it works, report a locally confirmed workaround for that app and device combination. If it fails or the symptoms do not match, continue ordinary troubleshooting; a different Bluetooth headset on the same iPhone or a FaceTime comparison can help distinguish affected paths.

## Evidence boundaries

- Treat this as one user-confirmed case, not an Apple-confirmed universal fix.
- Do not identify Voice Isolation or Automatic as the original culprit: the old mode was not recorded.
- Different per-app modes could explain a FaceTime contrast, but this case did not capture those modes.
- Icon changes alone do not prove a wireless-service restart or hardware failure.
- Use the documented result before repeating already unsuccessful pairing or reset suggestions for a matching case.

Public case and translations: [GitHub](https://github.com/Mingdao007/airpods-call-disconnect-fix). Report date and versions describe the recorded case, not the latest software.
