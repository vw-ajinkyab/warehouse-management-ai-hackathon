Next.js frontend for the VW LogiMind Warehouse AI control tower.

> For overall architecture, the API contract, the AI cascade, and Docker/EC2
> deployment, see the [root README](../README.md) — this file only covers
> frontend-specific setup.

## Backend API configuration

This app talks to the Node.js backend in `../backend` through the typed
client in [`lib/workbook-api.ts`](lib/workbook-api.ts). Copy the example env
file and point it at your backend:

```bash
cp .env.local.example .env.local
```

`NEXT_PUBLIC_API_URL` defaults to `http://localhost:8000` for local dev. For
a deployed environment (e.g. both apps running on the same EC2 instance),
change it to the instance's public IP or domain:

```bash
NEXT_PUBLIC_API_URL=http://<EC2-PUBLIC-IP>:8000
```

Note this value is baked in at build time (it's a `NEXT_PUBLIC_*` var), so
rebuild the frontend after changing it. Never put LLM/API secret keys here —
only the backend talks to the LLM provider.

> `lib/api.ts` and `lib/types.ts` are unused leftovers from an earlier
> FastAPI-based scaffold (they reference `/api/v1` and a different data
> model) — nothing imports them. Safe to delete, or ask to have them removed.

## Getting Started

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the app. The
backend must be running separately (see the root README) for real data to
load.

## Learn More

- [Next.js Documentation](https://nextjs.org/docs)
- [Learn Next.js](https://nextjs.org/learn)
