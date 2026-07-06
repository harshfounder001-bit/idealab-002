# AICTE IDEA Lab Management System

A comprehensive, cross-platform Flutter application designed to manage operations for the AICTE IDEA Lab. This platform features a **Mobile App** for students to register, book machines, create projects, and earn achievement points, alongside a powerful **Web Dashboard** for lab administrators to manage users, monitor machine status, and track lab activities in real-time.

## ✨ Key Features

**For Students (Mobile App):**
* **Secure Authentication:** Email/Password login with an Admin-approval gatekeeper.
* **Digital ID Pass:** Auto-generated QR code entry pass based on user profile.
* **Machine Booking:** Live calendar and time-slot booking for lab equipment. Prevent double-booking with real-time Firebase syncing.
* **Project Management:** Register new projects, add team members, and track status (Ongoing/Completed).
* **Gamification & Achievements:** Earn points for registering, booking machines, and completing projects. View unlocked badges.
* **Issue Reporting:** Report broken machines or lab issues directly to the admin.

**For Administrators (Web Dashboard):**
* **User Management:** Approve, reject, or view details of pending student registrations.
* **Machine Maintenance:** Toggle machine status (Available / Under Maintenance) live.
* **Booking & Project Tracking:** View all student bookings and project details.
* **Grievance Triage:** Review student-reported issues and update statuses (Pending, Processing, Completed).
* **Leaderboard:** View top-performing students based on their achievement points.
* **Event Management:** Add, edit, and delete lab events that sync instantly to the student app.

---

## 🛠️ Tech Stack
* **Framework:** Flutter (Dart)
* **Backend:** Firebase (Authentication, Cloud Firestore, Firebase Storage)
* **Platforms:** Android / iOS (Student App) & Web / Chrome (Admin Dashboard)

---

## 🚀 Getting Started

Follow these instructions to get a copy of the project up and running on your local machine.

### Prerequisites
1. Install [Flutter SDK](https://docs.flutter.dev/get-started/install).
2. Install [Node.js](https://nodejs.org/) (required for Firebase CLI).
3. Install the Firebase CLI by running this in your terminal:
   ```bash
   npm install -g firebase-tools

## Terminal Commands
1. Clone the Repository:
   ```bash
   git clone [https://github.com/soham-gumal/IDEA_LAB.git](https://github.com/soham-gumal/IDEA_LAB.git)
   cd IDEA_LAB
   flutter pub get

2. Firebase Setup (Crucial):
   Because this project relies on Firebase, you must connect it to your own Firebase project.
   A. Go to the Firebase Console and create a new project.
   B. Inside your Firebase project, enable the following services:
      - <b>Authentication:</b> Enable Email/Password sign-in.
      - <b>Firestore Database:</b> Create a database (start in Test Mode for development).
      - <b>Storage:</b> Enable Firebase Storage for profile pictures and project images.

   C. Log into Firebase from your terminal:
      ```bash
      firebase login

   D. Install the FlutterFire CLI:
      ```bash
      dart pub global activate flutterfire_cli

   E. Configure your Flutter app to use your Firebase project:
      ```bash
      flutterfire configure

3. Running the App
   To run the Student Mobile App (Android/iOS):
   ```bash
   flutter run

   To run the Admin Web Dashboard:
   ```bash
   flutter run -d chrome


## 📅 Maintenance Schedule

To keep the application secure, fast, and operating within Firebase's free tier limits, follow this standard maintenance routine:

### Every 6 Months (The "Tune-Up")
* **Update Dependencies:** Keep packages secure and bug-free by running `flutter pub outdated` to check for old packages, followed by `flutter pub upgrade`. (Always test the app thoroughly after updating).
* **Clean Firebase Storage:** Navigate to the Firebase Console and delete unused files (e.g., old profile pictures, assets from rejected projects) to prevent crossing the 5GB free tier threshold.
* **Purge Inactive Users:** Remove accounts of graduated or long-inactive students from Firebase Authentication and Firestore to keep queries fast and the database secure.

### Every 1 Year (The "Deep Clean")
* **Upgrade Flutter SDK:** Run `flutter upgrade` in your terminal to update the core engine, followed by `flutter doctor` to ensure your system health is optimal. Resolve any deprecated code warnings.
* **Full Database Backup:** Open the Google Cloud Console (linked to your Firebase project) and use the **Firestore Export** tool to download a complete backup of your database to a secure hard drive.
* **Audit Security & Admins:** Review your Firestore Rules to ensure any newly added collections are locked down with `isAdmin()` or `isAuth()`. Audit the `users` collection and downgrade the `role` of any administrators who have left the organization.
* **Optimize Firestore Indexes:** Check the Firestore > Indexes tab in the Firebase Console. Delete any unused composite indexes to prevent hitting Firebase index limits and to optimize database write speeds.
