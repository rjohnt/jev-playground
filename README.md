# Jev Playground

A sentiment and emotional tone playground powered by [TypeSafe Jev](https://typesafe.ai). Enter freeform text and watch the dominant emotion light up, with confidence and probabilities for ten labels.

## Run locally

Requires Node.js 22 or later. No dependencies to install.

```sh
cp .env.example .env.local
# Edit .env.local and add your TypeSafe API key.
npm start
```

Open http://localhost:4317. Analysis runs automatically after a 700 ms typing pause; an Analyze button and sample messages are also available.

## How it works

The browser sends text to the local Node server, which calls TypeSafe's `POST /v1/systemone` endpoint with `jev-latest` and a Choice question. The API key stays on the server. Results include a dominant label, probabilities, and confidence. Confidence summarizes the distribution; it is not a guarantee that the interpretation is correct.

Labels: happy, sad, neutral, funny, angry, anxious, excited, affectionate, confused, and mixed. The question asks for one dominant emotional tone, even when multiple emotions could apply.

The server binds to the local machine only. This is a local playground; add authentication and usage limits before deploying a publicly accessible API proxy. Text you analyze is sent to TypeSafe.

## Credentials

Create your own `.env.local` from the empty `.env.example`. Environment files are ignored by Git. Never commit an API key.

## Documentation

- [TypeSafe API](https://docs.typesafe.ai/api)
- [Choice questions](https://docs.typesafe.ai/primitives/choice)
- [Confidence](https://docs.typesafe.ai/confidence)
