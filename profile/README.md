# Tusk Framework

> **A domain-first PHP framework for applications that stay warm and ready.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/tusk-framework/tusk-framework/blob/main/LICENSE)
[![PHP](https://img.shields.io/badge/PHP-8.2%2B-777BB4.svg)](https://www.php.net/)
[![Documentation](https://img.shields.io/badge/docs-Tusk-green.svg)](https://tusk-framework.github.io/tusk-docs/)

---

## Build for the long run

In a traditional PHP-FPM request lifecycle, application bootstrapping is
commonly repeated for each request. Tusk takes a different path: RoadRunner
keeps PHP workers alive and ready to handle many requests, while the Tusk
Framework keeps application code explicit and domain-focused.

That means the application does not need to repeat all of its startup work for
every request, and workers can reuse initialized resources. It also means
developers must treat worker memory as long-lived: request-specific state must
not leak between requests. RoadRunner manages worker pooling and recycling; the
Framework owns the application request lifecycle.

Tusk is designed for teams who want the productivity of PHP with a runtime
model suited to APIs and services that benefit from persistent workers.

The platform separates application code from runtime operations:

```text
Client → RoadRunner → PHP worker running the Tusk Framework application
             ↑
       managed by Tusk Engine
```

- **Tusk Framework** provides application bootstrap, dependency injection,
  routing, request handling, and validation.
- **Tusk Engine** is the Go CLI and control plane. It validates project
  configuration, prepares the RoadRunner runtime, supervises its lifecycle,
  and provides diagnostics. It is not a second HTTP server or worker pool.
- **RoadRunner** owns HTTP transport and PHP worker management, including
  pooling and recycling.
- **Composer** creates PHP projects and manages their dependencies and scripts.

## Why this architecture?

- **Less repeated startup work:** a warm worker can serve multiple requests
  without rebuilding the whole application process each time.
- **Clear ownership:** the Framework handles application behavior, RoadRunner
  handles HTTP and workers, and the Engine operates the runtime around them.
- **Familiar PHP workflow:** use Composer for project creation and dependency
  management, with an explicit `bootstrap/app.php` entry point.
- **Built for real services:** keep domain code focused while choosing the
  persistence, database, and deployment approach that fits your application.

## Quick start

Ready to try it? Install PHP 8.2 or newer, Composer 2, the Tusk Engine, and
RoadRunner. See the
[installation guide](https://tusk-framework.github.io/tusk-docs/getting-started/installation/)
for platform-specific setup details.

Create and run an application:

```sh
composer create-project tusk/app catalog
cd catalog
tusk doctor
tusk start
```

That is it: the default application is available at
`http://127.0.0.1:8080`. The generated application uses
`bootstrap/app.php`; when you run `tusk start`, the Engine prepares the
RoadRunner configuration and supervises the runtime.

## Tusk ecosystem

| Project | Purpose |
| --- | --- |
| [Tusk Framework](https://github.com/tusk-framework/tusk-framework) | PHP components for building Tusk applications. |
| [Tusk Engine](https://github.com/tusk-framework/tusk-engine) | Go CLI and control plane for project configuration and runtime lifecycle. |
| [Tusk App](https://github.com/tusk-framework/tusk-app) | Composer skeleton for new applications. |
| [Tusk Docs](https://github.com/tusk-framework/tusk-docs) | Official guides, architecture, and API documentation. |
| [TuskPress](https://github.com/tusk-framework/tuskpress) | Example CMS application built for the Tusk platform. |

## Learn more

- [Documentation](https://tusk-framework.github.io/tusk-docs/)
- [Architecture overview](https://tusk-framework.github.io/tusk-docs/architecture/overview/)
- [Engine integration](https://tusk-framework.github.io/tusk-docs/guides/engine-integration/)
- [CLI guide](https://tusk-framework.github.io/tusk-docs/guides/cli-usage/)
- [GitHub organization](https://github.com/tusk-framework)
