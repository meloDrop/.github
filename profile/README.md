# meloDrop

meloDrop is an Android app for music discovery. Every user drops one song a day on their public profile, and the others can listen to it and save it to their streaming library. No algorithm, just songs picked by people.

It's my end-of-first-year project at Holberton School. The code and the docs are written in English, but the MVP itself (the app interface) will be in French.

## How it works

A drop stays online for 24 hours, starting from the time it was posted. Once it expires, the user can post a new one.

In the Discover feed, you listen to a 30-second preview, then swipe right to save the song or left to skip it. Saved songs are added to your Deezer favorites.

To find the same track across platforms, meloDrop stores its ISRC, a code that identifies a recording and is shared by every streaming service.

## Stack

![Kotlin](https://img.shields.io/badge/Kotlin-Jetpack_Compose-f08c00?style=flat-square&logo=kotlin&logoColor=white&labelColor=0c0c10)
![FastAPI](https://img.shields.io/badge/Python-FastAPI-f08c00?style=flat-square&logo=fastapi&logoColor=white&labelColor=0c0c10)
![MySQL](https://img.shields.io/badge/MySQL-8.0-f08c00?style=flat-square&logo=mysql&logoColor=white&labelColor=0c0c10)
![Docker](https://img.shields.io/badge/Docker-Compose-f08c00?style=flat-square&logo=docker&logoColor=white&labelColor=0c0c10)

The Android app is written in Kotlin with Jetpack Compose and talks to the backend through Retrofit. The backend runs on Python and FastAPI, with SQLAlchemy and a MySQL database. Everything runs locally with Docker Compose.

Deezer is the main platform for the MVP. The Spotify integration is written but stays closed to users until Spotify grants extended access. Apple Music is planned for later.

The app only ever talks to the backend. The backend is the only part that calls Deezer or Spotify, so API keys never end up in the APK.

## Running the backend

```bash
cd backend
cp .env.example .env
docker compose up --build
```

Fill in `.env` before starting. The API docs are then available at `/docs`. If Docker keeps using an old image, rebuild with `docker compose build --no-cache`.

## Working on the repo

`main` only receives the final version at the end of each stage, merged from `dev`. Everything else starts from `dev`, on a branch named `feat/`, `doc/` or `build/` followed by the task, with underscores (for example `feat/auth_login`). Branches go back into `dev` through a pull request.

Commit messages start with `feat:`, `fix:` or `doc:`, for example `feat: add daily drop endpoint`.

Secrets stay in `.env`, which is ignored by git. Don't commit keys.

## Where it's at

The MVP is in development until the end of October 2026. The database schema, the FastAPI setup and user registration are done. Login and account management are next.

If you have a question or spot a bug, open an issue or reach out to `github.com/litoxam`.
