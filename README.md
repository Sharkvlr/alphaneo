# Alphaneo

**Self-updating RPA bot that bulk-closes work orders in a third-party web CMMS.**
Windows desktop app used daily by an HVAC operations team · current version **v1.0.12**

`Python` `Selenium 4` `pywebview / WebView2` `PyInstaller` `Inno Setup` `GitHub Releases API`

---

## The problem

Every preventive, corrective and patrol work order had to be closed by hand in a web maintenance system: one order at a time, the same fields, every day. Alphaneo does it in bulk, unattended.

## What it does

- Logs into the maintenance system and closes **preventive, corrective and patrol** orders in batches.
- Fills each flow automatically (technician, dates and service text) using per-flow business rules.
- Shows live progress, with pause and stop, while the browser runs visibly so the operator can follow along.

## How it's built

- **~14k lines of Python.** The bot runs in a **separate worker process** so the UI never freezes. The UI and the worker talk through lightweight file-based messaging, and credentials are never written to disk.
- **UI migrated from Tkinter to WebView2** (pywebview + HTML/CSS/JS): smooth GPU-rendered animations instead of a laggy Tk loop.
- **Browser automation** with Selenium 4 on Chrome and Edge, with automatic driver management.
- **Self-updating:** on start, the app checks the GitHub Releases API, compares versions, downloads the new installer and runs it silently.
- **Release pipeline:** one script bumps the version, builds the `.exe` (PyInstaller), compiles the installer (Inno Setup), commits to the private source repo and publishes the public release.

> Source code is private. This repository only hosts the installer and auto-update releases.

---

## 🇧🇷 Download

Baixe a última versão em **[Releases](https://github.com/Sharkvlr/alphaneo/releases/latest)**.
O Alphaneo se atualiza sozinho: deixe instalado e abra o app. Ele confere esta página e instala a versão nova sem você precisar fazer nada.

---

© 2025-2026 Gabriel Adley. All rights reserved. (Lei 9.609/98, Lei do Software — Brasil.)
