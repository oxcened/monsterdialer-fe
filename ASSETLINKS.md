# Android App Links signing certificate

`public/.well-known/assetlinks.json` currently contains the locally verified
debug signing certificate for `dev.alenajam.monsterdialer`.

Before deploying this Hosting configuration for release builds, add the SHA-256
fingerprint for the production signing key to the same
`sha256_cert_fingerprints` array. The release key is restored only from GitHub
Actions secrets, so its fingerprint is not available in this repository.

To obtain it, decode the production keystore in a secure environment and run:

```sh
keytool -list -v -keystore release.keystore -alias "$ANDROID_KEY_ALIAS"
```

Copy the `SHA256:` value exactly, including colon separators. If the app is
distributed through Google Play with Play App Signing, use the **App signing
key certificate** SHA-256 fingerprint from Play Console instead (and keep the
upload-key fingerprint only if that key signs a separately distributed build).
