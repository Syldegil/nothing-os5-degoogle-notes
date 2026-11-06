# Evidence — historical audit dated 2026-11-05

| Claim | Method | Result and scope |
|---|---|---|
| GMS factory origin | Package/APEX path inspection on A024, C5.0-260924-2115 | `com.google.android.gmssystem`, version 2632320, factory container `/product/apex/com.google.android.gmssystem.prodvic.apex`; GMS factory APK beneath `/apex/com.google.android.gmssystem/priv-app/`; active update under `/data/app` |
| Package conflict | Host inspection of official microG v0.3.17.252432 and installed GMS certificate | Same `com.google.android.gms` package, different signing certificates; ordinary update is not a migration path |
| Profile boundary | PackageManager state analysis | Data and enabled state can differ by profile; shared package-code identity does not become a separate compatible GMS/microG installation |
| Limited state changes | Before/after PackageManager comparison | Eight enabled-state differences, no install/uninstall or data clearing; seven reversions tested |
| Network | Bounded UID/socket observations | Google infrastructure connections remained; no zero-Google claim |
| microG on this phone | No installation attempted | NOT_TESTED / migration NO-GO because prerequisites and recovery were unresolved |

The raw application inventory, exact profile layout, accounts, usage, packet destinations and private hashes are deliberately excluded. This public guide is a rewritten historical summary, not a fresh hardware test. It does not borrow later emulator microG Self-Check results. New public checks validate documentation/links/privacy only, recorded in VALIDATION.md.
