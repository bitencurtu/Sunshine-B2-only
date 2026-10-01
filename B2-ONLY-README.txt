SUNSHINE B2-ONLY CUSTOM PATCH
=============================

Goal
----
On Windows, the audio streamed to Moonlight is ONLY the Voicemeeter B2 bus.
Anything with B2 enabled in Voicemeeter is heard by the Moonlight client.
Anything not routed to B2 is not captured by Sunshine.

Behavior changes
----------------
- Captures the active Windows recording endpoint named "Voicemeeter Out B2" directly.
- Legacy fallback: "Voicemeeter AUX Output".
- Does not capture the Windows default speakers/headset.
- Does not use Audio Sink or Virtual Sink for Windows audio routing.
- Does not install Steam Streaming Speakers.
- Does not switch the Windows default audio device.
- Stream Audio still controls whether audio is sent at all.

Voicemeeter setup
-----------------
Use the B2 button as the only stream mix control:
  B2 ON  = this source goes to Moonlight
  B2 OFF = this source does not go to Moonlight

Important
---------
Voicemeeter B2 must exist and be enabled as an active Windows recording endpoint.
If Sunshine logs that B2 cannot be found, open Windows Sound > Recording and make sure
Voicemeeter Out B2 (or legacy Voicemeeter AUX Output) is enabled.

This folder contains patched SOURCE CODE. A Windows binary/installer must be built on Windows
or by the project's existing GitHub Actions Windows workflow.
