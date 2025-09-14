
# Uni-Option 🎓📱

*A Centralized University Information & Application Portal for Pakistani Universities*

Uni-Option is a **Flutter mobile application** designed to simplify access to university details, degree programs, and application processes in Pakistan. The app uses **Provider state management**, a **Supabase backend**, and follows **Material 3 design** principles with a culturally relevant Pakistani-inspired theme.

---

## 🚀 Features

* 📊 **University Information**: Browse universities with detailed programs and application steps.
* ⭐ **Favorites**: Mark universities as favorites (saved with persistence).
* 🔔 **Smart Notifications**: Reminders and alerts when favoriting/unfavoriting universities.
* 🎨 **Pakistani-Themed Design**: Green-based Material 3 theme inspired by the national flag.
* 🌓 **Light/Dark Mode**: Theme switching with persistent preferences.
* 🔐 **Admin Panel**: Secure admin login with separate interface.
* 💾 **Offline Support**: Fallback static data when backend is unavailable.

---

## 🏛 Architecture Overview

### **State Management (Provider)**

* `UniversityProvider`:

  * Fetches university data from Supabase
  * Handles favorites with **SharedPreferences**
  * Search & filtering logic
  * Triggers local notifications

* `ThemeProvider`:

  * Manages light/dark mode
  * Persists theme preference

### **Data Layer**

* **Models** (`lib/models/`): JSON-serializable classes with null safety and fallback values.
* **Backend**: Supabase with PostgreSQL queries (nested joins for degrees & application steps).
* **Data**: Fallback in `lib/data/universities_data.dart`.

### **UI Layer**

* **Navigation**: Named routes with argument passing.
* **Screens**: Organized under `lib/screens/` (includes admin panel).
* **Widgets**: Reusable Material 3 components in `lib/widgets/`.
* **Theme**: Defined in `lib/utils/theme.dart` with custom color palette:

  * Primary: `#01411C` (Dark Green)
  * Secondary: `#00A86B` (Medium Green)
  * Accent: `#F8C100` (Gold)

---

## 📂 Project Structure

```
lib/
├── main.dart              # App entry, providers, routes
├── models/                # Data models with JSON serialization
├── providers/             # State management (Provider)
├── screens/               # Feature-based screen organization
│   └── admin/             # Admin panel screens
├── widgets/               # Reusable UI components
├── services/              # External service integrations
├── utils/                 # Theme & constants
└── data/                  # Fallback university data
```

---

## 🔧 Development Conventions

* ✅ **Null Safety** in all model parsing
* 🔄 **notifyListeners()** after every state update
* ⚠️ **Error Handling** with user-friendly messages
* 🖼 **Asset Management**: University logos in `assets/images/` (registered in `pubspec.yaml`)
* 🎬 **Animations**: Shared element transitions with `animations` package
* 🧪 **Testing**: Widget tests in `test/` directory

---

## 📡 Supabase Integration

* **Queries**:

  ```dart
  final response = await supabase
      .from('universities')
      .select('*, degrees(*), application_steps(*)');
  ```
* **Environment Variables**: Store Supabase keys securely (not in code).
* **Fallback**: Uses static data if backend is unreachable.

---

## 🔔 Notifications

* Implemented via `flutter_local_notifications`.
* Triggered on **favorites/unfavorites** and **application deadlines**.
* Initialized in `main.dart` before app launch.

---

## 🛠 Common Tasks

### ➕ Adding New Universities

1. Add entry in `universities_data.dart`.
2. Add logo in `assets/images/` and update `pubspec.yaml`.

### 📱 Adding New Screens

1. Create screen under `lib/screens/`.
2. Register in `main.dart` routes.
3. Update `MainDrawer` if needed.

### 🗄 Updating Backend Schema

1. Update models with new fields (with defensive parsing).
2. Update Supabase queries.
3. Test with both filled and null fields.

---

## ✅ Quality Standards

* **Linting**: Uses `flutter_lints`.
* **Analysis**: Configured with `analysis_options.yaml`.
* **Testing**: Basic widget/unit tests included.


---

## 🧑‍💻 Tech Stack

* **Frontend**: Flutter (Dart), Material 3, Provider
* **Backend**: Supabase (PostgreSQL)
* **Persistence**: SharedPreferences
* **Notifications**: flutter\_local\_notifications

---

## 🌍 Context

This app is tailored for **Pakistani university applicants**, with culturally relevant design and features to make application tracking simpler and more engaging.

---



