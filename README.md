# 📺 downloadcc: Interactive Movies & TV Shows Downloader

[![Python](https://img.shields.io/badge/Python-3.12+-blue.svg?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![BitTorrent-libtorrent](https://img.shields.io/badge/BitTorrent-libtorrent-brightgreen.svg?style=flat-square)](https://libtorrent.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

A lightweight, fully interactive terminal-based media downloader that allows users to search for movies and TV shows, select seasons/episodes interactively using keyboard arrow keys, download media using the native `libtorrent` library, and automatically save files organized and renamed for iPad local playback compatibility.

---

## 📖 Table of Contents
- [Direct Download](#-direct-download)
- [Key Features](#-key-features)
- [How to Install](#-how-to-install)
- [How to Use](#-how-to-use)
- [Technical Stack](#-technical-stack)
- [Packaging & Distribution](#-packaging--distribution)
- [Transferring and Watching on iPad](#-transferring-and-watching-on-ipad)
- [File Structure](#-file-structure)
- [License](#-license)

---

## 🚀 Direct Download

You can download the compiled standalone Windows installer directly here:
👉 **[Download MoviesAndShowsInstaller.exe](https://github.com/IamOumarIbrahim/movies-shows-downloader/raw/master/MoviesAndShowsInstaller.exe)**

*(Note: During installation, the installer will automatically add `downloadcc` to your user's system PATH, making it executable from any shell immediately).*

---

## ⭐ Key Features

- **💻 100% Terminal-Based CLI**: Highly responsive interactive keyboard-driven selection screen (use Up/Down arrow keys and Enter to navigate).
- **📺 TV Show Metadata Integration**: Automatically interfaces with the TVmaze API to load shows, search seasons, and list all episodes dynamically.
- **🔍 Strict Title Matching**: Implements custom regex validation to ensure your query results exactly match the target series.
- **⚡ iPad-Compatible Video Profiles (H.264/AAC)**: Search rankings prioritize H.264 video streams and `.mp4` containers. It deprioritizes HEVC/x265, AV1, and 10-bit color formats to guarantee out-of-the-box playback on iPad Files app.
- **🚀 High-Speed Peer Discovery**: Configures the underlying `libtorrent` session with DHT, Local Service Discovery (LSD), UPnP, and NAT-PMP enabled.
- **📁 Automatic Post-Processing**: Automatically organizes files into target folders (e.g. `{Show Name} - Season XX`) and renames video files to the clean `S_XX_E_YY.ext` convention.
- **💾 Custom Save Destination**: Prompts you to input your desired output save directory after confirming your selection (defaults to your downloads workspace if left blank).

---

## ⚙️ How to Install

### Method A: Setup Installer (Recommended)
1. Download and run **[MoviesAndShowsInstaller.exe](https://github.com/IamOumarIbrahim/movies-shows-downloader/raw/master/MoviesAndShowsInstaller.exe)**.
2. Complete the installer prompts (it will install into your AppData directory and register `downloadcc` globally in your User PATH).
3. Open a **new** PowerShell or Command Prompt session and run the tool:
   ```bash
   downloadcc
   ```

### Method B: Manual Python Environment
1. Clone the repository:
   ```bash
   git clone https://github.com/IamOumarIbrahim/movies-shows-downloader.git
   cd movies-shows-downloader
   ```
2. Install dependencies:
   ```bash
   pip install requests beautifulsoup4 libtorrent pyinstaller
   ```
3. Run the script:
   ```bash
   python downloadcc.py
   ```

---

## 🏃 How to Use

Simply launch `downloadcc` with or without a query:

```bash
downloadcc "Mr. Robot"
```

1. **Interactive Search**: The CLI will search for matching titles and display a selection menu.
2. **Keyboard Controls**:
   - `Up/Down Arrow Keys`: Change selection highlight.
   - `Enter`: Confirm selection.
   - `Esc`: Cancel search.
3. **Select Season**: If you chose a TV Series, select a specific season (or choose **All Seasons (Complete Pack)**).
4. **Choose Save Directory**: Input the absolute path where you want the downloads saved (or press Enter to use default).
5. **Real-time Download**: Displays progress percentage, active transfer speed (MB/s), and active peer count.

---

## 🛠️ Technical Stack

| Dependency | Purpose | Details |
| :--- | :--- | :--- |
| **Python** | Language Core | Version 3.12+ |
| **libtorrent** | Torrent Engine | Python bindings for rasterbar libtorrent |
| **Requests / BeautifulSoup4** | Web Crawlers | Torrent indexing parsing |
| **TVmaze API** | TV Metadata | API client for metadata extraction |

---

## 📦 Packaging & Distribution

To re-compile the CLI script into a single-file executable and package it using Inno Setup:

```bash
# 1. Compile with PyInstaller
pyinstaller --noconfirm --onefile --console --name downloadcc downloadcc.py

# 2. Compile Inno Setup Script
& "C:\Users\omarb\AppData\Local\Programs\Inno Setup 6\ISCC.exe" installer.iss
```

---

## 📱 Transferring and Watching on iPad

1. **Transfer to iPad**:
   - Put the downloaded folders into your iCloud Drive/Google Drive on your PC. They will sync and appear in your iPad's **Files** app.
   - Or connect your iPad via USB and copy them directly inside the **VLC** files directory.
2. **Watch**:
   - Open **VLC on iPad** (free on App Store). VLC natively supports all audio codecs (including AC3/DTS) and plays these files seamlessly!

---

## 📁 File Structure

```
movies-shows-downloader/
├── .gitignore                   - Git ignore patterns
├── README.md                    - Project documentation (this file)
├── MoviesAndShowsInstaller.exe  - Compiled standalone Windows installer
├── downloadcc.py                - Main interactive CLI program entry point
├── installer.iss                - Inno Setup compiler configuration
└── search_engine.py             - TVmaze and Pirate Bay crawling engine
```

---

## 📄 License
This repository is licensed under the [MIT License](LICENSE).
