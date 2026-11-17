# Samze Movie Database — Documentation

## What this project is

An IMDb-style movie catalogue web app. Users can browse movies and people, create accounts, leave reviews, follow others, keep watched lists, search/get recommendations, and (for contributor accounts) add or edit catalogue entries.

## Tech stack

| Layer | Choice | Why it’s used |
| --- | --- | --- |
| Server | Node.js + Express | HTTP routes and page rendering |
| Templates | Pug | Server-rendered HTML pages |
| Database | MongoDB | Flexible documents for movies, people, users, reviews |
| Sessions | express-session + connect-flash | Login state and one-time status messages |
| Front-end assets | Bootstrap + custom JS/CSS in `public/` | Layout and browser-side interactions |
| Seed data | JSON files (`movies.json`, `users.json`, `reviews.json`) | Starter catalogue content |

## How the logic works

1. **Server start** — `server.js` connects to a local MongoDB database (typically `movieDB`) and mounts routers for movies, people, users, auth, and create/edit flows.
2. **Browse pages** — Most routes fetch documents from MongoDB and render Pug templates (movie pages, actor/director/writer pages, lists).
3. **Accounts** — Sign-up/login routes create or verify users and store session info so the site knows who is signed in.
4. **Social features** — Logged-in users can review titles, follow people, and manage watched lists; those actions update the related collections.
5. **Contributor editing** — Elevated users get create/edit routes that write new or updated catalogue documents.
6. **Search / recommendations** — Query helpers look across stored movies/people and surface related suggestions from the local database (not a third-party movie API).

## Project map

### Root — server entry, routes, and data helpers
| Path | Role |
| --- | --- |
| `server.js` | Starts Express, connects to MongoDB, mounts routers, configures sessions |
| `movies.js` | Movie document helpers/queries |
| `person.js` | Actor/director/writer helpers |
| `users.js` | Account/profile helpers |
| `reviews.js` | Review create/read helpers |
| `movies.json`, `users.json`, `reviews.json` | Seed/sample data for local databases |
| `package.json` | Dependencies and start script |
| `README.md` / `DOCUMENTATION.md` | Setup + this overview |

#### Routers (URL → page or action)
These files are the “controllers”: they receive requests and decide what to load or save.

| Path | Role |
| --- | --- |
| `movies-router.js` | Browse/search movie pages and movie actions |
| `actors-router.js` / `directors-router.js` / `writers-router.js` | People catalogue pages |
| `users-router.js` | Profiles, follows, watched-list style user features |
| `loginRouter.js` / `signUpRouter.js` | Authentication flows |
| `createMovies-router.js` / `createPerson-router.js` / `createReviews-router.js` | Contributor create/edit forms |

### `public/` — what the browser renders
| Path | Role |
| --- | --- |
| `public/views/` | Pug templates (`pages/` for full pages, `partials/` for shared navbar/chunks) |
| `public/mainCSS/` | Project-specific stylesheets per page/feature |
| `public/css/` + `public/js/` | Vendor Bootstrap/jQuery assets |
| `public/pictures/` | Logos, placeholders, and UI images |

### `businessLogic/`
Holds supporting data/notes used during development (for example shortened movie sample JSON). The live request flow still centers on `server.js` + routers + Mongo helpers.

### Request path in one line
**Browser → router → helper (`movies.js` / `users.js` / …) → MongoDB → Pug view in `public/views/`.**

## Mental model

This is a **classic server-rendered catalogue site**: Express handles pages and forms, MongoDB stores everything, and sessions remember who’s logged in. It’s self-contained—no external movie API is required once the database is seeded.
