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

For DeepSeek Harness, Niro Bridge installs a small companion plugin into your local Harness profile. The install is explicit — it happens with your approval, keeps a backup of what it touches, and is removable. Harness's own approval and sandbox behavior keep applying; the companion adds no extra network listener.

## Approve from your phone

When an agent asks for permission — run this tool, write that file — you can allow or deny it from Niro for **DeepSeek Harness, ZCode, and OpenCode**. If you don't answer within 120 seconds, the decision falls back to your Mac. MiMo approvals stay on the Mac for now, so Niro shows them as "Approval required on Mac" instead of a button that couldn't act.

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
- **Away from home, bring your own VPN.** Niro has no cloud relay and no subscription. To use it away from your local network, keep your Mac reachable through a VPN layer you control — Tailscale or a plain WireGuard tunnel both work unchanged. Niro talks to the same Bridge endpoint over the tunnel as it does at your desk, so no port forwarding on the Mac and no public exposure of the Bridge is required.
- **Verify your download.** Bridge releases include a `SHA256SUMS.txt` next to the DMG.

## Free

Niro is completely free. Optional in-app tips support EFREM Labs and do not unlock features.

## About this repository

This public repository contains **Niro Bridge release binaries and product documentation**. The Niro iPhone app is distributed through the App Store. The application source code is not published here.

Made by **EFREM Labs**.
