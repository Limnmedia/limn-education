LIMN Education development environment — public overview

This project uses Frappe v15 as a development baseline for the initial Fundamentals of Stop-Motion Camera course. The implementation is intended to evolve through a working educational vertical slice rather than prematurely defining a large platform.

## General prerequisites

- Supported macOS or Linux development environment
- Python and Node.js versions compatible with the selected Frappe v15 release
- Bench, MariaDB, Redis, and Yarn according to official Frappe installation documentation
- A dedicated project database and isolated environment

Follow the official Frappe installation and version compatibility guidance: https://docs.frappe.io/framework/user/en/installation

## Local operations and safety

Machine-specific paths, user directories, database sockets and ports, installed-version inventories, unrelated database instances, local maintenance procedures, and recovery instructions belong in LIMNMEDIA's **internal operations documentation**, not the public repository. Do not infer local configuration from this generic overview.

Never alter unrelated databases or running applications during setup. Record an approved local baseline privately before maintenance or upgrades. Keep credentials and backups outside Git.

For project scope and implementation decisions, see [DEVELOPMENT_STRATEGY.md](DEVELOPMENT_STRATEGY.md) and [PROJECT_PRINCIPLES.md](PROJECT_PRINCIPLES.md).
