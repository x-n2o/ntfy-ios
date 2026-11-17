# Cloud iPhone build

This branch adds a GitHub-hosted macOS build to upstream ntfy iOS `main` at
`96e659caf4b14405e201db6f5e4b2c6947c81643`. That source includes Critical Alerts
PR #44, merged as `780ac983ae0a11e2574a5c8d1a1736e9b5d27842`, and subsequent
upstream changes. Application source and entitlements are unchanged.

The workflow uses Xcode 26.3 on `macos-15`, resolves the committed Swift package
versions, and archives an unsigned iPhone application. The artifact includes the
unsigned IPA, build log, source revision, SDK versions, and dependency lock hash.

## Scope of the artifact

This is a compile verification artifact, not a ready-to-install or operational
notification app. The repository excludes its Firebase configuration, so the
workflow generates an explicitly nonfunctional placeholder. No production
credentials are used or included.

To produce a working iPhone installation, supply a real Firebase configuration
and matching APNs delivery setup, a signing identity and provisioning profiles
for the application and notification extension, and Apple-approved Critical
Alerts entitlements. A fork cannot inherit the upstream developer's signing or
entitlement approval. App group and bundle identifiers must match that setup.

Successful compilation does not establish real-device push delivery, mute or
Focus bypass, or end-to-end Healthchecks alerting. Verify each on the phone
after provisioning and installation.
