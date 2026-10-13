# Tusk Framework

Tusk is a domain-first PHP framework and application platform for APIs and
services that run on persistent PHP workers managed by RoadRunner.

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

## Quick start

Install PHP 8.2 or newer, Composer 2, the Tusk Engine, and RoadRunner. See the
[installation guide](https://tusk-framework.github.io/tusk-docs/getting-started/installation/)
for setup details.

Create and run an application:

```sh
composer create-project tusk/app catalog
cd catalog
tusk doctor
tusk start
```

The default application address is `http://127.0.0.1:8080`. The generated
application uses `bootstrap/app.php`; the Engine prepares the RoadRunner
configuration when starting it.

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
