<div align="center">

# VLSI Study

**A native Android learning app for VLSI & digital design students**

Video lessons · Reference books · Topic-wise quizzes · Progress tracking

`com.shafi.vlsistudy`

</div>

---

## Overview

VLSI Study brings together everything a student needs to revise VLSI and digital
electronics into one app — instead of hunting across YouTube playlists, scattered
PDFs, and separate quiz apps. Lessons, reference books, and self-assessment quizzes
are organized by topic, and the app tracks each student's progress as they work
through the syllabus.

Built as a real, end-to-end Android project: Kotlin + Jetpack Compose on the
frontend, Firebase on the backend, and published to the Google Play Store
(Internal testing track).

## Features

- **Video Lessons** — topic-wise video lectures (YouTube, direct links, or uploaded
  video) across modules: Digital Electronics Basics, Combinational Circuits, CMOS
  Fundamentals, Sequential Circuits, Verilog HDL, Layout & Fabrication, and VLSI
  Design Flow.
- **Reference Books** — built-in PDF viewer for reference material, organized
  alongside video lessons under the same topics.
- **Topic-wise Quizzes** — multiple-choice quizzes per topic with difficulty
  levels, so students can self-test right after finishing a topic.
- **Progress Tracking** — records lesson and quiz activity so students can see how
  far they've progressed through the syllabus.
- **Notifications** — Firebase Cloud Messaging alerts for new content and support
  ticket replies.
- **Support Tickets** — students can raise a question in-app and get a reply,
  without leaving the app.
- **User Profiles** — editable name, email, and profile photo.
- **Admin Dashboard** — a separate admin role manages lessons, books, and quizzes,
  and responds to support tickets, enforced via Firestore security rules.
- **Secure Authentication** — Firebase Authentication for sign-up, login, and
  password reset.

## Tech Stack

| Layer               | Technology                                  |
|---------------------|----------------------------------------------|
| Language            | Kotlin                                        |
| UI Toolkit          | Jetpack Compose, Material 3                   |
| Architecture        | MVVM + Repository pattern                     |
| Navigation          | Navigation Compose                            |
| Async / State       | Kotlin Coroutines, StateFlow                  |
| Image Loading       | Coil                                          |
| Media Playback      | Media3 / ExoPlayer                            |
| Documents           | PDF Viewer library                            |
| Authentication      | Firebase Authentication                       |
| Database            | Cloud Firestore                               |
| File Storage        | Firebase Storage                              |
| Push Notifications  | Firebase Cloud Messaging (FCM)                |
| Build System        | Gradle (Kotlin DSL)                           |
| Distribution        | Google Play Console (Internal testing track)  |

## Architecture

The app follows MVVM with a repository layer, keeping the Compose UI free of
business logic:

```
UI (Compose Screens)
   │  observes StateFlow, sends user actions
   ▼
ViewModel
   │  talks only to the Repository layer
   ▼
Repository
   │  single source of truth per feature (lessons, books, quizzes, progress, tickets)
   ▼
Firebase (Auth · Firestore · Storage · FCM)
```

Firestore security rules restrict each student to their own progress and
tickets, while admin-only collections require the admin role.

## Screenshots

| Home | Learn | Quiz | Profile |
|:---:|:---:|:---:|:---:|
| ![Home](screenshots/home.png) | ![Learn](screenshots/learn.png) | ![Quiz](screenshots/quiz.png) | ![Profile](screenshots/profile.png) |

- **Home** — personalized greeting, topic search, and an "Explore Topics" grid
  covering all modules with lesson counts.
- **Learn** — Videos/Books tabs listing lessons grouped by topic, with runtimes
  shown for each video.
- **Quiz** — topic-wise quizzes with question counts and a one-tap "Start Quiz."
- **Profile** — profile info, notifications, help & support, and app info.

> Add the four screenshot PNGs to a `screenshots/` folder in the repo root for
> these to render on GitHub.

## Getting Started

### Prerequisites

- Android Studio (latest stable)
- JDK 17+ (Gradle JDK set to a compatible JetBrains Runtime, e.g. `jbr-21`)
- A Firebase project with Authentication, Firestore, Storage, and Cloud
  Messaging enabled

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/vlsi-study.git
   ```
2. Open the project in Android Studio.
3. Create a Firebase project at the [Firebase Console](https://console.firebase.google.com/),
   add an Android app with package name `com.shafi.vlsistudy`, and download the
   generated `google-services.json` into the `app/` directory.
4. Enable **Authentication** (Email/Password), **Cloud Firestore**, **Storage**,
   and **Cloud Messaging** in the Firebase console.
5. Sync Gradle and run the app on an emulator or device.

### Building a Release

```
Build → Generate Signed App Bundle or APK... → Android App Bundle
```
Use your own release keystore. This produces a signed `app-release.aab` ready
for upload to the Google Play Console.

## Project Status

Published on the Google Play Store under the **Internal testing** track
(`com.shafi.vlsistudy`) — installable and verified working end-to-end. Not yet
on Production / public search.

## Privacy Policy

[View the privacy policy](https://claude.ai/code/artifact/52ad864e-4ab0-4e51-aed4-219ccf39893e)

## Future Scope

- Full Production release on the Play Store
- Offline mode (local caching of lessons, books, and quizzes)
- Downloadable video lessons for offline playback
- Per-topic discussion / doubt-clearing forum
- Quiz leaderboards and gamification
- Adaptive, performance-based quiz difficulty
- In-app Verilog HDL code playground
- Multi-language support
- iOS version
- Admin analytics dashboard (usage, quiz scores, drop-off points)

## Author

**Bhanu Prasad , Shaik Shafi**
B.Tech ICT, Marwadi University
Built for the Mobile & Pervasive Computing (MPC) course project.

## License

This project is for academic purposes. Add a license of your choice (e.g. MIT)
if you plan to open it up for reuse or contributions.
