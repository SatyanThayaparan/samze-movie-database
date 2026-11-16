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

1. Clone the repo and enter the project folder:

```bash
git clone https://github.com/SatyanThayaparan/samze-movie-database.git
cd samze-movie-database
```

2. Install [Node.js](https://nodejs.org/) and [MongoDB Community](https://www.mongodb.com/try/download/community). Start the MongoDB service so `mongodb://localhost:27017` is reachable.
3. Install npm dependencies:

```bash
npm install
```

4. Seed the `movieDB` database (from the project root, with MongoDB running):

```bash
mongoimport --db movieDB --collection movies --file movies.json --jsonArray
mongoimport --db movieDB --collection users --file users.json --jsonArray
mongoimport --db movieDB --collection reviews --file reviews.json --jsonArray
```

Or use MongoDB Compass: connect to `mongodb://localhost:27017`, create database `movieDB`, then import each JSON file into the matching collection.

5. Start the server:

```bash
npm start
```

6. Open `http://127.0.0.1:3000` (or the URL printed in the terminal).

## Usage

- Browse movie and people lists without an account
- Register / log in to review, follow, and track watched movies
- Contributing accounts can create catalogue entries

## Project structure

```text
samze-movie-database/
├── server.js                 # Express entrypoint (DB: movieDB)
├── businessLogic/            # users, search, contributing logic
├── public/                   # static assets and client scripts
├── movies.json / users.json / reviews.json
├── *-router.js               # route modules
└── package.json
```

## Notes

- The server expects MongoDB at `mongodb://localhost:27017` and database name `movieDB`.
