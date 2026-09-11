# Configuration

Open **Project Settings > Plugins > Git LFS Asset Locks** to configure the plugin for the current project.

## Locking

### Content Root

The Content Root identifies the Content Browser mount point that participates in checkout actions. Keep it aligned with the Unreal content area your team intends to coordinate.

### Managed Extensions

Managed Extensions identifies the file extensions considered by the plugin. Git LFS attributes remain the source of truth: a managed extension alone does not make an asset lockable.

## Git LFS

### Git Executable

Git Executable identifies the Git executable used by the editor. It normally resolves to `git` on the system path. Restart the editor after changing it.

## Freshness

### Fallback Remote and Fallback Branch

Before checkout, the plugin prefers the active local branch's configured upstream for its comparison reference. Set **Fallback Remote** and **Fallback Branch** only when a usable upstream is unavailable. Set both values together or leave both empty; the plugin does not infer a fallback.

Use a named Git remote and a branch name such as `develop` or `release/content`. The fallback is rejected when it is incomplete or unsafe.

## Administrative

### Enable Administrative Force Release

**Enable Administrative Force Release** is off by default. Enable it only for trusted administrators handling an exceptional recovery case.

When enabled, **Force Release Lock** is available only for one foreign lock at a time from the team lock browser or, when eligible, as **Force Release Lock…** in the Content Browser. It requires confirmation showing the asset path, current owner, and lock age, with a warning that the owner may still have local or unpushed work and that removal can permit conflicting edits to a non-mergeable asset.

Force Release uses the Git LFS force-unlock mechanism. Git LFS or the remote server can still reject it. After a request, the plugin refreshes authoritative lock state and reports success only when the foreign lock is confirmed absent. It does not automatically check out the asset or make it writable for the administrator.

Use ordinary **Release Checkout** for locks owned by you. Administrative Force Release is not routine cleanup and is not a replacement for coordinating with the lock owner.

## Refresh and diagnostics

Use **Refresh Checkout Status** when you need an updated lock snapshot. The team browser also provides **Run Setup Diagnostics**, which checks the prerequisites relevant to checkout and reports a safe, actionable summary.

See [Troubleshooting](Troubleshooting.md) for diagnostic outcomes and recovery guidance.
