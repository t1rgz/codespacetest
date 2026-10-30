# codespacetest
testing codespaces

This repository includes a devcontainer for Android development with Kotlin.

## Included tooling

- OpenJDK 17
- Android SDK command-line tools
- Android platform tools (`adb`)
- Android SDK platform 35 and build tools 35.0.0
- VS Code Kotlin and Gradle extensions

Open the repository in a devcontainer to install the toolchain. For an Android project that uses the Gradle wrapper, build it with `./gradlew assembleDebug`.

The container is intended for builds and device-connected workflows. Android emulators generally need hardware virtualization (KVM), which is not available in many Codespaces environments.