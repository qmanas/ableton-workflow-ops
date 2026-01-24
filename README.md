# 🎹 Ableton Workflow Ops: Automated Batch Exporter

A hybrid automation engine that streamlines the final stages of music production in Ableton Live. Using a combination of **Python**, **AppleScript**, and **Max for Live (JS)**, it automates the tedious GUI-driven process of exporting tracks, managing metadata, and handling file naming conventions.

---

## 🔥 The Problem Solved
Music producers often spend 30-60 minutes at the end of every session manually exporting stems, naming them correctly, and organizing folders. In professional studio environments, this is a major bottleneck that is highly prone to human error (e.g., misnaming a mix version).

---

## 🛡️ The "High-Integrity" Win: GUI Interop & Failover
Because Ableton Live does not expose a native "Headless Export" API for tracks, this project uses a **layered automation strategy**:
1.  **Orchestrator (Python)**: Manages the automation state, versioning (`version_finder.py`), and file path logic.
2.  **Executive Layer (AppleScript)**: Directly interacts with the Ableton GUI to navigate menus, input filenames, and trigger the export modal. It includes specialized retry logic (`diagnostic_ui.applescript`) to handle slow UI response times and pop-ups.
3.  **Signal Layer (Max for Live JS)**: Communicates with the Ableton internal API to verify the current session state before triggering the GUI layer.

---

## 💸 Technical Debt Liquidated
- **Reduced Human Error**: Stems are automatically tagged and organized by session date and version code.
- **Background Orchestration**: The Python launcher handles pre-flight checks (disk space, folder structure) before the intensive GUI automation begins, preventing 99% of "Silent Failures."

---

## 🛠️ Tech Stack
-   **Python 3**: Main orchestrator and metadata manager.
-   **AppleScript**: macOS GUI automation.
-   **JavaScript (Max for Live)**: Internal Ableton environment logic.
-   **JSON**: Cross-process communication.

---

## 🚀 Quick Start
*Note: This tool is designed for macOS due to AppleScript dependencies.*

1.  Clone the repository:
    ```bash
    git clone https://github.com/yourusername/ableton-workflow-ops.git
    ```
2.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3.  Launch the automation:
    ```bash
    python launcher.py
    ```

---

## 🤝 Contributing
Contributions are welcome! If you have optimized AppleScripts for different Ableton versions or Windows-compatible GUI scripts (PowerShell/AutoHotkey), please submit a Pull Request.

---

**Built by an engineer who loves sound. 🔉**
