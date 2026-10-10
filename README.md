# GPR Stock Scanner — Streamlit

## Files
- `streamlit_app.py`: app utama
- `requirements.txt`: dependencies

## Run locally
```bash
pip install -r requirements.txt
export ARJUM_API_KEY="YOUR_KEY"
streamlit run streamlit_app.py
```

On Windows PowerShell:
```powershell
$env:ARJUM_API_KEY="YOUR_KEY"
streamlit run streamlit_app.py
```

## Deploy to Streamlit Community Cloud
1. Upload `streamlit_app.py` and `requirements.txt` to a GitHub repository.
2. Create an app in Streamlit Community Cloud and select `streamlit_app.py`.
3. In app Settings → Secrets, add:
```toml
ARJUM_API_KEY = "YOUR_ARJUM_KEY"
```
4. Do not commit API keys to GitHub.

## Important limitations
- App attempts to retrieve a broad ticker directory from a public dataset API. If unavailable, it uses a fallback ticker list which is not guaranteed complete/current.
- Arjum `/api/screener/latest` is not used as the universe because it may return only a few screener matches.
- The app requests `/api/history/{code}?interval=...`; intraday support must be verified with actual API responses.
- Large scans create many provider requests and may take time or hit provider quotas. Start with 50.
- The GPR code is a Python implementation of the existing model core; it has not been numerically validated against the original Pine Script.
- Predictions are experimental, not financial advice.
