# Status and next steps

[Overview](../README.md) · [Features](features.md) · [Architecture](architecture.md)

Status reference: **October 22, 2026**. These are development directions, not scheduled commitments or promises of completion.

## Established work

- Responsive Home Assistant dashboard and focused room/workflow pages.
- Lighting controls, presence/schedule-based routines, and manual overrides.
- Connected calendar, task, media, camera, weather, and personal-information interfaces.
- Local Obsidian knowledge organization and selected dashboard shortcuts.
- Initial encrypted off-device vault backup and verified restore.
- Existing local voice components and phone Assist use.

These statements describe documented work. They do not certify the health of every integration or complete backup coverage.

## Connected prototype

**Vera Calendar** is deployed and connected to Home Assistant in test mode. Next work includes a convenient editor shortcut, secure phone access, independent calendars, recurrence/timezone improvements, and durable backup/restore verification. Existing Google calendars remain in place.

## Reliability and maintenance

- Consolidate overlapping evening lighting rules and verify intended behavior.
- Establish a sustainable vault backup/retention cadence and another independent destination.
- Verify recovery coverage for Home Assistant and application data separately.
- Continue reducing UI clutter while preserving clear controls and manual fallbacks.

## Vera — in-development local AI assistant

Vera is intended to complement the homelab by helping with:

- Retrieval from curated personal knowledge.
- Planning and administrative preparation.
- Summaries and decision support.
- Eventual, scoped Home Assistant interactions.

The assistant and its future integrations are not complete. Dedicated inference hardware is not built or finalized. Local inference deployment, curated knowledge access, service permissions, and validation/approval workflows need their own implementation and verification.

No automatic private-note ingestion, background memory collection, unrestricted home control, or independent consequential action is assumed.

## Expansion only when useful

Future storage and computing hardware should solve a demonstrated capacity or reliability need. The aim is a dependable environment that supports everyday life, not infrastructure growth for its own sake.
