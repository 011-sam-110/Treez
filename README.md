# Survey Sentence Generator

A Windows desktop tool for tree surveyors. Tap phrase buttons to build formal arboricultural observations, then hit **GO** to paste the sentence directly into any field.

---

## Features

- **Phrase library** — organised tabs for Numbers, Crown, Condition, Species, Groups, and more
- **One-tap GO** — minimises the window, copies the sentence, and pastes it wherever your cursor is
- **AI Clean** — rewrites your draft into polished BS 5837 report language using Groq
- **Usage sorting** — most-used phrases float to the top automatically
- **Smart suggestions** — recommends phrases from other categories based on your history
- **Field Mode** — high-contrast dark theme built for outdoor screens
- **Edit phrases** — add, rename, or delete phrases and categories in-app
- **Auto-update** — checks GitHub on startup and installs new versions in one click

---

## Download

Go to [**Releases**](https://github.com/011-sam-110/Treez/releases/latest) and download `SurveySentenceGenerator.exe`.  
No installation required — just run it.

---

## Usage

1. Click phrases to build a sentence in the text box at the top
2. Press **GO** — the app minimises and pastes the sentence into the active window
3. Use **Clean** (requires Wi-Fi) to have AI tidy the sentence into formal report language
4. Use **Undo** to remove the last phrase, or **Clear** to start over

### Editing phrases

Click **Edit Phrases** in the header to enter edit mode:
- Each phrase gets **Edit** and **Del** buttons
- Click **+ Add phrase** at the end of any tab to add a new one
- Click the **⚙** gear icon on any tab to rename it, recolour it, or delete the category
- Click **＋ Category** to add a new tab

### Settings

Click **Settings** in the header to adjust:
- **Typing delay** — seconds between GO and paste (increase if paste misses the field)
- **Clear after GO** — whether the sentence box clears automatically after pasting
- **Phrase button text size**

---

## Building from source

Requires Python 3.10+.

```bash
git clone https://github.com/011-sam-110/Treez.git
cd Treez
```

Create `api_keys.py` with your Groq key (get one free at [console.groq.com](https://console.groq.com)):

```python
# api_keys.py
GROQ_API_KEY = "gsk_..."
```

Then build the executable:

```bash
python build.py
```

Output: `dist/SurveySentenceGenerator.exe`

---

## Publishing a new release

1. Bump `APP_VERSION` in `main.py` (e.g. `"1.0.0"` → `"1.1.0"`)
2. Run `python build.py`
3. On GitHub: **Releases → Draft a new release**
4. Tag it `v1.1.0`, upload `dist/SurveySentenceGenerator.exe`, publish

Users will see an **↑ Update** button in the header next time they open the app.

---

## Data storage

All user data is stored in `%APPDATA%\SurveySentenceGenerator\`:

| File | Contents |
|---|---|
| `phrases.json` | Your phrase library |
| `settings.json` | App settings |
| `usage.json` | Phrase usage counts |
| `survey_tool.log` | Debug log |

---

## Dependencies

| Package | Purpose |
|---|---|
| `pyautogui` | Keyboard paste on GO |
| `pyperclip` | Clipboard copy |
| `openai` | Groq API client (AI Clean) |
