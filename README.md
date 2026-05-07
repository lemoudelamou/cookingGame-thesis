#  Cooking Game — JSON Tools Suite

A multi-page Streamlit application for managing and validating game assets for a cooking game. Upload JSON configuration files to check images, sounds, and tools against reference libraries, validate schemas, convert recipes, and compare structures.

---

## Features

The app has four pages, accessible from the sidebar:

### 1.  JSON Conversion
Convert raw recipe data into the game's expected JSON structure. Useful for onboarding new content without manually writing the schema.

### 2.  Schema Validator
Validate uploaded JSON files against the game's schema rules. Surfaces structural errors and missing required fields.

### 3.  Asset Checker
Upload a JSON configuration file and verify that all referenced assets actually exist in the internal libraries. Checks three asset types:

- **Images** — checks fields: `openIcon`, `cursorBitmap`, `additiveOpenIcon`, `activeIcon`
- **Sounds** — checks fields: `sound`, `activeSound`, `doneSound`, `openSound`
- **Tools** — checks field: `tool`

For each asset type you get:
- A **Summary** tab with coverage statistics and a progress bar
- A **Found** tab listing all matched assets with their source JSON fields
- A **Missing** tab listing all unmatched assets with where they were referenced

You can also filter image checks by folder (e.g. only check assets in specific subdirectories).

### 4.  Structure Comparison
Compare two JSON structures side by side to identify differences between versions or variants of a game configuration.

---

## Setup & Installation

### Prerequisites

- Python 3.9+
- pip

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <repo-folder>
```

### 2. (Recommended) Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up environment variables

This app uses the **OpenAI API** (for the JSON Conversion page). Create a `.env` file in the project root:

```
OPENAI_API_KEY=your_openai_api_key_here
```

> You can get an API key at [platform.openai.com](https://platform.openai.com/api-keys).

### 5. Run the app

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`.

---



## Usage

1. Launch the app with `streamlit run app.py`
2. Use the **sidebar** to navigate between pages


---

## Notes

- The reference libraries (`png_files_dict.py`, `sounds_dict.py`, `tool_names.py`) must be kept up to date as new assets are added to the game
- The OpenAI API is only used by the **JSON Conversion** page; the other three pages work fully offline