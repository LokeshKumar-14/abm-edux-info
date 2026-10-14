<p align="center">
  <img src="app%20pictures/app%20icon.png" alt="ABM EduX Logo" width="120">
</p>

<h1 align="center">ABM EduX</h1>
<p align="center">Smart Learning &amp; Education Management Platform</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white" alt="Platform">
  <img src="https://img.shields.io/badge/Kotlin-Jetpack%20Compose-7F52FF?logo=kotlin&logoColor=white" alt="Kotlin">
  <img src="https://img.shields.io/badge/Backend-Firebase-FFCA28?logo=firebase&logoColor=black" alt="Firebase">
  <img src="https://img.shields.io/badge/Live%20Classes-Agora%20RTC-E4B94F" alt="Agora RTC">
  <img src="https://img.shields.io/badge/Payments-Razorpay-0B1436" alt="Razorpay">
</p>

<p align="center">
  <a href="#about">About</a> ·
  <a href="#problem-statement">Problem</a> ·
  <a href="#student-features">Student</a> ·
  <a href="#live-classes--recording">Live Classes</a> ·
  <a href="#admin-panel">Admin</a> ·
  <a href="#tech-stack">Tech Stack</a> ·
  <a href="#screenshots">Screenshots</a> ·
  <a href="#download">Download</a>
</p>

---

## About

ABM EduX is a complete Android learning platform that brings students, teachers/admins, courses, live classes, study materials, tests, assignments, payments and learning analytics into a single application.

Students get a structured, modern learning experience; administrators get one set of tools to manage courses, content, live classes, students, payments and academic activity.

## Problem Statement

Traditional coaching setups lean on a different tool for every job — WhatsApp for communication, one app for videos, another for PDFs, manual tracking for tests and assignments, a separate app for live classes, and payments handled outside all of it. Students end up with no single place for their learning journey, and teachers juggle too many tools to manage it. ABM EduX brings all of this into one integrated platform.

## Student Features

- **Authentication** — Firebase Phone Authentication with OTP, session handling and a unique Firebase UID per student
- **Dashboard** — one navigation point for courses, live classes, videos, tests, assignments, study materials, leaderboard, announcements, profile and community
- **Courses** — browse and open courses with title, description, pricing, content, videos, tests, materials and live classes, stored in Firestore
- **Paid courses** — Razorpay checkout, discounted pricing, coupon codes, first-purchase offers and premium access
- **Videos** — course-organized video lectures played with AndroidX Media3 / ExoPlayer
- **Study materials** — in-app PDF viewer for notes and course material
- **Tests & quizzes** — attempt tests, submit answers, view results and track performance
- **Assignments** — view, submit and track assignment status, stored in Firebase
- **Leaderboard** — rankings based on academic and test performance
- **Community / discussion** — course-related Q&A and discussion stored in Firestore
- **Announcements & notifications** — live class alerts, new content, results, offers, payment updates and reminders

## Live Classes & Recording

Live sessions run on **Agora RTC** (`io.agora.rtc:full-sdk:4.5.2`) with camera, microphone, camera switching and screen sharing (Android `MediaProjection` API + foreground services).

Sessions can also be **recorded locally on the student/teacher's phone** — no need to be online to capture the class. Recordings are organized by course:

```text
Recordings/
    CourseId/
        recording1.mp4
        recording2.mp4
        recording3.mp4
```

From the recording management screen, you can start/stop a recording, list and sort recordings by date, play them back, delete them, upload them to Firebase Storage — and **merge multiple local recording segments from one session into a single video file**, so a class that was recorded in parts ends up as one clean file instead of several clips.

## Admin Panel

Administrators manage the platform end to end:

- Students, courses, videos, tests and assignments
- Live classes, discussions and announcements
- Coupons, payments and subscriptions
- Analytics and notifications
- Application settings

The admin dashboard gives a centralized overview of students, courses, payments, subscriptions, tests, assignments, live sessions and overall platform activity.

## Payments & Security

Course payments run through **Razorpay**, with the secret key kept server-side — never inside the Android app.

```text
Student → Select Course → Firebase Auth Session → Cloud Function (createRazorpayOrder)
   → Firestore validation + Razorpay order → Razorpay Checkout → Payment
   → Cloud Function (verifyRazorpayPayment) → Signature check → Course Access
   → Firestore user record updated
```

Coupons (percentage/fixed discount, expiry, usage cap, minimum order value, course-specific or first-purchase-only) and course price are revalidated server-side before an order is created, so pricing can't be tampered with client-side.

## Automatic Backend Tasks

Firebase Cloud Functions handle the logic that shouldn't live in the app: Razorpay order creation and payment verification, subscription expiry, coupon expiry and other secure server-side operations.

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Kotlin |
| UI | Jetpack Compose, Material 3, Navigation Compose |
| Image loading | Coil |
| Video | AndroidX Media3 / ExoPlayer |
| Background work | AndroidX WorkManager |
| Live communication | Agora RTC SDK |
| Screen sharing | Android MediaProjection API, Foreground Services |
| Payments | Razorpay Checkout |
| Auth | Firebase Authentication (Phone/OTP) |
| Database | Cloud Firestore |
| Storage | Firebase Storage |
| Backend | Firebase Cloud Functions |
| Tooling | Android Studio, Gradle, Git/GitHub |

## Architecture

<img src="app%20pictures/architecture.png" alt="ABM EduX system architecture" width="700">

```text
UI (Jetpack Compose Screens) → ViewModels → State Management
        ↓
Firebase / Backend Services
   ├── Firebase Auth
   ├── Firestore
   ├── Storage
   └── Cloud Functions → Razorpay
```

### Firestore structure

```text
Firestore
├── users               ├── assignments
├── courses             ├── assignmentSubmissions
├── videos              ├── discussion
├── tests               ├── liveClasses
├── payments            ├── orders
├── coupons             ├── subscriptions
└── announcements
```

## Screenshots

<p align="center">
  <img src="app%20pictures/p1.png" width="150">
  <img src="app%20pictures/p2.png" width="150">
  <img src="app%20pictures/p3.png" width="150">
  <img src="app%20pictures/p4.png" width="150">
  <img src="app%20pictures/p5.png" width="150">
</p>
<p align="center">
  <img src="app%20pictures/p6.png" width="150">
  <img src="app%20pictures/p7.png" width="150">
  <img src="app%20pictures/p8.png" width="150">
  <img src="app%20pictures/p9.png" width="150">
  <img src="app%20pictures/p10.png" width="150">
</p>
<p align="center">
  <img src="app%20pictures/p11.png" width="150">
  <img src="app%20pictures/p12.png" width="150">
  <img src="app%20pictures/p13.png" width="150">
  <img src="app%20pictures/p14.png" width="150">
  <img src="app%20pictures/p15.png" width="150">
</p>
<p align="center">
  <img src="app%20pictures/p16.png" width="150">
  <img src="app%20pictures/p17.png" width="150">
  <img src="app%20pictures/p18.png" width="150">
  <img src="app%20pictures/p19.png" width="150">
  <img src="app%20pictures/p20.png" width="150">
</p>

## What Makes ABM EduX Different

ABM EduX isn't just a video-learning app — it combines Learning + Live Classes + Tests + Assignments + Payments + Community + Analytics + Content Management, so students aren't switching between five different apps to get through one course.

## Future Scope

AI-based doubt solving and personalized recommendations, advanced student analytics and automated result analysis, more payment options, multi-teacher and multi-institute support, push notification automation, cloud video processing, a web-based admin dashboard, and an iOS app.

## Project Structure

```text
abm-edux
│
├── README.md
├── index.html
│
└── app pictures
    ├── app icon.png
    ├── architecture.png
    └── p1.png ... p20.png
```

## Download

<p align="center">
  <a href="https://play.google.com/store/apps/details?id=com.abhishek8107.abmedux">
    <img src="https://img.shields.io/badge/Get%20it%20on-Google%20Play-E4B94F?logo=googleplay&logoColor=0B1436&style=for-the-badge" alt="Get it on Google Play">
  </a>
</p>

## Developer

**Lokesh Kumar**
Robotics & Automation Engineering, National Institute of Technology Kurukshetra
