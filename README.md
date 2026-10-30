# JARVIS AI — voice + typing starter

## Features
- Type messages and receive AI responses.
- Use browser speech recognition for microphone input.
- Hear AI responses through browser text-to-speech.
- Toggle spoken replies and stop speech at any time.
- Responsive web app that can be installed on a phone or desktop as a PWA.

## Run
Requires Python 3.10+ and an OpenAI API key with API access. ChatGPT subscription and API billing are separate.

```bash
python -m venv .venv
# Windows PowerShell: .venv\Scripts\Activate.ps1
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
```
Set the API key in your shell, never in frontend code:
```bash
# macOS/Linux
export OPENAI_API_KEY="your_api_key"
# Windows PowerShell
$env:OPENAI_API_KEY="your_api_key"
```
Start:
```bash
uvicorn app:app --reload
```
Open http://127.0.0.1:8000

## Phone setup
For a quick same-Wi-Fi test, run:
```bash
uvicorn app:app --host 0.0.0.0 --port 8000
```
Find your computer's local IP and visit `http://COMPUTER-IP:8000` on your phone. Microphone and PWA installation generally require HTTPS or localhost; use a trusted HTTPS deployment for normal phone use. In the browser menu choose **Install app** or **Add to Home Screen**.

## Browser voice support
Speech synthesis is broadly supported. Speech recognition availability varies by browser and operating system; current Chrome/Edge builds are the most practical starting point. The browser will ask for microphone permission. This is push-to-talk, not always-listening wake-word activation.

## Safety and production notes
This is a starter, not a finished always-on agent. It does not directly control your computer, send email, or change calendar events. Gmail connected to ChatGPT is not automatically exposed to this separately hosted app.

Before public deployment, add user authentication, rate limiting, HTTPS, secure secret management, logging with privacy controls, and CSRF protections as appropriate. Add integrations one at a time using least-privilege credentials. Consequential actions must use a separate server-side approval step that displays the exact action and target and requires a fresh explicit confirmation. Do not execute actions merely because the model says to.
