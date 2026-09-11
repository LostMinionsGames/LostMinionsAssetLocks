# Lost Minions Asset Locks

Official documentation, release notes, and support resources for Lost Minions Asset Locks.

Lost Minions Asset Locks is an Unreal Engine editor plugin for teams that already use Git and Git LFS. It brings Git LFS locking into familiar Unreal workflows for non-mergeable assets such as `.uasset` and `.umap` files.

The plugin is deliberately focused. It helps teams check out and release lockable assets, see team lock state, and diagnose setup problems. It does not replace your existing Git client or manage commits, pushes, pulls, branches, merges, history, or pull requests.

## Current status

The current descriptor version is final `1.0.0` and is not marked beta. This repository documents the plugin, release notes, and public support resources; it is not a plugin source distribution and does not imply Fab availability, pricing, or a Fab listing.

## What it provides

- Content Browser **Check Out** and **Release Checkout** actions for managed assets.
- Team-wide **Git LFS Checkouts** with All, Mine, and Others views, path and owner filtering, owner details, **Locked For**, and **Locked At** information.
- Content Browser lock badges and status tooltips backed by the Git LFS lock snapshot.
- Setup diagnostics for Git, Git LFS, repository discovery, comparison references, lock-service access, and lockable attributes.
- Conservative freshness checks before checkout and dirty-local-state protection before ordinary release.
- An exceptional, default-off administrative Force Release option for a confirmed foreign lock. It does not automatically check the asset out afterward.

Lost Minions Asset Locks does not require an additional Lost Minions account, service, or subscription. Your Git hosting provider may still require its normal authentication.

## Requirements

- An Unreal Engine project using a delivered plugin package.
- Git available to the Unreal Editor process.
- Git LFS installed for each contributor.
- A Git worktree and a remote that supports Git LFS locking.
- Managed asset paths configured for Git LFS and marked `lockable`.

See [Getting started](Docs/Getting-Started.md) for setup details.

## Documentation

- [Getting started](Docs/Getting-Started.md)
- [Configuration](Docs/Configuration.md)
- [Troubleshooting](Docs/Troubleshooting.md)
- [FAQ](Docs/FAQ.md)
- [Release notes](CHANGELOG.md)

## Support

Use [Issues](https://github.com/LostMinionsGames/LostMinionsAssetLocks/issues) for public bug reports, support questions, and feature requests. Never post passwords, tokens, cookies, credentials, private keys, authentication headers, secret-bearing configuration, or unsanitized logs.

## Scope

This repository contains documentation and support material only. It does not host the plugin implementation or source distribution.
