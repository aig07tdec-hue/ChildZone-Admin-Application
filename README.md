# 🔐 ChildZoneAdmin – Administrative Management App

<p align="center">
  <strong>Centralized Administration for the ChildZone Educational Ecosystem</strong>
</p>

ChildZoneAdmin is a native Android administrative application designed to manage and monitor the ChildZone ecosystem. It provides administrators with tools to manage children's profiles, monitor learning performance, control educational games, and handle user-submitted reports.

Built using **Java, Android Studio, Firebase Authentication, and Cloud Firestore**, the application provides real-time data synchronization and centralized administrative control.

---

## 📌 Project Overview

ChildZoneAdmin acts as the administrative control center of the ChildZone ecosystem.

The application allows administrators to:

- Monitor registered children's information.
- View learning performance and engagement statistics.
- Manage children's profiles.
- Enable or disable educational games.
- Track and resolve user-submitted reports.
- Search and filter records.
- Synchronize data using Firebase Firestore.

## 🎯 Objectives

- Provide centralized administration.
- Monitor children's learning progress.
- Manage child profiles and information.
- Control educational game availability.
- Handle user reports and support requests.
- Display real-time dashboard statistics.
- Maintain synchronized cloud data.

---

## ✨ Features

### 📊 1. Admin Dashboard

Provides an overview of the ChildZone ecosystem using real-time Firestore data.

**Dashboard Statistics:**
- Total Registered Children
- Total Cumulative Score
- Average Learning Progress
- Total Playtime (Hours)
- Total Rewards Earned
- Weekly Engagement Progress

**Additional Features:**
- Real-time Firestore updates.
- Navigation Drawer.
- Bottom Navigation Bar.
- Centralized module navigation.

### 👦 2. Child Management

Manage and monitor registered children's profiles.

**Features:**
- Real-time child directory.
- Automatic test-child seeding when the collection is empty.
- Search by child name, ID, parent name, or parent email.
- Alphabetical sorting (A–Z).
- Detailed child information.

**Child Details Include:**
- Child ID and name.
- Age.
- Parent name and contact information.
- Firebase UID.
- Account creation date.
- Eye-comfort mode status.
- Total score.
- Learning progress.
- Total playtime.
- Rewards earned.

**Default Test Child:**

| Field | Value |
|---|---|
| Child ID | CZ10001 |
| Child Name | Vedant |

### 🎮 3. Game Management

Administrators can control the availability of educational games across the ChildZone platform.

**Default Games:**

| No. | Game Name | Category |
|---|---|---|
| 1 | Math Quiz | Educational |
| 2 | Word Builder | Educational |
| 3 | Memory Match | Memory |
| 4 | Alphabet Learning | Educational |
| 5 | Picture Match | Puzzle |

**Features:**
- Automatic default game configuration.
- Enable and disable games.
- Update game status in Firestore.
- Visual game availability indicators.
- Snackbar confirmation messages.

**Game Management Flow:**

```text
Admin App
    |
    v
Game Management
    |
    v
Enable / Disable Game
    |
    v
Cloud Firestore
    |
    v
ChildZone App
    |
    v
Updated Game Availability
```

### 📩 4. Reports & Support Management

Manage user-submitted issues, bug reports, and support requests.

**Features:**
- Real-time report retrieval.
- Latest reports displayed first.
- Search reports.
- Filter reports by status.
- View complete report details.
- Add or update administrator replies.
- Update report resolution status.
- Record server timestamps when resolved.

**Report Status:**

| Status | Description |
|---|---|
| Pending | Waiting for administrator action |
| In Progress | Currently being handled |
| Resolved | Issue has been resolved |

**Search Options:**
- Subject
- Category
- Submitter Name
- Child ID
- Description

---

## 🏗️ Application Architecture

ChildZoneAdmin follows a **Single-Activity Multi-Fragment Architecture**.

```text
              ChildZoneAdmin
                    |
                    v
          AdminDashboardActivity
                    |
          +---------+---------+
          |                   |
    Navigation Drawer   Bottom Navigation
          |                   |
          +---------+---------+
                    |
          +---------+----------+
          |         |          |
          v         v          v
      Dashboard  Children    Games
      Fragment   Fragment   Fragment
                    |
                    v
              Reports Fragment
                    |
                    v
              Firebase Services
                    |
             Cloud Firestore
                    |
       +------------+------------+
       |            |            |
       v            v            v
    children    gameConfig    reports
```

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Java 11 | Programming Language |
| XML | UI Layout Design |
| Android Studio | Development Environment |
| Android Views | Native UI |
| View Binding | View Access |
| Material Components | UI Components |
| ConstraintLayout | Responsive Layouts |
| RecyclerView | Dynamic Lists |
| CoordinatorLayout | UI Coordination |
| Firebase Authentication | Authentication |
| Cloud Firestore | Cloud Database |
| Gradle 9.5.0 | Build System |
| Android Gradle Plugin 8.5.0 | Android Build Plugin |
| Android SDK 34 | Target SDK |
| Minimum SDK 24 | Minimum Android Version |

---

## ☁️ Firebase Integration

ChildZoneAdmin uses Firebase for authentication, database storage, and real-time synchronization.

### Firebase Authentication
- Administrator authentication.
- Authenticated user identification.
- Access to authorized administrative operations.

### Cloud Firestore

The application uses three main collections:

#### 1. `children`

Stores child profiles and learning statistics.

```text
children/
    └── childDocument
         ├── childId
         ├── childName
         ├── age
         ├── parentName
         ├── parentEmail
         ├── parentMobile
         ├── firebaseUid
         ├── score
         ├── progress
         ├── playTime
         ├── rewards
         ├── eyeComfortEnabled
         └── createdAt
```

#### 2. `gameConfig`

Stores game configuration and availability.

```text
gameConfig/
    └── gameDocument
         ├── gameId
         ├── gameName
         ├── category
         ├── description
         ├── difficulty
         └── enabled
```

#### 3. `reports`

Stores user-submitted issues and support requests.

```text
reports/
    └── reportDocument
         ├── reportId
         ├── userId
         ├── userType
         ├── childId
         ├── userName
         ├── category
         ├── subject
         ├── description
         ├── status
         ├── adminReply
         ├── createdAt
         └── resolvedAt
```

### Real-Time Synchronization

Firestore snapshot listeners are used to retrieve updated information automatically.

**Synchronization Flow:**

```text
       ChildZone App
             |
             v
        Cloud Firestore
             |
             v
       ChildZoneAdmin
             |
             v
      Updated Admin Data
```

---

## 📁 Project Structure

```text
ChildZoneAdmin/
│
├── app/
│   └── src/
│       └── main/
│           ├── java/
│           │   └── com/
│           │       └── childzone/
│           │           └── admin/
│           │               ├── activities/
│           │               │   ├── AdminDashboardActivity.java
│           │               │   ├── ChildDetailsActivity.java
│           │               │   └── ReportDetailsActivity.java
│           │               │
│           │               ├── adapters/
│           │               │   ├── AdminReportsAdapter.java
│           │               │   ├── ChildAdapter.java
│           │               │   └── GameAdapter.java
│           │               │
│           │               ├── fragments/
│           │               │   ├── ChildManagementFragment.java
│           │               │   ├── DashboardFragment.java
│           │               │   ├── GameManagementFragment.java
│           │               │   └── ReportsFragment.java
│           │               │
│           │               └── models/
│           │                   ├── Child.java
│           │                   ├── Game.java
│           │                   └── Report.java
│           │
│           ├── res/
│           │   ├── drawable/
│           │   ├── layout/
│           │   ├── menu/
│           │   ├── navigation/
│           │   └── values/
│           │
│           └── AndroidManifest.xml
│
├── build.gradle
├── settings.gradle
├── gradle/
└── README.md
```

---

## 🚀 Installation & Setup

### Prerequisites

- Android Studio
- Java Development Kit (JDK) 11
- Android SDK 34
- Gradle-compatible development environment
- Firebase account

### Step 1: Clone Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### Step 2: Open Project

1. Open Android Studio.
2. Select **Open Project**.
3. Select the downloaded ChildZoneAdmin folder.
4. Wait for Gradle synchronization.

### Step 3: Configure Firebase

1. Create or select a Firebase project.
2. Register your Android application.
3. Download `google-services.json`.
4. Place the file inside the `app/` directory.
5. Enable Firebase Authentication.
6. Enable Cloud Firestore.
7. Configure the required database collections.

### Step 4: Build & Run

1. Sync Gradle.
2. Connect an Android device or start an emulator.
3. Click **Run ▶** in Android Studio.

---

## 🔒 Security

- Use Firebase Authentication for administrator sign-in.
- Configure Firestore Security Rules.
- Restrict game configuration updates to authorized administrators.
- Protect child information and user reports.
- Never upload private credentials or service-account keys to GitHub.
- Do not commit sensitive configuration files.

---

## 🧪 Testing

Important testing areas include:

- Admin authentication.
- Dashboard statistics.
- Real-time child data retrieval.
- Child search and sorting.
- Default game initialization.
- Enable/disable game functionality.
- Firestore synchronization.
- Report filtering and searching.
- Report status updates.
- Administrator reply functionality.
- Database security and error handling.

---

## 🔮 Future Enhancements

- Advanced learning analytics.
- Graphical performance reports.
- Export child progress reports.
- Push notifications for new reports.
- Advanced admin role management.
- Detailed game usage statistics.
- Report history and tracking.
- Improved dashboard visualizations.

---

## 📚 Project Information

| Information | Details |
|---|---|
| Project Name | ChildZoneAdmin |
| Project Type | Android Administrative Application |
| Platform | Android |
| Language | Java 11 |
| UI Design | XML |
| Architecture | Single-Activity Multi-Fragment |
| Backend | Firebase |
| Authentication | Firebase Authentication |
| Database | Cloud Firestore |
| Build System | Gradle |
| Target SDK | 34 |
| Minimum SDK | 24 |
| IDE | Android Studio |

---

## 📄 License

This project was developed for educational and academic purposes.

---

<p align="center">
  <strong>ChildZoneAdmin</strong><br>
  Manage • Monitor • Support • Improve 🚀
</p>
