# StudySaathi AI — Node.js server

This is a starter backend for the StudySaathi AI website. It provides:

- `GET /api/health` — checks that the server is running.
- `POST /api/ask` — sends a typed question and optional image to the OpenAI API.
- Static frontend hosting from the `public/` folder.

## 1. Put your website files in the right place

Copy your existing frontend files into `public/`, for example:

- `public/index.html`
- `public/style.css`
- any browser JavaScript and images used by the website

If your current frontend has a different structure, keep its folders and paths consistent.

## 2. Install Node.js

Use Node.js 20 or newer. In the project folder, run:

```bash
npm install
```

## 3. Set your API key privately

Copy `.env.example` to `.env` and replace `your_api_key_here` with your own OpenAI API key.

Do not upload `.env` to GitHub. Do not put the API key in HTML or browser JavaScript. The `.gitignore` file excludes `.env`.

API usage may incur charges; check your OpenAI API account's billing and usage limits.

## 4. Run locally

```bash
npm start
```

Open `http://localhost:3000`. Check `http://localhost:3000/api/health` to verify the server.

## 5. Connect your existing frontend

Your website's browser JavaScript should send a request to `/api/ask`:

```js
const response = await fetch("/api/ask", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    question: "Explain photosynthesis",
    language: "Hindi"
  })
});
const data = await response.json();
console.log(data.answer);
```

For image questions, send `image` as a base64 data URL (for example `data:image/jpeg;base64,...`). A file input must be converted to a data URL in browser JavaScript first. Keep request sizes reasonable.

An example helper is provided in `public/ask-example.js`. You may need to adapt it to your existing page's element IDs and design.

## 6. Deploy

Deploy the Node.js project to a Node.js hosting service such as Render or Railway. Add `OPENAI_API_KEY` (and optionally `OPENAI_MODEL`) in that service's environment-variable settings. The host should run `npm install` and `npm start`.

**Important:** GitHub Pages is static hosting and cannot run this `server.js`. You can keep your code in GitHub, but the backend must run on a Node.js host. If the frontend is hosted on a separate domain, configure CORS securely for that exact frontend origin before making browser requests.

## API request example

```json
{
  "question": "Explain photosynthesis",
  "language": "Hindi"
}
```

Optional image field:

```json
{
  "question": "Solve this question",
  "image": "data:image/jpeg;base64,....",
  "language": "Hindi"
}
```

Response:

```json
{
  "answer": "..."
}
```
