# Casino Bonus Scraper & Live Tracker

A complete, single-command automated toolchain designed to fulfill a screening assessment. It pulls raw bonus data from a public casino promotion feed, structures unstructured text fields using an LLM pipeline, and serves the results dynamically on a mobile-friendly frontend view.

## 🚀 Setup & Installation

### 1. Prerequisites
Ensure you have **Python 3.8+** installed on your system.

### 2. Install Dependencies
Clone this repository to your local setup and install the required modules:
```bash
pip install requests beautifulsoup4 openai
```

### 3. Configure API Keys
The scraper leverages OpenAI's structured outputs (`gpt-4o-mini`). Export your API key in your terminal environment:
```bash
# MacOS/Linux
export OPENAI_API_KEY="your-api-key-here"

# Windows (Command Prompt)
set OPENAI_API_KEY=your-api-key-here
```
*Note: If no API key is specified, the script falls back gracefully to standard rule-based parsing outputs to avoid crashing.*

## 🛠️ How To Run

Execute the pipeline using a single command:
```bash
python scraper.py
```
This action generates a freshly updated `casinos.json` in the active root directory.

## 🌐 Deploying to GitHub Pages

This project is fully structured to run right out of the box via **GitHub Pages**:
1. Push this entire codebase to a public/private GitHub repository.
2. Navigate to your repository settings page: **Settings -> Pages**.
3. Under the **Build and deployment** section, select **Deploy from a branch** and point the source path directly to your `main` or `master` branch root folder (`/`).
4. Hit Save. Your live tracker page will be accessible at `https://<your-username>.github.io/<your-repo-name>/`.
