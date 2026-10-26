# ttalk Releases & The v1.0.0 Success Story

Official public binary releases, architecture overview, and 1-click bootstrap for **[ttalk](https://github.com/teshah/ttalk)** — an air-gapped, open-weights, open-source voice dictation engine running 100% locally on standard Windows hardware with zero cloud dependencies.

---

## ⚡ 1-Click Fast Install (Any Windows 10/11 Laptop)

Open **PowerShell** and run this single command:

```powershell
irm https://gist.githubusercontent.com/teshah/919ad5d28858adf2b74a6d889e3f43b3/raw/install.ps1 | iex
```

### What This Does Automatically in ~15 Seconds:
1. Downloads the 100% offline standalone production release (`ttalk-portable-v1.0.0.zip`).
2. Extracts it cleanly into `%LOCALAPPDATA%\ttalk`.
3. Creates a **ttalk** shortcut directly on your Desktop.
4. Launches the engine immediately — **zero developer tools, zero Git, and zero external packages required**.

---

## 🗑️ 1-Click Uninstall

To cleanly remove `ttalk` and its desktop shortcut at any time:

```powershell
irm https://gist.githubusercontent.com/teshah/7ad69aebf046b0267f20214200dbd5f5/raw/uninstall.ps1 | iex
```

---

## 🚀 The `ttalk v1.0.0` Success Story

### The Challenge
Modern commercial voice dictation tools (such as Wispr Flow) deliver impressive user experiences, but operate as **cloud-tethered SaaS products**:
* Every word you speak travels across the public internet to third-party servers.
* Requires monthly subscriptions and internet connectivity.
* Unacceptable for confidential engineering environments, proprietary codebases, financial documents, or air-gapped networks.

### The Objective
Engineer an **open-weights, open-source, air-gapped equivalent** capable of running on standard commodity developer laptops (tested on an Intel Core i7-8850H 6-core CPU with zero external GPU acceleration required).

### Methodology: Software Factory Discipline
`ttalk` was built from inception under a strict **Software Factory Framework**:
1. **Gated Progression**: Zero production code written before formal architectural sign-off (`RFC-001 v1.0.0`).
2. **Architecture Decision Records (ADRs)**: 6 formal decision records codified in version control governing tech stack, TDD boundaries, and scope freeze.
3. **Rigorous TDD Invariant**: All subsystem slices authored via isolated git worktrees with prior failing Red integration tests before Green implementation.
4. **Anti-Slop AST Auditing**: Automated AST scanners enforcing 0.00 conversational commentary and strict Clippy `-D warnings` standards.

---

## 📊 Empirical Value Proofs & Benchmark Results

`ttalk v1.0.0` was validated through the **5 Ultimate Value Proofs**:

| Value Proof | Empirical Result | Target Metric | Status |
| :--- | :---: | :---: | :---: |
| **Proof 1: Cognitive Flow Latency** | **1.22s** average turnaround | $\le 1.25\text{s}$ on CPU | 🟢 **CERTIFIED** |
| **Proof 2: Voice Recognition Accuracy** | **96.0%** across all test categories | $\ge 85.0\%$ threshold | 🟢 **CERTIFIED** |
| **Proof 3: Air-Gap Network Hygiene** | **0 bytes** outbound traffic | 100% offline | 🟢 **CERTIFIED** |
| **Proof 4: Non-Destructive OS Injection** | **100% byte-for-byte** clipboard restore | Zero data loss | 🟢 **CERTIFIED** |
| **Proof 5: Clean-Machine Replication** | **15 seconds** via 1-line script | $< 5\text{ minutes}$ | 🟢 **CERTIFIED** |

### Live Spoken Voice Benchmark Results (5 Golden Tests)

```text
======================================================================
                  FINAL TEST SCORECARD
======================================================================
  [PASS]  TEST-01 (Basic Conversational):        100.0%  (1.24s)
  [PASS]  TEST-02 (Technical & Engineering):     100.0%  (1.29s)
  [PASS]  TEST-03 (Punctuation & Numbers):        90.9%  (1.23s)
  [PASS]  TEST-04 (Speech Fillers & Fast Paced):  88.9%  (1.16s)
  [PASS]  TEST-05 (Dictation & Formatting):      100.0%  (1.19s)
----------------------------------------------------------------------
  TOTAL PASSED:   5 / 5 (100% Pass Rate)
  AVG ACCURACY:   96.0% Word Accuracy
  AVG LATENCY:    1.22s (Sub-1.25s Turnaround on i7 CPU)
======================================================================
```

---

## 🛠️ Architecture at a Glance

* **Stand-Alone Core**: Native Rust engine with custom circular ring buffering, exact 3:1 decimation ($48\text{kHz} \rightarrow 16\text{kHz}$), and energy-based VAD boundary management.
* **Offline Speech-to-Text**: Whisper model running natively via AVX2 CPU acceleration with 6 physical execution threads.
* **Safe OS Citizen**: Direct `user32.dll` / `kernel32.dll` ctypes integration that backs up your clipboard, simulates `Ctrl+V` paste into any active window, and immediately restores your original clipboard without leaking secrets.
* **Clean Portability**: Zero external dependencies. Works on fresh, out-of-the-box Windows 10/11 x64 laptops.

---

## 📦 Manual Direct Download

Download the portable archive directly:
* **[ttalk-portable-v1.0.0.zip](https://github.com/teshah/ttalk-releases/releases/download/v1.0.0/ttalk-portable-v1.0.0.zip)** (136 MB)
