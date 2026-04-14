# FocusTimerApp 

FocusTimerApp is a feature-rich, productivity-enhancing WPF desktop application designed to implement the Pomodoro technique. It goes beyond a simple timer by integrating real-time system monitoring to enforce "Focus Zones" and track user productivity automatically.

![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat&logo=dotnet)
![WPF](https://img.shields.io/badge/WPF-MVVM-00599C?style=flat&logo=windows)

## Key Features

* **Dual Timer Modes**: Supports both classic Pomodoro (Work/Break intervals) and Basic tracking (Count-up) modes.
* **Smart "Focus Zone" Monitoring**: 
    * Utilizes **Win32 APIs** (`GetForegroundWindow`, `GetWindowThreadProcessId`) to track the active foreground application in real-time.
    * Automatically pauses the timer and triggers system tray notifications if the user navigates away from designated "Work Zone" applications.
* **Global Hotkey Management**: Register custom global hotkeys to control the timer (Start/Pause/Stop) and toggle the UI overlay, even when the app is running in the system tray.
* **Unobtrusive Overlay Mode**: Features a minimalist, Always-on-Top overlay to keep track of time without cluttering the screen.
* **Compact Configuration Export/Import**: 
    * Share personalized settings and hotkeys via a compact code string.
    * Implemented using **JSON Serialization**, **Brotli Compression**, and **Base64 URL Encoding** to minimize the payload size.
* **Integrated Focus Music Player**: 
    * Built-in local MP3 library parser using `TagLib` to read metadata.
    * Background media playback capabilities to help maintain focus.
* **Modern UI & System Tray**: Dynamic Dark/Light theme switching and seamless background execution via the Windows System Tray (`NotifyIcon`).

## Tech Stack & Architecture

* **Framework**: C# WPF on .NET 8.0
* **Architecture**: Strict **MVVM (Model-View-ViewModel)** pattern
* **Service Management**: Microsoft Dependency Injection (`IServiceProvider`)
* **System Integration**: Win32 API Interop (user32.dll)
* **Libraries**: `TagLibSharp` (Metadata parsing), `Newtonsoft.Json`

## Project Structure

The project strictly separates concerns for maintainability and scalability:
* `Models/`: Data structures for application state, configurations, and hotkey bindings.
* `ViewModels/`: UI logic, Command bindings (`RelayCommand`), and state management implementing `INotifyPropertyChanged`.
* `Services/`: Core business logic injected via DI (e.g., `TimerService`, `AppFocusService`, `HotkeyService`, `SettingsService`).
* `Views/`: XAML files defining the UI, utilizing Data Binding and Resource Dictionaries for themes.
* `Helpers/`: Utility classes for Win32 API interoperability and hotkey parsing.

## Getting Started

### Prerequisites
* Windows 10 / 11
* [.NET 8.0 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0)
* Visual Studio 2022 (for development)

### Installation
1.  Clone the repository:
    ```bash
    git clone [https://github.com/minhquansicula/FocusTimerApp.git](https://github.com/minhquansicula/FocusTimerApp.git)
    ```
2.  Open the solution (`.sln`) in Visual Studio 2022.
3.  Restore NuGet packages.
4.  Set `GroupThree.FocusTimerApp` as the startup project.
5.  Build and Run (`F5`).

## Configuration Code Feature

To share your exact timer durations and hotkey bindings with a friend:
1.  Navigate to **Settings** -> **Configuration Code**.
2.  Click **Generate** to create a compressed export code.
3.  Copy and share the code. The recipient can paste it into the **Import** field and apply the settings instantly.

## Author

**Do Minh Quan**
* Software Engineering Student at FPT University Ho Chi Minh
* GitHub: [@minhquansicula](https://github.com/minhquansicula)
* LinkedIn: [do-minh-quan](https://www.linkedin.com/in/siminhcoquan)
* Email: wuanminh777@gmail.com

---
*This project was built to explore advanced WPF concepts, MVVM architecture, and Win32 system integration.*
