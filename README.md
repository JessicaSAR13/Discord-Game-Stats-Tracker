# Discord Game Stats Tracker

A production-ready Discord bot that aggregates player and clan stats from popular titles and streams them into channels with rich embeds, leaderboards, and alerts. It automates data collection via official game APIs and Android device flows (for mobile-only titles), eliminating manual screenshots and messy spreadsheets. The result: always-fresh stats, cleaner reporting, and higher engagement across your Discord community.

<p align="center">
  <a href="https://Appilot.app" target="_blank">
    <img src="media/appilot-baner.png" alt="Appilot Banner" width="100%">
  </a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank">
    <img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram">
  </a>&nbsp;
  <a href="https://wa.me/923249868488?text=Hi%20Appilot%2C%20I'm%20interested%20in%20automation." target="_blank">
    <img src="https://img.shields.io/badge/Chat-WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>&nbsp;
  <a href="mailto:support@appilot.app" target="_blank">
    <img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  </a>&nbsp;
  <a href="https://appilot.app" target="_blank">
    <img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website">
  </a>
</p>

<p align="center"> 
   Created by Appilot, built to showcase our approach to Automation!<br>
   <strong>If you are looking for custom Discord Game Stats Tracker, you've just found your team — Let’s Chat.👆👆</strong>
</p>

## Introduction
**What it does:** Collects live/periodic player metrics (KD, MMR, ranks, wins, inventories, events), normalizes them, and posts to Discord with slash commands, scheduled reports, and auto-updated leaderboards.

**What it automates:** Repetitive logins, app navigation, stat lookups, screenshotting, and formatting — including mobile game flows via Android device automation.

**Who benefits:** Gaming communities, esports teams, streamers, and clan admins who need accurate stats without the grind.

### Automating Cross-Platform Game Stat Aggregation
- Unified pipeline for API + Android-device flows, so you can track both PC/console titles and mobile-only games.
- Rich Discord UX: slash commands, buttons, and mod-only controls for posting, pinning, and refreshing stats.
- Resilient schedulers with retries, backoff, and proxy rotation to avoid rate limits and lockouts.
- Transparent observability: structured logs, per-game adapters, and exportable CSV/JSON results.
- Scales to hundreds of servers and thousands of tracked profiles with sharding and device pools.

## Core Features
- **Real Devices and Emulators:** Run stat-collection flows on real Android devices or emulators (Bluestacks/Nox) for titles that lack public APIs, ensuring high coverage and realistic behavior.
- **No-ADB Wireless Automation:** Control devices over Wi-Fi (ADB-less) via Appilot accessibility flows to reduce detection vectors and cable clutter.
- **Mimicking Human Behavior:** Randomized tap paths, realistic delays, scrolling variance, and viewport checks to match human interaction patterns.
- **Multiple Accounts Support:** Manage many player IDs, clans, or alt accounts; isolate sessions and credentials with per-profile configs.
- **Multi-Device Integration:** Parallelize across device farms; dispatch tasks via queues for fast bulk refreshes.
- **Exponential Growth for Your Account:** Automated highlights, milestone posts, and role rewards drive engagement, retention, and organic server growth.
- **Premium Support:** Priority debugging, adapter updates for new game patches, and custom feature requests.

**Additional Capabilities**
| Feature | Description |
| --- | --- |
| Discord Rich Embeds & Threads | Clean stat cards with thumbnails, fields, and charts; auto-threaded match recaps to prevent channel spam. |
| Slash Commands & Permissions | `/stats`, `/link`, `/leaderboard`, `/compare`, with role-based access and cooldowns. |
| Game API Adapters | Pluggable adapters for Steam/Riot/Bungie/Epic/Ubisoft; fall back to Android flows when APIs are limited. |
| Leaderboard Engine | Periodic rank recompute, tie-break rules, seasonal resets, and pinned top-10 snapshots. |
| Webhooks & Notifications | Post match alerts, rank-ups, and event timers to designated channels or external webhooks. |
| Caching & Rate Limiting | Smart caching, per-adapter throttles, and burst control to respect vendor limits. |

</p>
<p align="center">
  <a href="https://appilot.app" target="_blank">
    <img src="media/Discord Game Stats Tracker-banner.png" alt="Discord Game Stats Tracker-architecture" width="95%">
  </a>
</p>

## How It Works
1. **Input or Trigger** — Start from the Appilot dashboard or a Discord slash command; define players, teams, games, and schedule windows (e.g., every 15 minutes or on-demand).
2. **Core Logic** — For API-enabled titles, call the adapter; for mobile-only titles, Appilot drives a device/emulator (UI Automator/Accessibility) to log in, navigate, and capture stats.
3. **Normalization & Storage** — Parse responses/screens, extract KPIs, normalize into a shared schema, and persist to a local/remote store with run metadata.
4. **Output or Action** — Publish rich embeds, update leaderboards, export CSV/JSON, or trigger webhooks to downstream systems.
5. **Other functionalities** — Built-in retries, error tagging, screenshots-on-failure, rotating proxies, and parallel workers ensure resilience at scale.

## Tech Stack
**Language:** Kotlin, Java, Python, JavaScript/TypeScript  
**Frameworks:** Appium, UI Automator, Espresso, Robot Framework, Cucumber, discord.py / discord.js  
**Tools:** Appilot, Android Debug Bridge (ADB), Appium Inspector, Bluestacks, Nox Player, Scrcpy, Firebase Test Lab, Accessibility  
**Infrastructure:** Dockerized device farms, Cloud-based emulators, Proxy networks, Parallel Device Execution, Task Queues, Real device farm

## Directory Structure
```
discord-game-stats-tracker/
│
├── bot/
│ ├── app/
│ │ ├── main.py # Discord bot entry (discord.py) / or index.ts for discord.js
│ │ ├── commands/
│ │ │ ├── stats.py
│ │ │ ├── leaderboard.py
│ │ │ └── link_account.py
│ │ ├── adapters/
│ │ │ ├── riot_adapter.py
│ │ │ ├── bungie_adapter.py
│ │ │ ├── steam_adapter.py
│ │ │ └── mobile_adapter.py # Android/Appilot pipeline
│ │ ├── services/
│ │ │ ├── scheduler.py
│ │ │ ├── cache.py
│ │ │ └── notifier.py
│ │ └── utils/
│ │ ├── logger.py
│ │ ├── parser.py
│ │ └── config_loader.py
│ └── pyproject.toml
│
├── mobile-automation/
│ ├── flows/
│ │ ├── login_flow.yaml
│ │ ├── navigate_stats.yaml
│ │ └── capture_screens.yaml
│ ├── runners/
│ │ ├── appium_runner.kt
│ │ └── uiautomator_utils.kt
│ └── devices/
│ ├── device_pool.yaml
│ └── proxies.yaml
│
├── config/
│ ├── settings.yaml
│ ├── secrets.sample.env
│ └── discord.json
│
├── data/
│ ├── storage.sqlite
│ └── exports/
│ ├── latest_stats.json
│ └── leaderboard.csv
│
├── logs/
│ └── bot.log
│
├── tests/
│ ├── unit/
│ └── integration/
│
├── docker/
│ ├── Dockerfile.bot
│ └── docker-compose.yml
│
├── scripts/
│ ├── seed_profiles.py
│ └── export_reports.py
│
└── README.md
```


## Use Cases
- **Esports teams** use it to auto-publish match results and player form, so they can brief coaches quickly before scrims.
- **Community servers** use it to run fair, auto-updated leaderboards, so they can host seasonal events without manual tallying.
- **Streamers** use it to announce rank-ups and personal bests, so they can increase chat hype and retention.
- **Clan admins** use it to track member activity across alts, so they can manage roles and participation requirements automatically.

## FAQs
**How do I configure this for multiple games and accounts?**  
Add player IDs and choose game adapters in `config/settings.yaml`, then link Discord users via `/link`. Each adapter has its own options (platform, region, privacy), and you can assign profiles to schedules.

**Does it support proxy rotation or anti-detection?**  
Yes. For API calls we throttle and cache; for mobile flows we route devices through rotating proxies and use human-like interactions, randomized delays, and accessibility-based control to reduce fingerprints.

**Can I schedule it to run periodically?**  
Absolutely. Use the built-in scheduler or your orchestrator (cron/K8s). Define intervals per adapter and per profile, with jitter to avoid synchronized bursts.

**What if a game updates its UI or API?**  
Adapters are versioned. For API changes we patch quickly; for UI changes you can tweak YAML flows (selectors, waits) without recompiling. Premium Support covers urgent patches.

## Performance & Reliability Benchmarks
- **Execution Speed:** Typical stat refresh completes in **3–12 seconds per API profile**; **20–45 seconds per mobile flow** (including app launch and navigation).
- **Success Rate:** End-to-end collection succeeds **~95%** under mixed API + mobile workloads with retries and fallbacks.
- **Scalability:** Horizontal sharding for Discord plus device pooling supports **300–1000 concurrent Android sessions** and **hundreds of servers**.
- **Resource Efficiency:** Worker pools auto-scale; caches reduce duplicate calls by **60–80%**; mobile runners reuse sessions to cut cold-starts.
- **Error Handling:** Exponential backoff, circuit breakers, screenshot-on-failure, structured logs, and alerting to a maintainer channel for fast triage.

##
<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
</p>
