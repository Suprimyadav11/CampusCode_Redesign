# CampusCode — Build. Compete. Ship.

CampusCode is a responsive student-community and hackathon portal built with **React**, **TypeScript**, **React Router**, and **Vite**. It includes a public landing page, demo authentication screens, and a student dashboard with sample events and activity.

This repository is a front-end demonstration. It does not include a production backend, database, or real account authentication.

## Contents

- [Features](#features)
- [Technology stack](#technology-stack)
- [Project structure](#project-structure)
- [Requirements](#requirements)
- [Run the project locally](#run-the-project-locally)
- [Available routes](#available-routes)
- [How the application works](#how-the-application-works)
- [Build for production](#build-for-production)
- [Important notes](#important-notes)

## Features

### Public landing page

- CampusCode branding and navigation.
- Sections introducing the community, mission, process, hackathons, and ways to join.
- Responsive layouts for desktop and mobile screens.
- Scroll-based visual effects, marquee animation, and reduced-motion support.
- Local font files, logo assets, and an experience video with a poster image.

### Login and registration

- Separate login and registration routes.
- Email and password validation.
- Registration form validation, password confirmation, and password-strength feedback.
- Password visibility controls and accessible form feedback.
- Demo session handling on the client side.

### Student dashboard

- Protected dashboard route that checks for a client-side student session.
- Student profile and dashboard statistics.
- Hackathon/event exploration and event-detail dialogs.
- Event registration state, recent activity, notifications, and help dialog.
- Sample dashboard data and browser storage for selected state.

## Technology stack

| Technology | Purpose |
| --- | --- |
| React 19 | Component-based user interface |
| TypeScript | Typed application code |
| React Router 7 | Client-side routing |
| Vite | Development server and production bundler |
| CSS | Layout, responsive styling, themes, and animations |
| Browser Storage | Demo session and dashboard-state persistence |

## Project structure

```text
campuscode/
├── public/
│   ├── brand/                  # CampusCode logo variants
│   ├── fonts/                  # Locally stored font files
│   ├── videos/                 # Experience video and poster image
│   └── favicon.svg             # Browser tab icon
├── src/
│   ├── components/
│   │   ├── dashboard/          # Reusable dashboard components and dialogs
│   │   ├── Brand.tsx           # Brand mark component
│   │   ├── ExperienceSection.tsx
│   │   ├── Marquee.tsx
│   │   ├── ScrollManager.tsx
│   │   └── SiteHeader.tsx
│   ├── lib/
│   │   ├── auth-helpers.ts     # Email/password validation helpers
│   │   ├── icons.tsx           # Shared icon components
│   │   ├── student-session.ts  # Demo session and dashboard storage
│   │   └── useLandingEffects.ts
│   ├── pages/
│   │   ├── AuthPage.tsx        # Login and registration page
│   │   ├── LandingPage.tsx     # Public home page
│   │   └── StudentDashboard.tsx
│   ├── sections/               # Landing-page sections
│   ├── styles/                 # Global, landing, auth, dashboard, and animation CSS
│   ├── App.tsx                 # Route definitions
│   └── main.tsx                # React application entry point
├── index.html                  # HTML entry point and page metadata
├── package.json                # Scripts and dependencies
├── package-lock.json           # npm dependency lockfile
├── bun.lock                    # Bun dependency lockfile
├── tsconfig.json               # TypeScript configuration
├── vite.config.ts              # Vite configuration
└── README.md
```

## Requirements

Install the following before starting:

- **Node.js** (a current LTS release is recommended).
- **npm**, which is included with Node.js.

Check the installed versions:

```bash
node --version
npm --version
```

## Run the project locally

1. Extract the ZIP archive.
2. Open the extracted project folder in a terminal or VS Code.
3. Install the dependencies:

   ```bash
   npm install
   ```

4. Start the development server:

   ```bash
   npm run dev
   ```

5. Open the local URL printed by Vite. The Vite configuration uses port `3000`, so the usual address is:

   ```text
   http://localhost:3000
   ```

Keep the terminal running while using the development site. Stop the server with `Ctrl + C`.

## Available routes

| Route | Description |
| --- | --- |
| `/` | Public CampusCode landing page |
| `/login` | Demo login form |
| `/register` | Demo registration form |
| `/dashboard` | Student dashboard; requires a demo session |

Unknown routes redirect to the home page.

## How the application works

### Application startup and routing

`src/main.tsx` mounts the React application and wraps it in `BrowserRouter`. `src/App.tsx` declares the routes and connects each route to its page component. `ScrollManager` handles route-related scroll behavior.

### Authentication demo

`src/pages/AuthPage.tsx` renders the login or registration interface according to the selected route. Shared validation helpers are kept in `src/lib/auth-helpers.ts`. Successful demo authentication creates a client-side student session through `src/lib/student-session.ts`.

### Student dashboard

The dashboard is assembled from reusable components in `src/components/dashboard/`. The session and sample dashboard data are managed by `src/lib/student-session.ts`. Event, notification, and session state is stored in the browser where implemented, so the demo can retain selected state between page visits in the same browser.

### Styling and media

The styles are organized by purpose in `src/styles/`. Fonts, logos, the video, and its poster image are served from `public/`. Vite serves files in `public/` from the site root, so they are referenced by paths such as `/brand/campuscode-logo.svg` and `/videos/what-is-campuscode.mp4`.

## Build for production

Run the TypeScript check and create the optimized production build:

```bash
npm run build
```

The generated site is placed in the `dist/` directory.

To preview the production build locally:

```bash
npm run preview
```

## Useful npm scripts

| Command | Purpose |
| --- | --- |
| `npm run dev` | Start the local development server |
| `npm run build` | Type-check and create the production build |
| `npm run preview` | Preview the production build |
| `npm run lint` | Run the TypeScript compiler check |

## Important notes

- This is a **front-end demo**, not a production authentication system.
- Login and registration do not communicate with a server or create real user accounts.
- Dashboard content includes sample data. Browser storage is used for demo persistence where implemented.
- Do not use real passwords or sensitive personal information in this demo.
- No external API keys or backend environment variables are required to run the current front-end project.
- Keep `package-lock.json` committed so npm installs the dependency versions recorded for this project.
