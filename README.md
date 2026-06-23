# AudioVerse / SoundEng

Monorepo containing the Android mobile application and a PHP (Laravel) backend/frontend.

## Table of contents
- Overview
- Repository structure
- Prerequisites
- Android setup
- Business (Laravel) setup
- Build & Run
- Testing
- Environment & config
- Contributing
- License
- Maintainers / Contact

## Overview

This repository contains two main parts:
- `app/` — Android application (Gradle, Kotlin/Java, resources)
- `Business/BoardingHouse/` — PHP/Laravel backend and frontend assets

Use this README to get the project running locally, build releases, and contribute.

## Repository structure

- `app/` — Android app module
- `Business/BoardingHouse/` — Laravel app and frontend build files
- `gradle/`, Gradle wrapper and top-level Gradle configuration

## Prerequisites

- Java JDK 11+ (or project JDK configured in Android Studio)
- Android Studio with Android SDK (matching project configuration)
- Gradle wrapper included (use `./gradlew` or `gradlew.bat`)
- PHP 8.x
- Composer
- A relational database (MySQL or Postgres)
- Node.js (16+) and npm or yarn for frontend tooling

## Android setup

1. Open the project in Android Studio and import the Gradle project.
2. Ensure `local.properties` contains the Android SDK path (Android Studio usually handles this).

Build and run from command line:

```bash
# Unix/macOS
./gradlew clean assembleDebug
./gradlew installDebug

# Windows (PowerShell)
.\gradlew.bat clean assembleDebug
.\gradlew.bat installDebug
```

Notes:
- If you need signing for release builds, store keystore paths and passwords locally (do not commit them). Use `app/keystore.properties` or environment variables.

## Business (Laravel) setup

From the `Business/BoardingHouse` directory:

```bash
cd Business/BoardingHouse
composer install
cp .env.example .env
php artisan key:generate
# Edit .env and configure DB connection and other secrets
php artisan migrate --seed

# Frontend assets (if applicable)
npm install
npm run dev

# Start local server
php artisan serve --host=127.0.0.1 --port=8000
```

If using Docker for the backend, add instructions here for building and running containers.

## Build & Run

- Android: build via Android Studio or `./gradlew assembleRelease` for production artifacts.
- Backend: configure `.env`, migrate DB, then run `php artisan serve` or expose via your webserver.

## Testing

- Android unit tests:

```bash
./gradlew test
```

- Android instrumented tests (connected device/emulator):

```bash
./gradlew connectedAndroidTest
```

- Backend PHPUnit tests:

```bash
cd Business/BoardingHouse
./vendor/bin/phpunit
```

## Environment & config notes

- Do not commit secrets: use `.env` for the Laravel app and `local.properties`/keystore files for Android.
- Add any API keys, OAuth credentials, or third-party config notes here and indicate where to place them locally.

## Contributing

1. Fork the repo and create a feature branch: `git checkout -b feat/your-feature`
2. Keep commits focused and descriptive.
3. Run linters and tests before opening a PR.
4. Describe breaking changes and migration steps in PR description.

See `CONTRIBUTING.md` (create if needed) for more details.

## Known issues / TODO

- Document major TODOs or current limitations here.

## License

Add a `LICENSE` file at the project root. If you want a default, use the MIT license.

## Maintainers / Contact

Add maintainer names and preferred contact (email or GitHub handles).

---

If you'd like, I can:
- Add more precise SDK/JDK versions and Gradle targets
- Create a `CONTRIBUTING.md` and `LICENSE` file
- Add CI/CD notes (GitHub Actions / Bitrise / Fastlane) for Android releases
