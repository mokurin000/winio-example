# winio-example

This is an example project for `winio` targeting Android, Windows, macOS, Linux, and iOS.

The included CI workflow is ready to build and deploy prebuilt binaries for Windows, macOS, and Linux, as well as `aarch64`, `armv7`, and `x86_64` Android APKs.

You may also find [cargo-bundle](https://github.com/burtonageo/cargo-bundle) useful for packaging `.app`/`.ipa` bundles for macOS and iOS, or creating Windows installers.

## Getting Started

To set up your application ID, replace every occurrence of `rs.compio.winio.widgets` throughout the project.

> **Note:** For the best Linux compatibility, the application ID should be a valid D-Bus well-known name.

The `APP_ID` constant in `lib.rs` does **not** affect the runtime behavior on Windows, macOS, iOS, or Android. In particular, it is unrelated to the Windows AppUserModelID (AUMID).

## Rounded Corners

See [qrcode-gen@2939502](https://github.com/mokurin000/qrcode-gen/commit/2939502161d6f2b4345c9566dc6bdb761ae151dc) for a simple implementation that excludes the bottom rounded corners from the Android view size. You can also use it as a reference for implementing more sophisticated margin handling with proper DPI scaling.

## Android Signing Key

A default Android signing key is included for convenience. Before publishing your application, you should replace it with your own private signing key.

Update the `android.yaml` workflow to generate `key.properties` and restore the keystore file by decoding a Base64-encoded GitHub secret, e.g.

If you're unfamiliar with Android app signing or GitHub Actions secrets, feel free to ask an AI assistant for help.

To generate your own keystore, utilize keytool from Java Development Kit:

```bash
keytool -genkey -alias testkey -keyalg RSA -keysize 2048 -validity 36500 -keystore mykey.keystore -storepass storepass
```
