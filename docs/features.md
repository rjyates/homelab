# Feature tour

[Overview](../README.md) · [Architecture](architecture.md) · [Roadmap](roadmap.md)

This tour describes existing work and known limitations. It does not expose personal content or serve as a live health report.

## Home interface

The main dashboard uses **Catppuccin colors and Bubble cards**, with related desktop and mobile layouts. Desktop makes room for a side panel; mobile prioritizes compact navigation and touch controls.

- Room tiles group controls by where devices are used, including a garage area ready for future devices.
- Individual lamp buttons show on/off state and supported lamp colors. Room icons provide grouped lighting control.
- A routines tile provides access to routines and their status.
- Planner, email, finances, and career pages provide focused destinations rather than expanding every tool on the home screen.
- A compact welcome banner provides contextual information; the Planner preview and camera area share the main workspace.
- Bottom controls provide access to Security, System Health, and Assist.

**Design focus:** consistent visual language, fewer duplicate controls, and useful information at a glance.

## Lighting and routines

Lighting combines daily schedules, sunset conditions, presence transitions, and named routines.

- Kitchen and living-room sunset lighting is conditioned on being home.
- Arrival behavior is triggered by a location transition, allowing manual changes while home without continuously reasserting the arrival action.
- Kitchen lighting includes scheduled morning behavior and a warm candlelight-style normal setting.
- Goodnight turns off household lamps and explicitly restores a chosen bedroom-lamp setting.
- Relax provides low-light behavior where the device supports it; a switch-controlled lamp cannot supply bulb-level color or dimming.
- Evening wind-down behavior uses purple on compatible lamps.
- A Pause control provides an understandable override for automatic routines.

The configuration has grown iteratively. **Overlapping evening rules were identified and still need consolidation**; this documentation does not imply that conflict review is complete.

## Planner and household organization

The Planner groups calendars, tasks, flexible weekly chores, lists, and notes. The home preview uses a compact event timeline with expandable details and duration-sensitive event boxes.

Calendar presentation distinguishes all-day items and completed events. Assignment-like items are presented as all-day entries with deadlines in their titles where applicable. This display behavior is distinct from rewriting the source calendar.

Weekly chores can be completed flexibly and recur after completion, rather than requiring a rigid daily checklist. Longer-horizon planning helps bring future administrative needs into view. Personal event titles and household task records remain private.

## Vera Calendar — connected prototype

A custom frontend provides day/week/month/agenda views, event details, and create/edit/delete workflows. Its backend uses **Radicale and standard CalDAV/iCalendar** rather than treating the browser as permanent event storage.

Verified work includes:

- Deployment as a Home Assistant local app accessed through Ingress.
- Event persistence across an app restart using synthetic records.
- Home Assistant CalDAV connection and addition of the calendar to the Planner.
- Integration tests covering CRUD, UID preservation, stale-revision rejection, all-day boundaries, supported recurrence, and invalid daylight-saving times.

The prototype currently uses **one calendar**; colored categories are not independent calendars. Recurrence exceptions, richer phone access, broader timezone behavior, backup/restore coverage, and production hardening remain unfinished. Advanced events the adapter cannot preserve are read-only.

Google calendars remain in place. No migration or full replacement is claimed.

## Media and security interfaces

Living-room pages bring music and television controls together, using existing Music Assistant and TV integrations. Camera pages bring existing Frigate and camera integrations into the same interface, alongside event-notification workflows.

Camera feeds, placement, recordings, notification destinations, and operational security settings are not published here. A configured entry is not proof of stream availability.

## Focused personal dashboards

- **Email:** summaries from multiple mailboxes, separating personal and work views. Account identities and messages stay private.
- **Financial administration:** monthly review, bill/provider navigation, and review history. No balances or records are published.
- **Career & learning:** professional links, résumé access, opportunity review controls, and access to learning/homelab material. This does not claim unattended applications or a verified autonomous discovery pipeline.
- **Wearable information:** a compact daily Oura summary opens a more detailed view. This is presentation, not medical advice or an AI health system.
- **Weather:** home and away context, radar access, and severe-weather features. Location and notification details stay private.

Some private pages have a dashboard privacy lock. **This is a presentation barrier, not authorization or data isolation from administrators/API credentials.**

## Voice, knowledge, and operations

Home Assistant Assist has been used successfully on the phone. Piper, Speech-to-Phrase, and Wyoming components provide a local voice path; this is separate from a conversational local LLM.

The Second Brain page opens selected **Obsidian** notes through local application links. It requires the appropriate vault on the opening device and does not mirror the vault into Home Assistant.

A **System Health** page provides a dedicated monitoring interface. Tailscale supports private remote connectivity. Supporting services include messaging, administration tools, and a self-hosted password manager; their credentials and access configuration are outside this repository.

## Recovery work

The Obsidian vault has an **encrypted restic backup on a separate device**, with an initial isolated restore compared byte-for-byte. That is evidence for the tested snapshot, not proof that subsequent edits are backed up.

Backup scheduling, retention, an independent disaster-recovery destination, and full Home Assistant/app recovery coverage are unresolved. Dashboard recovery copies, Git history, vault backups, and full service backups are different layers.
