# TaskTopFight — beta releases

Test builds of TaskTopFight. **These are not the builds for players** — those
live in [TaskTopFight-Release](https://github.com/fishbill88/TaskTopFight-Release).

Every push to `main` in the source repo is built and published here, so what is
at the top of this list is the newest work, not the safest.

## Who gets these

Only machines that have asked for them. In the game's ⚙ settings panel there is
a checkbox, **Participate in beta test**, default off:

| the box | the app polls | gets a build |
|---|---|---|
| off | `TaskTopFight-Release` | when someone promotes one |
| on | `TTF-Beta-Release` (here) | within ten minutes of the push |

It is the same installer either way — the checkbox is remembered on the machine,
not baked into the download, so ticking it takes effect without reinstalling
anything. Unticking it does **not** roll you back: the app never downgrades, so
a beta tester who opts out simply stops moving until the stable feed catches up
and passes them.

## Promoting a build to players

Actions → **promote** → Run workflow.

Leave the version blank to send the newest beta, or type one (`0.4.7`) to send
an older build that turned out to be the good one. It copies that release's
files across to `TaskTopFight-Release` unchanged — same installer, same hash, no
rebuild — and every player picks it up within ten minutes.

It refuses rather than clobbers: a version already published to players has to
be deleted there first, and a release missing any of its four files is not sent
at all.

## What is in a release

| file | |
|---|---|
| `TaskTopFight-Setup-<version>.exe` | the installer |
| `latest.yml` | the update feed the installed app polls |
| `*.blockmap` | lets an update download only the changed parts |
| `TaskTopFight-RoomServer-<version>.zip` | the Tower room server, from the same commit |

The middle two are for the app, not for you. Don't delete them from a release:
that breaks auto-update for everyone still on an older beta.

---

Releases here are published automatically by CI. Nothing in this repository is
edited by hand except the workflow that promotes a build.
