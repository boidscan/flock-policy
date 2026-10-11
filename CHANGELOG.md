# Changelog

## Policy 2, 2026-10-11

The flock starts sweeping. Signed by the founding maintainer alone and published without the 7-day review.

- Pause lifted. Probation and verification of results are in boidscan since v0.0.3.
- Internet catalog `0be1ee95bcbdb2e0833cb5f1ee9fe6e38ed6619b2d8b6ebee807f1d331caae42`, the one v0.0.3 builds. Policy 1 pinned a catalog from before the banner module got a 5 second target timeout, so no v0.0.3 boid could sweep under it.
- First seed: `http://157.180.95.126`.
- Unchanged: `min_version` v0.0.3, at most 10,000 packets per second, each unit scanned at most once every 7 days, no revoked boids.
- Expires 2026-10-25T17:54:10Z.

## Policy 1, 2026-10-11

Bootstrap policy, signed by the founding maintainer alone. It was published without the 7-day review, since the review process starts with this repository.

- The flock is paused until probation and verification of results are built into boidscan.
- `min_version` is v0.0.3, the first release that reads this policy.
- Internet catalog `a3baef084bba49b7c116d6c238b407327fcfd1a6fc04131653e7fda7b619db52`, at most 10,000 packets per second, each unit scanned at most once every 7 days.
- No revoked boids and no seeds.
- Expires 2026-10-25T12:10:28Z.
