# Setup

## Prerequisites

### To launch
1. [Developer Mode enabled](#enabling-developer-mode)
2. Windows 10 (or later)
4. Visual Studio 2026 OR WinDbg (for debugging if needed)
5. Make sure you select the "Desktop development with C++" workload.
6. Visual C++ Redistributables (unsure which are needed)
7. Graphics Tools (from `Settings > Apps > Optional Features` (Windows 10) or `Settings > System > Optional Features` (Windows 11))
8. The latest [release](https://github.com/WinDurango/WinDurango/releases)/[artifact](https://github.com/WinDurango/WinDurango/actions/workflows/build-WD.yml)

### To build

1. Everything from [the launch requirements](#to-launch) (except for the release/artifact)
2. Windows 10 (or later)
3. Windows App SDK 
4. Visual Studio 2026 and/or Visual Studio Code
5. Git
6. CMake
7. Windows 11 SDK version 10.0.28000.0 or later
8. The following from the Visual Studio Installer
   - Desktop Development with C++
   - Windows Application Development
   - MSVC (143) C++ Build Tools
   - C++ (143) Universal Windows Platform Tools
   - .NET Desktop Development
   - Game Development with C++
9. The project cloned to a folder

## Running the package

To run the package, you need to setup the [Launch prerequisites](#to-launch) and have already [registered the package](#registering-the-uwp-package).   
You'll need to also copy in all the DLLs from the latest [release](https://github.com/WinDurango/WinDurango/releases)/[artifact](https://github.com/WinDurango/WinDurango/actions/workflows/msbuild.yml) into your app's Mount folder (the folder that has the EXE) and copy the EmbeddedXVD folder into the Mount folder. 

Make sure you copy these dll's from EmbeddedXVD/Windows/System32 into the Mount dir:
 - `xg_x.dll`, `xg.dll` (if present)
 - `AcpHal.dll`
 - `xaudio2_9.dll`,
 - `D3DCompiler46.dll` (if present)
 - `sc_dll.dll` (if present)

After that, you just need to open the app through the start menu. (or other preferred way of running UWP apps)

## Registering the UWP package

You cannot normally run a UWP app's EXE file directly, instead you have to register the UWP app and launch it from the Start Menu/a Debugger.

1. [Enable Developer Mode](#enabling-developer-mode)
2. Go to the Mount folder of your game (where the EXE sits)
3. Open Powershell.exe to that directory
4. Run `Add-AppXPackage -Register .\AppxManifest.xml`

## Enabling Developer Mode

To register UWP apps, you have to enable Developer Mode.

1. Go to For Developers in Settings (path differs depending on Windows version, read below)
   - Settings > Windows Update > For Developers (Windows 10)
   - Settings > System > For Developers (Windows 11)
2. Enable Developer Mode

# Building

1. Clone the repo  
   - `git clone --recursive https://github.com/WinDurango/WinDurango.git`
3. Open up the `VS 2026 Powershell Prompt`
3. Clone the repo
   ```sh
   git clone https://github.com/WinDurango/WinDurango
   ```
4. Install VCPKG packages
   ```sh
   vcpkg install
   ```
5. Prep CMake
   ```sh
    mkdir build && cd build
    cmake ..
   ```
6. Build WinDurango
   ```sh
   cmake --build .
   ```
   
# Contributing
To contribute, just create a fork, make your changes and create a pull request. AI Code is not allowed.
