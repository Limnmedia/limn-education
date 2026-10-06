# LIMN Education Development Environment

## Baseline

**Known-good foundation: This configuration successfully initializes and builds Frappe v15. Treat it as the LIMN Education project baseline until intentionally changed.**

This document describes the machine and environment as established on October 6, 2026.

## Purpose

This environment is the local development foundation for LIMNMEDIA’s education and course platform, provisionally named LIMN Education.

It supports development of multiple LIMNMEDIA courses, future Frappe LMS integration, LIMNMEDIA-specific educational workflows, the future `limn_education` custom Frappe app, local testing, GitHub collaboration, and eventual Frappe Cloud deployment.

Upstream Frappe and LMS code should remain unmodified. LIMNMEDIA-specific behavior belongs in `limn_education` whenever possible.

## Architecture

```text
macOS arm64
    ↓
Homebrew
    ├── MariaDB 11.8.9, isolated local database
    ├── Redis, available but not persistently configured
    └── native build dependencies
    ↓
uv → Python 3.11.17
    ↓
Node.js 18 via nvm → Yarn Classic 1.22.22
    ↓
frappe-bench 5.31.0
    ↓
Frappe Framework 15.121.3
    ↓
Future local Frappe site
    ↓
Future Frappe LMS v15-compatible branch
    ↓
Future limn_education custom app
    ↓
GitHub → Frappe Cloud
```

## Known-Good Versions

| Component | Verified value |
|---|---|
| Operating system | macOS |
| CPU architecture | Apple Silicon `arm64` |
| Homebrew prefix | `/opt/homebrew` |
| uv | `0.12.23` |
| Python | `3.11.17` |
| uv Python executable | `/Users/system/.local/bin/python3.11` |
| frappe-bench | `5.31.0` |
| Bench root | `/Users/system/Repos/LIMN-EDUCATION/bench` |
| Bench Python | `/Users/system/Repos/LIMN-EDUCATION/bench/env/bin/python` |
| nvm | `0.40.3` |
| Node.js | `18.20.8` |
| npm | `10.8.2` |
| Yarn | `1.22.22` |
| Frappe | `15.121.3` |
| Frappe branch | `version-15` |

Node and Yarn paths:

```text
/Users/system/.nvm/versions/node/v18.20.8/bin/node
/Users/system/.nvm/versions/node/v18.20.8/bin/yarn
```

The Frappe asset build completed successfully. No local site, LMS app, or `limn_education` app exists yet.

## Bench Layout

```text
/Users/system/Repos/LIMN-EDUCATION/bench/
├── apps/
│   └── frappe/
├── config/
├── env/
├── logs/
├── sites/
└── Procfile
```

Frappe belongs under `bench/apps/frappe`. Future applications should also be installed under `bench/apps/`.

## MariaDB Configuration

MariaDB 11.8.9 is the **LIMN Education selected local Frappe database**:

```text
Binary: /opt/homebrew/opt/mariadb@11.8/bin/mariadbd
Data directory: /opt/homebrew/var/mysql-frappe15
Socket: /opt/homebrew/var/mysql-frappe15/mysql.sock
Port: 3307
Bind address: 127.0.0.1
```

Frappe supports more than one database configuration depending on version and deployment context. This selection is specific to the LIMN Education local environment and is not a claim that MariaDB 11.8 is the only supported Frappe database.

A separate MariaDB 13 installation exists at:

```text
/opt/homebrew/var/mysql
```

It is unrelated to LIMN Education. It must not be used, migrated, upgraded, reinitialized, deleted, or pointed at by the Frappe Bench.

Any future MariaDB command must explicitly confirm the LIMN Education values:

```text
datadir = /opt/homebrew/var/mysql-frappe15
port    = 3307
socket  = /opt/homebrew/var/mysql-frappe15/mysql.sock
```

The versioned Homebrew formula’s default service configuration points toward `/opt/homebrew/var/mysql`, so it must not be started casually without confirming its data-directory arguments.

## Redis

Redis is installed, but no persistent global Redis service has been established for LIMN Education. Bench may later manage development Redis processes using its generated configuration files. Do not assume the global Homebrew Redis service is the correct Redis instance for the Bench.

## Safe Maintenance Boundaries

### Routine or generally safe maintenance

These may be updated deliberately when no project operation is in progress:

- Homebrew metadata
- `uv` itself
- nvm metadata
- Development-only command-line tools
- Browserslist data
- Git metadata
- Documentation
- Non-project system utilities

Check the environment afterward.

### Deliberate project upgrades

These require a planned change, testing, and a change-log entry:

- Python used by Bench
- Node.js or Yarn
- frappe-bench
- MariaDB or Redis
- Frappe patch or major versions
- LMS version
- Custom app dependencies
- Frappe Cloud configuration

Frappe and LMS upgrades can involve schema migrations and compatibility changes.

### Do not casually upgrade

Do not casually upgrade or modify:

- Frappe major version
- LMS major version
- MariaDB major version
- The existing MariaDB 13 installation or data directory
- Bench’s `env` manually
- Frappe or LMS source code directly
- Existing unrelated LIMNMEDIA repositories
- macOS or Xcode during active project work

## Maintenance Schedule

This project does not require an enterprise-style maintenance routine.

Run the health check:

- After relevant system or package changes
- When troubleshooting
- After returning to the project following a substantial gap
- Before significant upgrades
- Before deployments

It is not required before every ordinary course-development session.

## Health Check

This is a non-destructive foundation check:

```sh
cd /Users/system/Repos/LIMN-EDUCATION/bench

bench --version
bench version
./env/bin/python --version
node --version
npm --version
yarn --version

git -C apps/frappe branch --show-current
git -C apps/frappe describe --tags --always --dirty
git -C apps/frappe status --short

test -d apps/frappe/frappe/public/dist
test -d sites/assets

/opt/homebrew/opt/mariadb@11.8/bin/mariadb --version
```

When MariaDB is intentionally running:

```sh
/opt/homebrew/opt/mariadb@11.8/bin/mariadb-admin \
  --no-defaults \
  --socket=/opt/homebrew/var/mysql-frappe15/mysql.sock \
  --user=root ping
```

Do not use an unqualified `mysql` or `mariadb` command until its path and target socket are confirmed.

## Backup and Recovery

Git should protect custom app source code, hooks, DocTypes, fixtures, tests, metadata, documentation, migration patches, and dependency declarations.

Git does not automatically protect MariaDB databases, Frappe site files, uploaded course media, private videos, large source assets, local secrets, Redis state, the Bench virtual environment, or downloaded dependencies.

Eventually back up:

1. GitHub repositories and local Git history.
2. Each Frappe site database.
3. Each site’s `public/files` and `private/files`.
4. Course source media and original production assets.
5. Environment manifests and version records.
6. Non-secret configuration templates.
7. Secret-storage instructions, without committing secrets.
8. The MariaDB data-directory and port/socket configuration.

Course source media that is too large or private for Git should use an appropriate separate backup or asset-storage system.

Future database backups must explicitly target MariaDB 11.8 on port 3307 or its isolated socket. They must never default to `/opt/homebrew/var/mysql`.

## Reproducibility

Eventually maintain:

- This document
- A tool-version file or equivalent version record
- An `.nvmrc` for the intended Node version
- The Python version used by Bench
- Bench, Frappe, and LMS version records
- The custom app `pyproject.toml`
- Frappe compatibility metadata
- Dependency lockfiles where appropriate
- MariaDB version, port, socket, and data-directory documentation
- Redis strategy
- Setup and restore checklists
- Frappe Cloud deployment instructions
- Required macOS and Homebrew dependencies

Never commit site passwords, database credentials, API keys, private tokens, local `.env` files, or private course media unless intentionally stored in a secure repository.

## Upgrade Procedure

```text
backup
  ↓
change one layer intentionally
  ↓
verify locally
  ↓
test course functionality
  ↓
commit/version the change
  ↓
deploy only after approval
```

Every change should identify the component, current and target versions, reason, compatibility requirements, backup location, verification commands, and rollback approach.

Do not combine a Frappe major upgrade, LMS upgrade, MariaDB upgrade, Node upgrade, and custom app changes in one untracked operation.

## Troubleshooting Notes

### Homebrew permission reports

Codex’s restricted sandbox falsely reported Homebrew directories as unwritable. Normal Terminal verification showed Homebrew was healthy. Recheck from normal Terminal before changing ownership or permissions.

### MariaDB background processes

MariaDB 11.8 initialized successfully and returned `mysqld is alive`. Manually started background processes did not remain alive after a Codex command session ended. This appears to be an execution-environment process-lifecycle issue, not a MariaDB startup failure.

No custom LaunchAgent or additional service infrastructure is currently established.

### Redis unavailable during asset build

The Frappe asset build completed successfully while Redis was intentionally unavailable. Warnings such as `Cannot connect to redis_cache to update assets_json` were expected because no site or persistent development Redis process existed.

### Yarn peer dependency warnings

Yarn reported unmet peer dependencies involving `less`, `stylus`, and `vue-template-compiler`. The Frappe v15 asset build still completed successfully. Do not add arbitrary packages unless a real build or runtime failure appears.

### Browserslist warning

The asset build reported an outdated `caniuse-lite` database. Compilation still succeeded. This is maintenance noise, not currently an environment failure.

### Actual failures

Treat these as failures requiring investigation:

- Bench cannot report its version.
- Bench Python is missing or is not Python 3.11.x.
- Frappe is on the wrong branch.
- Asset compilation exits nonzero.
- MariaDB connects to the wrong data directory.
- Site migration fails.
- LMS installation or migration fails.
- Custom app tests fail.
- Frappe Cloud rejects app compatibility metadata.

## Future Maintenance Automation

Do not implement these yet. Small scripts may eventually be useful:

### `dev-status`

Report Bench path, Frappe/LMS/custom-app versions, tool versions, MariaDB target configuration, Redis status, and Git status.

### `dev-start`

Start only the intended local development services and verify MariaDB, Redis, and the Frappe site.

### `dev-stop`

Stop only services belonging to the LIMN Education Bench. It must not stop or modify MariaDB 13.

### `dev-doctor`

Run non-destructive checks for tool versions, Bench structure, Git status, Frappe branch, assets, MariaDB target, Redis, and disk space.

### `backup`

Create database dumps, site-file archives, and a version manifest. It must refuse to operate if the MariaDB data directory is not exactly `/opt/homebrew/var/mysql-frappe15`.

## Change Log

| Date | Component | Old version/state | New version/state | Reason | Verification result |
|---|---|---|---|---|---|
| 2026-10-06 | Python | Homebrew Python only for Frappe use | uv Python 3.11.17 | Frappe v15 development | Bench environment created successfully |
| 2026-10-06 | Bench | Not installed | frappe-bench 5.31.0 | Create local Frappe environment | `bench version` successful |
| 2026-10-06 | Node | Not installed | Node 18.20.8 via nvm | Frappe v15 frontend requirements | Asset build successful |
| 2026-10-06 | Yarn | Not installed | Yarn 1.22.22 | Frappe v15 frontend dependencies | `yarn install` successful |
| 2026-10-06 | Frappe | Not installed | Frappe 15.121.3, `version-15` | Initialize local Bench | Assets compiled successfully |
| 2026-10-06 | MariaDB | MariaDB 13.0.2 at `/opt/homebrew/var/mysql` | MariaDB 11.8.9 at `/opt/homebrew/var/mysql-frappe15` | Isolate selected local Frappe database | `mysqld is alive` while process was running |
|  |  |  |  |  |  |

Future entries should include the date, component, previous state, new state, reason, verification result, and backup or rollback reference where applicable.
