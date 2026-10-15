# AI-Assistent
# 📄 AI Resume ATS Checker

A Streamlit app that scores your resume for Applicant Tracking Systems (ATS) and suggests concrete improvements, powered by Google Gemini Flash.

## Features

- Upload a resume as **PDF, DOCX or TXT**
- Overall **ATS score (0-100)** plus a breakdown (formatting, keywords, impact, skills, education, readability)
- Strengths, weaknesses and **missing keywords**
- Prioritized **improvement suggestions** with specific fixes
- **Before/after rewrite examples** for weak bullet points
- Optional **job description** for targeted keyword matching
- Download the full report as JSON

## Tech stack

- [Streamlit](https://streamlit.io) for the UI
- [Google Gemini API](https://ai.google.dev) (`gemini-2.5-flash` by default) via the `google-genai` SDK
- `pypdf` and `python-docx` for text extraction

## Run locally

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

pip install -r requirements.txt
```

Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey), then provide it in one of these ways:

1. **Secrets file (recommended):** create `.streamlit/secrets.toml`

   ```toml
   GEMINI_API_KEY = "your-api-key"
   ```

2. **Environment variable:**

   ```bash
   export GEMINI_API_KEY="your-api-key"      # Windows: set GEMINI_API_KEY=your-api-key
   ```

3. **Sidebar:** paste the key into the app's sidebar box.

Start the app:

```bash
streamlit run app.py
```

## Configuration

| Variable | Default | Purpose |
|---|---|---|
| `GEMINI_API_KEY` | none | Your Gemini API key |
| `GEMINI_MODEL` | `gemini-2.5-flash` | Change the Gemini model name |

## Deploy on Streamlit Community Cloud

1. Push this repo to GitHub (never commit your API key).
2. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
3. Click **Create app**, choose your repo, branch `main`, and main file `app.py`.
4. Open **Advanced settings → Secrets** and add:

   ```toml
   GEMINI_API_KEY = "your-api-key"
   ```

5. Click **Deploy**.

## Notes and limitations

- Scanned (image-only) PDFs cannot be read; use a text-based PDF or DOCX.
- The ATS score is an AI estimate, not the output of a real ATS. Use it as guidance.
- Resume text is sent to Google's Gemini API for analysis. Do not upload anything you are not comfortable sharing.

## License

MIT
