# StudySaathi AI

A mobile-first study portal for Class 9–12, undergraduate degrees, MBA and M.Com. It includes an AI question solver that accepts typed questions or a photo of a question.

## Important: what is real and what needs setup

- The question solver calls the OpenAI API from the server. It is not a fake/demo answer generator.
- You must provide your own API key and a server host. API use may cost money and is not included with this code.
- **Never** put the API key in `public/` or in browser JavaScript.
- The PDF/resource cards link to official education portals; this starter does not host or redistribute textbooks itself.
- The interface is a starter project, not yet a complete authenticated LMS or a searchable database of every course PDF.

## Run locally

1. Install Node.js 20 or newer.
2. Copy `.env.example` to `.env`.
3. Put your API key in `.env` as `OPENAI_API_KEY=...`.
4. Run `npm install`.
5. Run `npm start`.
6. Open `http://localhost:3000`.

## Deploy

Deploy the whole project to a Node.js host that supports environment variables (for example, Render or Railway). Add `OPENAI_API_KEY` and optionally `OPENAI_MODEL` in the host's environment settings. A static-only host such as GitHub Pages cannot run `server.js`, so the AI endpoint will not work there by itself.

## Current features

- Responsive mobile layout and Hindi/English interface labels.
- Camera/file upload for a question photo (browser device picker may offer camera).
- Typed question + photo in one request.
- AI-generated step-by-step explanations across science, maths, commerce and management.
- Study resource links to official portals.
- Server-side API key handling and basic error messages.

## Before public launch

Add rate limiting, user accounts if needed, abuse controls, privacy notice, logging policy, spending limits, accessibility testing and subject-matter review. Don't upload private documents or personal information into the question scanner.
