# FAQ

## Is this a full Git client?

No. Lost Minions Asset Locks focuses on Git LFS asset locking inside Unreal Engine. Use your normal Git tools for commits, pushes, pulls, branches, merges, history, pull requests, and conflict resolution.

## What does Check Out do?

For an eligible managed asset, Check Out requests a Git LFS lock and then refreshes lock state to confirm that you own it.

## What happens when another teammate owns the lock?

The normal workflow treats the asset as foreign-owned and read-only. Coordinate with the owner before editing it.

## Can I see team locks?

Yes. Open **Tools > Lost Minions Asset Locks > Git LFS Checkouts** to see All, Mine, and Others views with path and owner filters.

## What are Locked For and Locked At?

**Locked For** is a compact age such as `3 hr 18 min`. **Locked At** is the exact UTC time parsed from Git LFS lock metadata. Missing or invalid timestamps are shown as unavailable rather than invented.

## Why is an asset unavailable?

The plugin could not safely verify the necessary lock state or prerequisite. Refresh status and run setup diagnostics. See [Troubleshooting](Troubleshooting.md).

## What does administrative Force Release do?

It is a default-off, exceptional administrative action for one confirmed foreign Git LFS lock. It requires a warning and confirmation, asks Git LFS to force-unlock the path, and succeeds only after an authoritative refresh confirms the lock is absent.

## Does Force Release check the asset out afterward?

No. If you need the asset afterward, use the normal Check Out workflow after the force release has completed.

## What happens if I have local changes?

Ordinary release checks local state and can refuse to release a dirty asset. Resolve the local changes through your normal Git workflow first.

## Which Unreal Engine versions are supported?

Final `1.0.0` packaged plugins were built, loaded in clean C++ hosts, and focused-test validated on UE 5.6.1, UE 5.7.4, and UE 5.8.1. This does not claim compatibility with other engine versions; consult the release material supplied with your plugin package.

## Do I need a Lost Minions account or subscription?

No additional Lost Minions account, service, or subscription is required. Your Git hosting provider may require its normal account and authentication.

## Is read-only handling an absolute security boundary?

No. Read-only handling is defense in depth around the checkout workflow. It is not an uncircumventable security sandbox or a guarantee that every possible Unreal save or write path can be prevented.
