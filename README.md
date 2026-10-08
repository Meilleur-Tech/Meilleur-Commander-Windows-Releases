# Meilleur Commander Windows Releases

Public, **binary-only** immutable release distribution for the Meilleur Commander Windows x86_64 client.

**Source and build:** [Meilleur-Tech/Meilleur-Commander](https://github.com/Meilleur-Tech/Meilleur-Commander). This repository is distribution storage, **not** a source checkout or a signing authority. Never publish application source, private signing keys, credentials, tokens, enrollment state, Gateway configuration, or unsigned customer manifests.

## Release and trust contract

- Each accepted Windows release is published under an immutable `windows-client-v<version>` tag with audited native binaries, exact SHA256 checksums, provenance and an RSA-signed release manifest.
- `channels/stable.json` is a **machine-readable discovery catalog**. It may identify a published release, but GitHub Releases “Latest” and this catalog **never authorize client installation**.
- Authorized Gateway independently verifies signature, exact immutable asset SHA256/URL, platform **windows**, architecture **x86_64**, Bridge protocol and Gateway compatibility, and performs **explicit per-Gateway activation**.
- Canonical RSA release key identity: `mc-client-caf94007b07dc90b`. The **private key remains exclusively with the authorized Owner release signer**, never in this repository or GitHub Actions.
- Windows client and Gateway versions are independent. A compatible client release does **not** require a Gateway container build, version bump or restart.
- Preserve immutable historic assets and URLs. Existing Windows clients may require a signed upgrade via their existing trusted legacy `pmeger/Meilleur-Commander-Releases` URL before accepting this repository; do not redirect an unupgraded installed client to an untrusted URL.
- The `stable` channel begins with `release: null`. This explicitly means **no organizational Windows public release has been signed and accepted yet**. Do not turn “Latest” into a release by merely copying files.

### Independent verification

Check the exact `channels/stable.json` manifest against the trusted public key set distributed with the native client, download the recorded immutable ZIP, validate the exact SHA256 and approved platform-specific GitHub release URL, then inspect the accepted Gateway's `/client/releases/windows/manifest.json` and `/client/releases/windows/package.zip`. A discovered GitHub version is not activated until the Gateway selects it.

Development issue: [#536](https://github.com/Meilleur-Tech/Meilleur-Commander/issues/536).
