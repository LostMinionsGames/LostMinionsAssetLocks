# Getting started

Lost Minions Asset Locks is for Unreal teams that already use Git and Git LFS. It coordinates Git LFS locks for configured Unreal asset paths; it does not replace the rest of your Git workflow.

## Before you begin

- Use a project located in the intended Git worktree.
- Ensure Git is available to the Unreal Editor process.
- Install Git LFS for each contributor and initialize it with your normal Git LFS setup.
- Use a remote that supports Git LFS locking and authenticate through that provider's normal Git credential flow.
- Configure the asset paths you want to protect with both Git LFS and the `lockable` attribute.

For example, a repository may contain rules like these in its applicable `.gitattributes` file:

```gitattributes
*.uasset filter=lfs diff=lfs merge=lfs -text lockable
*.umap filter=lfs diff=lfs merge=lfs -text lockable
```

Commit the attribute rules before the team starts using the checkout workflow.

## Install and enable

Follow the installation instructions supplied with the plugin package you received, then enable **Lost Minions Asset Locks** in Unreal Engine if it is not already enabled. Restart the editor when Unreal requests it.

This repository does not currently provide Fab installation instructions or imply that a Fab listing is available.

## Configure and verify

1. Open **Project Settings > Plugins > Git LFS Asset Locks**.
2. Confirm the managed content root and extensions match the assets your team intends to coordinate.
3. Confirm **Git Executable** resolves to the Git installation Unreal should use. Restart the editor after changing this setting.
4. Open **Tools > Lost Minions Asset Locks > Git LFS Checkouts**.
5. Select **Run Setup Diagnostics** and resolve any reported prerequisite before checkout.

## Normal workflow

1. Sync your branch through the team's normal Git tools.
2. In the Content Browser, select one or more managed assets and choose **Git LFS Locks > Check Out**. The native Unreal checkout flow can also participate when the active source-control provider is Git.
3. Edit and save assets checked out by you.
4. Use your normal Git tools to commit, push, review, and integrate the work.
5. When the work is integrated and the local asset is clean, select **Release Checkout**.

To view team lock state, open **Tools > Lost Minions Asset Locks > Git LFS Checkouts**. The same browser remains available from the managed asset context menu.

## Engine compatibility

The current plugin descriptor is final `1.0.0` and is not marked beta. Final packaged plugins were built, loaded in clean C++ hosts, and focused-test validated on UE 5.6.1, UE 5.7.4, and UE 5.8.1. This is not a claim of compatibility with other engine versions; check the release material supplied with your plugin package before adopting it for a project.

Next: [Configuration](Configuration.md) and [Troubleshooting](Troubleshooting.md).
