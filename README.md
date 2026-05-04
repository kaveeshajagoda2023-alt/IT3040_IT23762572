# IT3040 – Assignment 1 (Option 1): Transliteration Accuracy Testing

## Overview

This repository contains the Playwright automation project for testing the **Chat Sinhala transliteration** function of [https://www.pixelssuite.com/chat-translator](https://www.pixelssuite.com/chat-translator).

- **50 negative test cases** covering all 24 Singlish input types specified in Appendix 1.
- A Python + Playwright script that auto-runs every test case, captures the actual output, and writes results back to the Excel file.

---

## Repository Structure

```
test_automation/
├── test_automation.py          # Main Playwright automation script
├── Assignment_1_Test_cases.xlsx  # Test case spreadsheet (fill before running)
├── Commands.txt                # Quick-reference command cheat-sheet
└── README.md                   # This file
```

---

## Prerequisites

| Requirement | Version | Notes |
|---|---|---|
| Python | 3.11 or 3.12 | [python.org](https://python.org) |
| Google Chrome | Latest | Recommended; Playwright can also install Chromium |
| pip | Latest | Upgraded in setup step |

---

## Setup Instructions

### Step 1 – Clone / Download the Repository

Download the ZIP and extract it to your `D:\` drive:

```
D:\test_automation\
```

Or clone via Git:

```bash
git clone https://github.com/<your-username>/it3040-assignment1.git
cd it3040-assignment1
```

---

### Step 2 – Open Command Prompt and Navigate to the Folder

```cmd
cd /d D:\test_automation
```

---

### Step 3 – Install Dependencies (one-time)

Run the following commands **in order**:

```cmd
pip install -U pip
pip install playwright openpyxl
playwright install
```

> **Note:** If you already have Google Chrome installed, Playwright will use it automatically via `channel="chrome"`.

---

### Step 4 – Prepare the Excel File

Open `Assignment_1_Test_cases.xlsx` (already included with 50 test cases pre-filled).

The columns are:

| Column | Description | Filled by |
|---|---|---|
| A – TC ID | Test case ID (Neg_0001 … Neg_0050) | You (pre-filled) |
| B – Input length type | S / M / L | You (pre-filled) |
| C – Input | Singlish input text | You (pre-filled) |
| D – Expected output | Correct Sinhala translation | You (pre-filled) |
| E – Actual output | Auto-filled by script | Script |
| F – Status | Pass / Fail | Script |
| G – Singlish input types covered | Input type categories | You (pre-filled) |
| H – Evidence or rationale | Justification | You (pre-filled) |

> **Do NOT** enter anything in columns E and F before running the script.

---

### Step 5 – Run the Automation Script

```cmd
python test_automation.py --excel "Assignment_1_Test_cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 5000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --keep-open
```

**Parameter Reference:**

| Parameter | Default | Description |
|---|---|---|
| `--excel` | *(required)* | Path to the Excel test cases file |
| `--url` | *(required)* | URL of the transliteration application |
| `--wait-ms` | 5000 | Milliseconds to wait after typing before capturing output |
| `--type-delay-ms` | 80 | Delay (ms) between each keystroke to simulate real typing |
| `--slow-mo-ms` | 200 | Playwright slow-motion delay (ms) for visual debugging |
| `--save-every` | 1 | Save Excel file after every N test cases |
| `--keep-open` | False | Keep browser window open after all tests complete |
| `--headless` | False | Run without a visible browser window |

---

### Step 6 – Review Results

1. After the script finishes, reopen `Assignment_1_Test_cases.xlsx`.
2. Verify the **Actual output** (column E) and **Status** (column F) values.
3. All 50 test cases should show **Fail** (since they are negative test cases — the system is expected to produce incorrect output).
4. Manually review any unexpected **Pass** results and update the expected output if needed.

---

## Test Case Summary

The 50 negative test cases cover all 24 Singlish input types:

| # | Singlish Input Type | TCs |
|---|---|---|
| 1 | Question forms | Neg_0001, Neg_0002 |
| 2 | Command forms | Neg_0003, Neg_0004 |
| 3 | Greetings | Neg_0005, Neg_0006 |
| 4 | Requests | Neg_0007, Neg_0008 |
| 5 | Responses | Neg_0009, Neg_0010 |
| 6 | Repeated Words | Neg_0011, Neg_0012 |
| 7 | Inputs with Punctuation Marks | Neg_0013, Neg_0014 |
| 8 | Romanization / Spelling Variants | Neg_0015, Neg_0016 |
| 9 | Isolated English Word Insertions | Neg_0017, Neg_0018 |
| 10 | Multi-Word English Phrases | Neg_0019, Neg_0020 |
| 11 | English Digital Terms | Neg_0021, Neg_0022 |
| 12 | Platform/App Names | Neg_0023, Neg_0024 |
| 13 | English Abbreviations/Acronyms | Neg_0025, Neg_0026 |
| 14 | English Clipped Forms | Neg_0027, Neg_0028 |
| 15 | Place Names Embedded in Singlish | Neg_0029, Neg_0030 |
| 16 | Person Names Embedded in Singlish | Neg_0031, Neg_0032 |
| 17 | Inputs with Numbers and Numeric Suffixes | Neg_0033, Neg_0034 |
| 18 | Inputs with Currency | Neg_0035, Neg_0036 |
| 19 | Inputs with Time Formats | Neg_0037, Neg_0038 |
| 20 | Inputs with Dates | Neg_0039, Neg_0040 |
| 21 | Inputs with Unit of Measurements | Neg_0041, Neg_0042 |
| 22 | Inputs with Slang and Casual Phrasing | Neg_0043, Neg_0044 |
| 23 | Online Identifiers in Singlish | Neg_0045, Neg_0046 |
| 24 | Inputs Containing Emojis | Neg_0047, Neg_0048 |
| Free | Any type (multi-type) | Neg_0049, Neg_0050 |

---

## Troubleshooting

| Issue | Solution |
|---|---|
| `playwright not installed` | Run `pip install playwright openpyxl && playwright install` |
| Browser does not open | Try adding `--headless` flag or install Google Chrome |
| Script cannot find input field | Increase `--wait-ms` to 8000 or check if the site has changed |
| Excel not saving | Make sure the file is not open in Excel while the script runs |
| All results show Pass unexpectedly | Manually verify the expected output column against actual app output |

---

## Notes

- This project tests only the **Chat Sinhala** transliteration function.
- **Standard Sinhala**, backend APIs, performance, scalability, and security testing are **out of scope**.
- No examples from Appendix 1 or Appendix 2 of the assignment are reused in these test cases.

---

## Author

BSc (Hons) Information Technology – Year 3  
IT3040 ITPM – Semester 1 – Assignment 1 Option 1
