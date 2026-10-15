# Animeverse Catalog API — GitHub + Vercel

A small Vercel-ready Python/FastAPI backend for Animeverse. It uses AniList GraphQL for **catalog metadata** and does not need an API key for these public queries.

## Endpoints

- `GET /` — API information
- `GET /api/health` — health check
- `GET /api/anime/search?query=naruto&page=1&per_page=20`
- `GET /api/anime/trending?page=1&per_page=20`
- `GET /api/anime/popular?page=1&per_page=20`
- `GET /api/anime/genres`
- `GET /api/anime/info?id=21` — AniList ID; `21` is an example

## Deploy with GitHub + Vercel

1. Extract this ZIP and open the folder in VS Code.
2. Create a new empty GitHub repository.
3. In the VS Code terminal, run the commands below from this folder (replace the URL with your own repository URL):

```powershell
git init
git add .
git commit -m "Add Animeverse catalog API"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

4. Open https://vercel.com/ and choose **Add New → Project**.
5. Import the GitHub repository and deploy. Vercel should detect the Python function and install `requirements.txt`.
6. Test the deployment by opening `/api/health` and `/api/anime/search?query=naruto` on your deployed domain.

## Run locally

Requires Python 3.10+ and Node.js/npm. In PowerShell:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m pip install uvicorn
uvicorn api.index:app --reload
```

Then open `http://127.0.0.1:8000/docs`.

## Important scope note

This is a Vercel-deployable **catalog API**, not a conversion of Kuhi's stream extraction or HLS proxy system. Vercel serverless functions have execution/runtime constraints, and this project intentionally does not include provider-restriction bypasses or unauthorized copyrighted episode extraction. Add playback only through sources you are authorized to embed or distribute.
