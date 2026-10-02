# DefaultAudioChanger (Modernized Windows 11 Fork)

A lightweight, high-performance Windows tray utility written in native C++ / Win32 API that allows toggling the default audio endpoint with a **single left-click** on the system tray icon.

This is a modernized fork of the original 2015 project, fully rewritten and optimized for Windows 11 and Visual Studio 2022.

## 🚀 Key Improvements in this Fork

*   **Single Left-Click Toggle:** Replaced the legacy requirement of opening the context menu. A single click on the tray icon instantly cycles between selected audio devices.
*   **Asynchronous WinAPI Pipeline:** Implemented via a robust `::PostMessage` message-queuing architecture. This bypasses the old WTL runtime crashes caused by graphic elements (`listView`) being destroyed in RAM while the dialog is hidden.
*   **Dynamic Custom Icons:** Fully supports Windows 11 endpoint icon extraction. The tray icon dynamically morphs into the exact device icon (e.g., custom headphone/speaker icons) defined in your Windows Sound Control Panel.
*   **Smart Minimize Затвор:** Modified the upper-right standard Close button (`X`) behavior to safely hide the dialog to the tray instead of terminating the background process. The process can now be cleanly closed via the context menu.
*   **Modern Build Toolchain:** Updated the complete configuration to toolset **v143** and hardcoded native search paths for Spectre-mitigated static libraries (`atls.lib`), eliminating the need for manual library copying.

## 🛠️ Requirements & Build Instructions

### Prerequisites
*   Windows 11 (tested on latest 26H2 builds)
*   Visual Studio 2022 / Build Tools 2022 (MSVC v143)
*   WTL 9.1 (Windows Template Library)

### Compilation via Command Line
1. Open the **Developer Command Prompt for VS 2022** as Administrator.
2. Navigate to the root directory:
   ```cmd
   cd C:\Scripts\DefaultAudioChanger_custom
   ```
3. Execute the MSBuild compilation engine to melt the release binary:
   ```cmd
   msbuild DefaultAudioChanger.sln /p:Configuration=Release /p:Platform=Win32 /p:WindowsTargetPlatformVersion=10.0
   ```
4. The production binary will materialize at `DefaultAudioChanger\Release\DefaultAudioChanger.exe`.

## 📄 License
This project is released under the open-source **MIT License**, preserving the original author's requirements while opening the codebase for community improvements.
