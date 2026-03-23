# AI Mock Interview Web App

A React + TypeScript + Vite single-page app to create, manage, and run mock coding interviews with user authentication using Clerk.

## 🚀 Features

- Clerk auth flow (`signin`, `signup`, `signout`) integrated
- Protected route structure with role-based pages
- Interview generation, editing, and feedback
- SPA client-side routing with `react-router-dom`
- Toast notifications using custom provider
- Vite build + optimization

## 📁 Project structure

- `src/App.tsx` - Router layout for public, auth, and protected paths
- `src/main.tsx` - Clerk provider + app bootstrap
- `src/routes/*` - Page components
- `src/layouts/*` - Layout wrappers and authentication guards
- `src/components/*` - UI components (generate, question-section, modal, etc.)
- `src/provider/toast-provider.tsx` - toast wrapper

## 🧩 Local setup

1. node 18+ and npm.
2. copy `.env.example` to `.env` (if provided) or set env keys:
   - `VITE_CLERK_PUBLISHABLE_KEY`
   - `VITE_CLERK_FRONTEND_API` (if required by Clerk)
3. install:

```bash
npm install
```

4. start:

```bash
npm run dev
```

5. production build:

```bash
npm run build
npm run preview
```

## 🔧 Vercel deployment (SPA setup)

1. In project root, add `vercel.json`:

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

2. Set Vercel Project settings:
   - Build command: `npm run build`
   - Output directory: `dist`

3. Add env vars in Vercel:
   - `VITE_CLERK_PUBLISHABLE_KEY`
   - `VITE_CLERK_FRONTEND_API`

4. Clerk redirect URLs:
   - `https://<your-domain>.vercel.app`
   - `https://<your-domain>.vercel.app/signin`
   - `https://<your-domain>.vercel.app/signup`

## 🛠 Routing

`App.tsx` uses `BrowserRouter` and defines:

- `/` home
- `/signin/*`, `/signup/*`
- `/generate`, `/generate/:interviewId`, `/generate/interview/:interviewId`, etc.

This is why the Vercel rewrite to `/index.html` is required.

## 🧪 Verification flow

1. Access app root
2. Visit `/generate` directly (should not 404)
3. Sign in via Clerk and confirm callback returns to app route

## 🤝 Contributing

- Fork repo, branch from `main`
- Add features/tests
- PR with clear description

## 📜 License

MIT
