<p align="center">
  <!-- REPLACE: add a light variant of the logo for dark mode (docs/media/logo-white.svg) and switch to <picture>; the current logo is unreadable on GitHub dark theme -->
  <img src="docs/media/logo.svg" width="220" alt="Krateo PlatformOps">
</p>

<h1 align="center">Krateo PlatformOps</h1>

<p align="center">
  An open-source control plane for platform engineering that runs on Kubernetes.<br>
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

Platform teams spend their time on tickets and copy-pasted templates, while every new project waits days for infrastructure that should be routine. Krateo PlatformOps turns that work into declarations: the platform team describes a resource once, as a blueprint, and developers request it from a portal, with the result reconciled by Kubernetes like any other object.

Under the hood, a composition engine turns each blueprint into its own Kubernetes API, any external service with an OpenAPI spec can be managed as a Kubernetes resource, and the portal itself is declared as Kubernetes resources, so it lives in Git with the rest of the platform.

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

Runnable examples, each with its preconditions and a single command, live with the components they exercise. Start with the [installer examples](https://github.com/krateo-platformops/installer/tree/main/examples).

## Docs

- [Documentation](https://docs.krateo.io/?utm_source=github&utm_medium=readme&utm_campaign=krateo&utm_content=docs) for concepts, guides and reference <!-- REPLACE: confirm the long-term docs domain -->
- [Release notes](RELEASE_NOTES.md) for what changed in each platform release
- Roadmap: [REPLACE: public roadmap link]

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
