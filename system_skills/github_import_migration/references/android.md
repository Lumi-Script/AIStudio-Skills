# Android Migration — Self-Contained

Instructions for migrating Android projects to AI Studio.

## Constraints
- Toolchain: JDK 21 (Temurin), Android SDK 36, AGP 9.1.1, Gradle 9.3.1, Kotlin 2.2.10.
- Output: app/build/outputs/apk/debug/app-debug.apk
- Keystore: ${rootDir}/debug.keystore with alias androiddebugkey and password android.
- Secrets: Secrets Gradle Plugin reading from .env and .env.example.
