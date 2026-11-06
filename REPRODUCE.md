# Read-only reproduction protocol

Use a separately authorized test device and matching firmware, Android platform-tools and APK signature tools. No device was accessed for this public export. Keep the outputs private: even read-only commands can reveal identifiers, profiles and paths.

```sh
# TEST_ADB_SERIAL is a placeholder, not a real serial.
adb -s "$TEST_ADB_SERIAL" shell getprop ro.build.display.id
adb -s "$TEST_ADB_SERIAL" shell pm path com.google.android.gms
adb -s "$TEST_ADB_SERIAL" shell dumpsys package com.google.android.gms
adb -s "$TEST_ADB_SERIAL" shell cmd apexservice list --active
```

Check command availability with the matching firmware's help; output formats vary. Record installed/enabled state separately for each authorized profile, package base and update locations, version and signing certificate. Do not publish a full package/profile dump. For APKs lawfully obtained on the host, `apksigner verify --print-certs INPUT.apk` checks signatures; compare the public official microG release with the actual GMS package. Do not attempt installation to prove a predictable signature conflict.

Presence, enabled state, a running process and observed network activity answer different questions. For network analysis, document interface, duration, UID attribution, shared UIDs, positive control and unclassified traffic. A provider IP prefix is not proof of payload, hostname or purpose.

Rollback scope: historical changes modified only per-user enabled state. Seven tested reversions restored default state before reapplying the changes. Generic syntax is `pm default-state --user USER_ID PACKAGE`, only if the recorded original state was default. Both identifiers are placeholders to resolve from your own private evidence. It does not restore deleted data or remove an APEX. No batch disable/uninstall command, data-restoration or flash recipe is supplied; their prerequisites were not qualified.

Rollback requires Android/ADB access and sufficient privileges; the historical experiment used root. No recovery is implied when Android cannot boot.
