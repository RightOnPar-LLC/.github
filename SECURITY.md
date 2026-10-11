# Security policy

This policy covers every public repository in the RightOnPar-LLC organization and the services at `*.meshtool.ai`.

## Reporting a vulnerability

Please **do not open a public issue** for security problems.

Email **support@meshtool.ai** with:

- what you found and where (repo, package, or URL),
- steps to reproduce,
- the impact you believe it has.

You can also use GitHub's **private vulnerability reporting** ("Report a vulnerability" under a repository's Security tab) where it is enabled.

## What to expect

- Acknowledgement within **3 business days**.
- A status update within **10 business days**, including whether we've confirmed the issue and a planned fix window.
- Credit in the release notes when the fix ships — or anonymity, if you prefer.

## Supported versions

Only the latest published version of each npm package (`@meshtool/sdk`, `meshmarket`, `mesh-connector`) receives security fixes.

## Package provenance

New releases of `@meshtool/sdk` are published from GitHub Actions via npm trusted publishing, with a provenance attestation linking each version to the exact commit and workflow that built it. You can check this on the package's npm page.
