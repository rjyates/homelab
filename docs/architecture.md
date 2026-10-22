# Architecture and decisions

[Overview](../README.md) · [Features](features.md) · [Roadmap](roadmap.md)

## Responsibilities before integrations

| Component | Responsibility | Boundary |
| :--- | :--- | :--- |
| **Home Assistant** | Device integration, home automation, dashboard presentation, and links to specialized tools | Not a universal database or the complete AI assistant |
| **Obsidian** | Local personal knowledge, strategy, and technical reference | Not a live service registry or unrestricted AI memory |
| **Specialized applications** | Their own authoritative operational records and workflows | Dashboards should not silently duplicate or replace these stores |
| **Vera Calendar** | Prototype calendar editing backed by CalDAV | Still requires hardening before replacing established calendars |
| **Vera — planned assistance layer** | Curated retrieval, planning support, and proposed actions | No automatic access to every system or private note |

## Current computing context

Home Assistant runs on an existing **Bosgame mini PC**. A **Surface Pro** is the current personal-computing/Obsidian device. Supporting services use Home Assistant-managed apps where established; this is not a deployed multi-server cluster.

A future desktop, tablet, NAS, and dedicated AI inference hardware are plans, not current infrastructure. The Surface's possible secondary homelab role is uncommitted. Detailed hardware inventories stay private.

## Why the interface is organized this way

Room pages match physical use. Specialized pages keep more involved workflows out of the home overview. Shared colors and controls reduce the need to relearn navigation between desktop and phone.

Manual controls and a Pause mechanism matter because automation should not repeatedly fight a person's choice. Device capabilities also matter: a smart plug can switch a lamp, but cannot supply dimming or color control by itself.

## Local-first without pretending everything is offline

Local knowledge storage, local voice components, self-hosted services, and an experimental CalDAV calendar support ownership and portability. External calendar, email, wearable, weather, device, and coding services still create dependencies.

Each integration should be judged on usefulness, maintenance, privacy, and reliability rather than a blanket requirement to self-host everything.

## Calendar persistence and concurrency

The custom calendar uses standard calendar records, preserves event identity, and uses conditional writes to reject stale updates/deletes. Unsupported complex events are treated conservatively rather than silently losing fields.

Browser state is not the authoritative calendar store. Application restart persistence was checked separately from backup recovery, which remains unfinished.

## Knowledge access is explicit

Obsidian navigation links do not constitute ingestion or general file access. Future AI assistance should use deliberately curated material with an explicit scope. Git exclusions are organizational safeguards, not security controls.

The public repository contains newly written summaries, not exports of private knowledge notes or live dashboards.

## Operational discipline

Preserve recovery copies before risky configuration changes, validate affected configuration, and verify the user-facing result. Prefer supported configuration interfaces. Large dashboard storage changes require controlled maintenance rather than editing live state behind the application.

Separate four questions: is a service configured, is it running, does its workflow work end-to-end, and can its data be recovered? Evidence for one does not prove the others.

## AI proposes; trusted software executes

The intended Vera model is assistance with a defined boundary: interpret or retrieve information, propose an action, validate it through trusted software, and obtain human approval where consequences require it.

Existing coding/administration tools remain distinct from a deployed local assistant. No unrestricted agent access or autonomous application submission is implied.
