<p align="center">
  <!-- REPLACE: add a light variant of the logo for dark mode (docs/media/logo-white.svg) and switch to <picture>; the current logo is unreadable on GitHub dark theme -->
  <img src="docs/media/logo.svg" width="220" alt="Krateo PlatformOps">
</p>

<h1 align="center">Krateo PlatformOps</h1>

<p align="center">
  An open-source control plane on Kubernetes that creates and governs any resource, on any infrastructure.<br>
  Platform teams publish golden paths once; developers get a self-service portal for everything else.
</p>

<p align="center">
  <!-- REPLACE: badges to be wired by engineering, in sync with the installer release pipeline -->
  <img alt="Build: placeholder" src="https://img.shields.io/badge/build-REPLACE-lightgrey">
  <img alt="Release: placeholder" src="https://img.shields.io/badge/release-REPLACE-lightgrey">
  <img alt="License: placeholder" src="https://img.shields.io/badge/license-Apache%202.0%20(REPLACE)-lightgrey">
  <img alt="Stars: placeholder" src="https://img.shields.io/badge/stars-REPLACE-lightgrey">
  <!-- REPLACE: CNCF Landscape badge, only once the listing is approved (requires 300+ stars) -->
</p>

<p align="center">
  <a href="#install">Install</a> ·
  <a href="https://docs.krateo.io/?utm_source=github&utm_medium=readme&utm_campaign=krateo&utm_content=docs-nav">Documentation</a> ·
  <a href="#community">Community</a> ·
  <a href="#contributing">Contributing</a> ·
  <a href="#agentiko">Enterprise</a>
</p>

<!-- REPLACE: hero GIF (20-30 s, no audio): a golden path requested from the portal and the resulting resources reconciling. Store under docs/media/ -->
<p align="center"><em>[REPLACE: hero GIF of a golden path from request to running resources]</em></p>

## What is this

Platform teams spend their time on tickets and copy-pasted templates, while every new project waits days for infrastructure that should be routine.

Krateo PlatformOps is a control plane that runs on Kubernetes and creates any resource on almost any infrastructure: Kubernetes clusters, applications, pipelines, databases, registries, API gateways. The only requirement is that the resource can be described in YAML as its desired state. Krateo validates every change, applies what was approved and keeps it true over time, inside and outside the cluster it runs on, on the major clouds and on-premises.

Roles stay clear. The platform team writes the templates, as blueprints; developers use them from a self-service portal and manage the whole lifecycle of what they created from one place, instead of searching across dozens of dashboards.

## Install

Requires a Kubernetes cluster (1.36 or later) and Helm. One command installs the whole platform:

```sh
helm install installer \
  oci://ghcr.io/krateo-platformops/charts/installer \
  --version 0.3.11 \
  --namespace krateo-system --create-namespace \
  --set bootstrap.coreProvider.enabled=true
```

On kind or bare metal, add `--set exposure.type=NodePort`. Upgrades, uninstall and every option are in the [installer documentation](https://github.com/krateo-platformops/installer/blob/main/docs/usage.md).

No cluster at hand? Try Krateo in the browser in the [free self-service lab](https://killercoda.com/krateoplatformops/). <!-- REPLACE: verify the lab runs the current installer -->

## What you get

- **Golden paths as Kubernetes APIs.** Each blueprint becomes a CRD with its own schema, versioning and RBAC.
- **Any API as a resource.** Generate a Kubernetes operator from an OpenAPI spec and manage external services declaratively.
- **A composable portal.** Navigation, pages and forms are Kubernetes resources, versioned in Git.
- **Ordered, self-healing installs.** Components roll out in dependency order and reconcile like the rest of the platform.
- **FinOps and observability blueprints.** Cost and telemetry data collected on the same control plane.

## Examples

Krateo installs the same way everywhere; what changes is the blueprints you add on top. Ready-to-use blueprints for AWS, Azure, Google Cloud, OpenStack, Keycloak and more live in the [krateo-blueprints](https://github.com/krateo-blueprints) organization.

## Docs

- [Documentation](https://docs.krateo.io/?utm_source=github&utm_medium=readme&utm_campaign=krateo&utm_content=docs) for concepts, guides and reference <!-- REPLACE: confirm the long-term docs domain -->
- [Release notes](RELEASE_NOTES.md) for what changed in each platform release
- Roadmap: [REPLACE: link to ROADMAP.md, to be created]

## Community

Questions and ideas go to [GitHub Discussions](https://github.com/krateo-platformops/krateo/discussions). For real-time chat, join us on [Discord](https://discord.krateo.io/). <!-- REPLACE: confirm the Discord invite domain -->

If Krateo PlatformOps is useful to you, star this repository: it helps other platform teams find it.

## Contributing

Bug reports, documentation fixes and new blueprints are the most valuable contributions right now. Read [CONTRIBUTING](https://github.com/krateo-platformops/.github/blob/main/CONTRIBUTING.md) before opening a pull request, and report vulnerabilities privately as described in the [security policy](https://github.com/krateo-platformops/krateo/security/policy).

## Develop & release

Platform releases are tag-driven and assembled by the installer; see [how a release ships](https://github.com/krateo-platformops/installer/blob/main/docs/release.md).

## License

Licensed under the [Apache License 2.0](LICENSE). <!-- REPLACE: LICENSE file is missing from this repository and must be added -->

<a id="agentiko"></a>
## AGENTIKO: agents on top of Krateo PlatformOps

Once the platform runs, most of the work is keeping it healthy and changing it safely. AGENTIKO is the reasoning plane built by Krateo on Krateo PlatformOps: its agents read the platform, investigate, and prepare the change. They propose, they prove, a person decides, and the loop closes.

AGENTIKO is a commercial product, in alpha at Kiratech since 3 August 2026.

[Learn about AGENTIKO](https://agentiko.eu/?utm_source=github&utm_medium=readme&utm_campaign=krateo&utm_content=agentiko-cta)
