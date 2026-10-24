# Niro

**Your Coding Agents, on Your Phone.**

Niro is a free iPhone companion for the coding agents running on your Mac. Pick up a session, send the next instruction, check progress, and switch between supported providers without staying at your desk.

[**App Store**](https://apps.apple.com/app/niro/id6815434350) · [**Website**](https://niro-2uw.pages.dev) · [**Download Niro Bridge**](https://github.com/efrem-labs/niro-releases/releases/latest)

![Niro — Your coding agents, on your phone](assets/01-your-coding-agents.png)

## Supported agents

- **MiMo Desktop**
- **OpenCode** — including headless `opencode serve` sessions
- **ZCode** — per-session model choice across ZCode's own model catalog
- **DeepSeek Harness** — connected through a small, explicitly installed local companion

Niro Bridge normalizes the different local interfaces used by these agents into one phone-friendly connection. Provider credentials and model settings stay on the Mac — the phone never holds an agent's API keys.

## How it works

1. Install **Niro** on your iPhone.
2. Install **Niro Bridge** on your Mac.
3. Open Niro Bridge. It lives quietly in the macOS menu bar.
4. Pair your iPhone and Mac on the same local network.
5. Continue your existing coding-agent sessions from the phone.

For DeepSeek Harness, Niro uses a small companion plugin in your Harness desktop profile. In the current release you install it yourself, by running the installer bundled inside Niro Bridge and then restarting DeepSeek Harness:

```bash
node "/Applications/Niro Bridge.app/Contents/Resources/harness-plugin/install.cjs"
```

The installer only adds or updates Niro's own entry in that profile, keeps a backup, and is safe to re-run. The companion opens no TCP port — it talks to Niro Bridge over an owner-only Unix socket — and Harness's own approvals and sandbox keep applying. Other Harness profiles are not touched.

## Approve from your phone

When an agent asks for permission — run this tool, write that file — you can allow or deny it from Niro for **DeepSeek Harness, ZCode, and OpenCode**, while Niro is connected and in the foreground. An answer applies to that one request; it is not a permanent exemption. DeepSeek Harness hands a request back to the Mac when Niro has not been active for about 45 seconds, or when no answer arrives within 120 seconds; the other providers fall back to the Mac similarly, with timing details that can differ by provider. MiMo approvals stay on the Mac for now, so Niro shows them as "Approval required on Mac" instead of a button that couldn't act.

## Keep the conversation going

![Continue a coding-agent session from your iPhone](assets/03-keep-the-conversation-going.png)

Read the response, add a follow-up, and keep a task moving while you are away from the Mac.

## Your setup, your models

![Choose from supported providers and their available models](assets/04-your-setup-your-models.png)

Niro uses the providers and models already available through your Mac setup. Availability varies by provider and configuration.

## Niro Bridge for macOS

Niro Bridge is the small macOS companion that connects Niro on iPhone to supported coding agents running on the Mac.

- Menu-bar app
- Supports MiMo Desktop, OpenCode, ZCode, and DeepSeek Harness
- Local pairing with explicit approval on the Mac
- No Niro account required

Download the latest build from [**Releases**](https://github.com/efrem-labs/niro-releases/releases/latest).

## Network & security

- **Local network first.** Niro Bridge runs only on your Mac and advertises itself over Bonjour (`_niro._tcp`). The phone always connects to the exact endpoint discovery hands it. There is no Niro server: session traffic never passes through anything operated by EFREM Labs.
- **Pairing is explicit.** A new iPhone is paired only after you tap Allow on the Mac. The Bridge token is delivered at that moment and stored in the iPhone Keychain; unauthenticated requests to the Bridge are rejected.
- **Away from home, bring your own network.** Niro has no cloud relay and no subscription. To use it away from your local network, your Mac must remain reachable through a network layer you set up and control — for example Tailscale. Niro talks to the same Bridge endpoint as it does at your desk; Niro itself does not require exposing the Bridge to the public internet. Remote reachability is part of your network setup — Niro does not configure or verify it.
- **Verify your download.** The current release ships with a `SHA256SUMS.txt` next to the DMG.

## Free

Niro is completely free. Optional in-app tips support EFREM Labs and do not unlock features.

## About this repository

This public repository contains **Niro Bridge release binaries and product documentation**. The Niro iPhone app is distributed through the App Store. The application source code is not published here.

Made by **EFREM Labs**.
