

# TDS Data Analyst Agent (Backend/API Only)

**Author:** Syed Ali Mujtaba  
**Student ID:** 21f1004482

This project is a backend-only, API-driven data analysis agent designed for the TDS course. It leverages FastAPI, Google Generative AI, and modern Python data tools to provide automated data analysis and insights via a simple HTTP API.

---

## 📦 Project Structure

- `app.py` — Main FastAPI application (API endpoints for analysis)
- `requirements.txt` — Python dependencies
- `Dockerfile` — Container build for Railway or any Docker host
- `entrypoint.sh` — Startup script (runs FastAPI server)
- `Procfile` — Process definition for Railway/Heroku
- `LICENSE` — MIT License
- `.gitignore` — Standard ignores

---

## 🚀 Deployment (Railway)

1. **Set up your environment variables:**
   - Create a `.env` file with:
     ```
     GOOGLE_API_KEY=your_actual_google_api_key_here
     ```
2. **Push your code to GitHub.**
3. **Deploy on Railway:**
   - Go to [Railway.app](https://railway.app)
   - Create a new project and link your GitHub repo
   - Railway will auto-detect your Dockerfile and build your app
   - Set your environment variables in the Railway dashboard
4. **Access your API:**
   - Railway will provide a public URL (e.g., `https://your-app-name.up.railway.app`)
   - Your main API endpoint will be at `/api`

---

## 🛠️ Local Development

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Run the app:
   ```bash
   uvicorn app:app --host 0.0.0.0 --port 8000
   # or
   python app.py
   ```
3. Test your API at: [http://localhost:8000](http://localhost:8000)

---

## 🧑‍💻 API Usage

Send a POST request to `/api` with your `questions.txt` and (optionally) a data file:

```bash
curl -X POST "https://your-app-name.up.railway.app/api" \
  -F "questions_file=@questions.txt" \
  -F "data_file=@your_data.csv"
```

- `questions_file` (required): Text file with your analysis questions
- `data_file` (optional): CSV, Excel, or JSON data file

The API will return a JSON response with answers and (if relevant) base64-encoded visualizations.

---

## ⚙️ Environment Variables

| Variable           | Description                        | Required |
|--------------------|------------------------------------|----------|
| `GOOGLE_API_KEY`   | Google Generative AI API Key        | Yes      |
| `PORT`             | App port (set by Railway)           | No       |
| `MODEL_NAME`       | LLM model name (default: Gemini)    | No       |
| `TEMPERATURE`      | LLM temperature (default: 0.7)      | No       |
| `MAX_TOKENS`       | Max tokens for LLM output           | No       |
| `REQUEST_TIMEOUT`  | Request timeout (seconds)           | No       |
| `API_TIMEOUT`      | API timeout (seconds)               | No       |

---

## 🐳 Docker Usage (Optional)

To build and run locally with Docker:

```bash
docker build -t tds-data-analyst .
docker run -p 8000:8000 --env-file .env tds-data-analyst
```

---

## 📝 Features

- LLM-powered data analysis and insight generation
- Supports multiple file formats (CSV, Excel, JSON)
- Automated chart/visualization generation (base64 images in JSON)
- Google Gemini integration
- Easy deployment to Railway (or any Docker host)

---

## 🆘 Troubleshooting

- **Missing modules:** Check your `requirements.txt`
- **API key errors:** Ensure `GOOGLE_API_KEY` is set in Railway variables
- **Port issues:** Railway sets the `PORT` variable automatically
- **Build errors:** Check Railway build logs for details

View logs in Railway dashboard under Deployments → View Logs, or with:
```bash
railway logs
```

---

## 📄 License

MIT License. See LICENSE for details.