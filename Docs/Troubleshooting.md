# Troubleshooting

Start with **Tools > Lost Minions Asset Locks > Git LFS Checkouts**, then choose **Run Setup Diagnostics**. The diagnostic report is the best first source for Git, Git LFS, repository, comparison-reference, lock-service, and attribute failures.

When requesting help, share only a concise, sanitized description and relevant sanitized diagnostic summary. Do not post passwords, tokens, credentials, cookies, private keys, authentication headers, private repository URLs, secret-bearing configuration, or full unsanitized logs.

## Git is unavailable

Install Git or correct **Git Executable** in Project Settings, then restart the editor if you changed the setting and run diagnostics again.

## Git LFS is unavailable

Install Git LFS for the workstation, complete your normal Git LFS initialization, and run diagnostics again.

## The project is not in the expected Git worktree

Open the intended project from its Git worktree. The plugin needs a resolvable repository root before it can safely determine paths and lock state.

## A comparison reference cannot be resolved

Check the active branch's upstream configuration first. If your branch has no usable upstream, configure both **Fallback Remote** and **Fallback Branch** with a named remote and branch. An incomplete fallback, URL-like remote, or unsafe revision expression is rejected.

## Lock service or authentication fails

Verify normal Git authentication and Git LFS locking support with your hosting provider. Refresh checkout status after fixing the underlying access issue. When lock status cannot be verified, the plugin treats it as unavailable rather than assuming a lock is safe to acquire or release.

## The selected asset is not lockable

Confirm that the selected file is in the configured content root, has a managed extension, and is covered by Git attributes that report both the Git LFS filter and `lockable` attribute. Commit attribute changes before retrying.

## The selected asset differs from the comparison reference

Sync or reconcile that asset through your normal Git workflow, then try checkout again. The plugin compares the selected asset rather than treating unrelated upstream changes as a checkout blocker.

## Another teammate owns the lock

The normal workflow leaves the foreign lock read-only. Coordinate with the owner. If an exceptional administrative recovery is necessary, see [Configuration](Configuration.md#enable-administrative-force-release); Force Release is default-off, confirmed, and does not check the asset out afterward.

## Ordinary release is refused because the asset is dirty

Commit or otherwise reconcile the selected asset's local changes through your normal Git workflow before using **Release Checkout**. This protection applies to owned locks; do not use administrative Force Release as a substitute.

## Lock status is unavailable

Refresh status and run diagnostics after resolving the underlying Git, Git LFS, network, repository, or authentication problem. The plugin fails closed while it cannot obtain authoritative state.
