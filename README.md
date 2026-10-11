# Flock policy

The signed policy of the [boidscan](https://github.com/boidscan/boidscan) flock. The rules behind it are in [GOVERNANCE.md](https://github.com/boidscan/boidscan/blob/main/GOVERNANCE.md).

Every boid follows the newest policy signed by enough maintainers. A boid without a valid policy stops scanning and keeps serving its data. Every policy expires, so the flock stops on its own if nobody looks after it.

## Current state

Policy 1 pauses the flock. Boidscan runs only in closed test flocks for now, and no public seed is published.

## What is here

| File | Content |
|---|---|
| `policies/N.json` | every signed policy, by serial. Boids need the older ones to follow a change of maintainers, so none are deleted. |
| `policy.json` | the bundle boids download from https://boidscan.network/policy.json |
| `CHANGELOG.md` | what each policy changed, and why |

## Maintainers

| Key | Since |
|---|---|
| `p7pq44zppib4uviomfk4nqonpx4wdtlf5mtaiqevbzm2p2t2mhfq` | policy 1 |

One signature is enough for now. The keys are listed in each policy. The first set is built into boidscan ([root.go](https://github.com/boidscan/boidscan/blob/main/internal/flockpolicy/root.go)), and every later set must be signed by the set before it.

## Check a policy yourself

With a boidscan build that has the `policy` command (first release: v0.0.3):

```sh
boidscan policy verify policies/*.json
boidscan policy bundle policies/*.json 2>/dev/null | cmp - policy.json
```

The first command checks every signature, starting from the keys built into boidscan. The second checks that `policy.json` holds exactly these policies.

## Propose a change

Open a pull request that changes `policies/N.json` for the next serial, without signatures, and explain why in the description. A change is merged after at least 7 days of review. A maintainer then signs it offline and publishes it.

To have a boid removed from the flock, open an issue with the evidence. Abuse reports go to the boid's abuse contact first, which every boid names on its info page and in its scans.

## Publish a policy (maintainers)

```sh
boidscan policy new -from policies/1.json -out policies/2.json   # next serial, valid 14 days
# edit policies/2.json
boidscan policy sign -key /path/to/maintainer.key policies/2.json
boidscan policy verify policies/*.json
boidscan policy bundle policies/*.json > policy.json
```

Upload `policy.json` to https://boidscan.network/policy.json, add a CHANGELOG entry and commit. Boids check that URL hourly and pass the policy on to each other.
