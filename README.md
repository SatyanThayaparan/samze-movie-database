# Samze Movie Database

IMDb-style movie catalogue web app with users, reviews, people pages, and contributing-user tools.

## Features

- Browse movies, actors, directors, and writers
- User accounts, follows, and watched lists
- Reviews on movies
- Search and recommendations
- Contributing users can add or remove movies
- Express + Pug server with MongoDB-backed data

## Tech stack

- Node.js
- Express
- Pug
- MongoDB
- Bootstrap / client-side JS

## Setup

1. Install [Node.js](https://nodejs.org/) and [MongoDB](https://www.mongodb.com/try/download/community) (or MongoDB Compass for local imports).
2. Install dependencies from the project root:

```bash
npm install
```

3. Start MongoDB locally, then import seed data (`movies.json`, `users.json`, `reviews.json`) into your collections via Compass or `mongoimport`.
4. Confirm the Mongo connection string in the server config matches your local instance (default is often `mongodb://localhost:27017`).
5. Start the server:

```bash
npm start
```

## Usage

Open `http://127.0.0.1:3000` (or the URL printed by the server).

- Browse movie and people lists without an account
- Register / log in to review, follow, and track watched movies
- Contributing accounts can create catalogue entries

## Project structure

```text
samze-movie-database/
├── server.js                 # Express entrypoint
├── businessLogic/            # users, search, contributing logic
├── public/                   # static assets and client scripts
├── *-router.js               # route modules
└── package.json
```

## Notes

- Seed JSON files and router modules expect a running MongoDB instance before first use.
