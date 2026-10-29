# Decision X-Ray AI

An educational AI-powered decision support web app. Analyze risks, assumptions, scenarios, alternatives and action plans, with a visual decision tree, saved history and browser PDF export.

## Prerequisites
- Python 3.10+
- Node.js 20+

## Start backend
```bash
cd backend
python -m venv .venv
# Windows PowerShell: .venv\Scripts\Activate.ps1
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
copy .env.example .env  # Windows; use cp on macOS/Linux
uvicorn main:app --reload
```
Backend API: http://127.0.0.1:8000/docs

## Start frontend (separate terminal)
```bash
cd frontend
npm install
npm run dev
```
Open http://127.0.0.1:5173

## Real AI mode
Edit `backend/.env`:
```
DEMO_MODE=false
OPENAI_API_KEY=your_key_here
OPENAI_MODEL=gpt-4o-mini
```
The default model is illustrative; select a model supported by your provider. A compatible provider can optionally be configured with `OPENAI_BASE_URL`. JSON-object response format must be supported.

## Demo mode
`DEMO_MODE=true` (default) shows clearly labeled illustrative results and does not contact an AI provider. It is not a real AI inference.

## API
- GET /api/health
- POST /api/analyze
- GET /api/history
- GET /api/history/{analysis_id}
- DELETE /api/history/{analysis_id}

## Limitations
- Local single-user educational prototype, not secure for public multi-user deployment.
- No authentication or account-level data separation.
- AI may produce incorrect or ungrounded conclusions; verify consequential decisions.
- PDF export uses browser Print > Save as PDF.
- API calls require internet access and may incur provider charges.
- This prototype has not been verified against every provider/model.
