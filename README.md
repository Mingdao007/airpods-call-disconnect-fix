# AirPods disconnect immediately during iPhone calls: try Standard Mic Mode

[中文说明](README.zh-CN.md) · [Codex skill](airpods-call-disconnect-fix/SKILL.md) · [MIT license](LICENSE)

**If AirPods play music normally but disconnect as soon as a call starts, try setting that calling app's microphone mode to `Standard`.** This resolved the reported iPhone Air + AirPods 4 case on iOS 26.6.2 on 2026-10-08.

This repository shares one user's troubleshooting experience and a small reusable Codex skill. The working setting is a case-confirmed workaround; the underlying iOS or firmware defect has not been identified.

## Quick fix

During a call, open **Control Center → [App] Controls → Mic Mode → Standard**. The app control might be labeled **WhatsApp Controls**, **Phone Controls**, or the name of another supported calling app.

**If connecting AirPods immediately breaks the call:** leave the AirPods in their case, start the call using the iPhone, select Standard for that app, end the call, then reconnect the AirPods and retry. Note the previous mode so the setting is easy to restore.

Microphone modes are saved **per app**. Check each affected app separately, including the Phone app. Standard retains normal voice processing; it does not disable the microphone. These controls and their persistence are documented by [Apple](https://support.apple.com/en-us/101993).

## Does this match your problem?

The reported symptoms were:

- Music and video playback through AirPods worked normally.
- Calls in **WhatsApp, WeChat, Douyin**, and the iPhone **Phone** app triggered an immediate disconnect.
- **FaceTime worked** on the same iPhone according to the reporter.
- The same AirPods worked for calls on a **MacBook and iPad**.
- The problem appeared at home; calls generally worked at school and other locations.
- Switching off Wi-Fi in Settings and using cellular data did not resolve it.
- Forgetting the AirPods, pairing again, and toggling Bluetooth did not resolve it.
- After a failure, Bluetooth could show **Connected** or **Not Connected**, while the expected AirPods audio output was unavailable.
- Wi-Fi, Bluetooth, and AirDrop indicators briefly changed together, then recovered.

This symptom combination makes the per-app microphone-mode setting a useful early check. Similar-looking disconnects can have other causes.

## Case AP-CALL-001

| Field | Recorded observation |
|---|---|
| Report date | 2026-10-08 |
| iPhone | iPhone Air |
| Earphones | AirPods 4; ANC variant and firmware version were not recorded |
| iOS | 26.6.2; the reporter also recalled failures on earlier unspecified versions |
| Trigger | Starting a call; the reviewed video also showed a transient interruption while an incoming WhatsApp call was still unanswered |
| Other calling paths | Ordinary Phone calls also failed; FaceTime was reported to work |
| Setting change | Selected Standard microphone mode |
| Result | The reporter immediately confirmed that the problem was resolved |

The original microphone mode was not recorded. The confirmation did not provide a separate post-change result for every app or a long-term observation period.

A private demonstration video was reviewed during troubleshooting. At approximately 00:45, Wi-Fi, AirDrop, and Bluetooth indicators were blue and Bluetooth showed AirPods. At approximately 00:46, the three indicators became gray and the AirPods icon disappeared from the media card. Wi-Fi appeared blue again around 00:49; Bluetooth, AirDrop, and the AirPods media icon returned around 00:50. No tap on those connection controls was visible at the interruption.

That sequence records visible connection-state changes. It does not establish a wireless-service restart, a chip failure, or the cause of the changes. The public case is recorded in text so it can be shared without the original video's personal information.

## What this result tells us

Selecting Standard was the successful change in this case. A microphone-processing setting is therefore a useful troubleshooting lead for this pattern.

Different apps can retain different microphone modes, which could help explain why FaceTime behaved differently. The modes actually selected in those apps were not captured, so that explanation remains a hypothesis.

The case does not establish that Voice Isolation, Automatic mode, AirPods 4 hardware, or iPhone Air hardware is generally defective. In particular, the previous mode is unknown. Apple documents the setting; the specific resolution here comes from the reporter's experience.

If Standard solves your problem, keep it for the affected app and check other affected apps separately. If it does not, a comparison with another Bluetooth headset on the same phone can help narrow the scope. A support report should include the calling app, exact device and software versions, and whether the wireless indicators change together.

## Reuse with Codex

The self-contained skill is in [`airpods-call-disconnect-fix/`](airpods-call-disconnect-fix/SKILL.md). Select that directory when installing this repository with a compatible Codex skill installer.

Example request:

> Use $airpods-call-disconnect-fix. My AirPods play music normally but disconnect immediately when I start a WhatsApp call on my iPhone.

The skill prompts Codex to check Standard Mic Mode early when the symptoms match, distinguish the observed workaround from a proposed cause, and avoid treating an unrecorded original mode as a confirmed culprit.

## Sources and additional reports

- ✅ Confirmed: [Apple — microphone modes and audio input controls](https://support.apple.com/en-us/101993). Supports the UI setting and per-app persistence.
- ✅ Confirmed: [Apple — 中文麦克风模式说明](https://support.apple.com/zh-cn/101993). Chinese version of the official setting instructions.
- Case AP-CALL-001 is a first-person troubleshooting report. The successful setting change was confirmed by the reporter on 2026-10-08.

If you add an issue, include your iPhone model, iOS version, AirPods model and firmware, app and version, previous microphone mode if known, and the result after selecting Standard. Include whether FaceTime and ordinary Phone calls behave differently. Share a short text description of any wireless-indicator changes.

Search terms: AirPods disconnect during calls; AirPods music works calls fail; iPhone Air AirPods 4 iOS 26.6.2; Bluetooth Wi-Fi AirDrop disconnect together; WhatsApp WeChat Douyin call disconnect; FaceTime works; Standard Mic Mode; Voice Isolation; AirPods 通话掉线; 耳机听歌正常打电话断开; 标准麦克风模式.
