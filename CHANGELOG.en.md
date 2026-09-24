# Changelog

This file records user-visible changes for public releases. Add a new version at the top for each release and keep the release tag aligned with the Flutter version.

## [2.0.0+2] - Initial public release

### Added

- Configurable content operations, home sections, rankings, recommendations, and source ingestion management.
- Multi-source playback, episode selection, resume playback, watch history, danmaku, comments, replies, reports, and feedback workflows.
- Membership entitlements, check-ins, tasks, gold-credit ledger, exchange store, invitation codes, invitation QR codes, promotion links, and rewards.
- Offline download queues, cache management, notification workflows, and Android push-service integration points.

### Improved

- User profile, membership identity, titles, and interaction-data synchronization.
- CoolAdmin management for content, users, membership, operations, collection sources, and community moderation.

### Upgrade Notes

- Server-side database migrations must be applied before deploying the matching backend version.
- Verify the APK SHA-256 value shown in the GitHub Release before installation.

## Version Format

- `2.0.0` is the user-visible version.
- `+2` is the Android build number and must increase for every distributable build.
