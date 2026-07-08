# CineScope 🎬

A movie discovery website built with React — search movies, view details, and
build your own watchlist. Built as a college front-end project.

## Tech used

- React (JavaScript, no TypeScript)
- React Router
- Fetch API
- OMDb API for movie data
- localStorage for auth + watchlist (no backend)
- Plain CSS (no frameworks)

## Setup

1. Install dependencies:
   ```
   npm install
   ```

2. Get a free OMDb API key: go to https://www.omdbapi.com/apikey.aspx,
   choose the FREE tier, and enter your email. The key shows up in your
   inbox in a minute or two.

3. Open `src/utils/api.js` and replace `YOUR_API_KEY_HERE` with your key:
   ```js
   const API_KEY = "your_actual_key_here";
   ```

4. Run the app:
   ```
   npm start
   ```

   It will open at http://localhost:3000

## How it works

- **Home page** loads a "Trending" and "Popular" row by fetching a hardcoded
  list of movie titles from OMDb (OMDb doesn't have a real trending endpoint
  like TMDB does).
- **Search** reads the query from the URL (`/search?q=batman`) and hits
  OMDb's search endpoint.
- **Movie Details** fetches full info (plot, cast, ratings, etc.) by IMDb ID.
- **Login/Sign Up** is fully fake — no server. User accounts are stored in
  `localStorage` under the key `cinescope_users`, and the current logged-in
  user under `cinescope_current_user`.
- **Watchlist** is stored per-user in localStorage
  (`cinescope_watchlist_<username>`), so each account has its own list.

## Folder structure

```
src/
  components/   -> Navbar, MovieCard, SearchBar, Loader, Footer
  pages/        -> Home, Search, MovieDetails, Login, Profile, NotFound
  utils/        -> api.js, auth.js, watchlist.js
  App.js
  index.js
  index.css
```

## Known limitations

- Auth is not secure (plain text passwords in localStorage) — this is a
  front-end only demo, not meant for real users.
- OMDb's free tier is limited to 1,000 requests/day.
- No pagination on search results (OMDb returns up to 10 per page; this
  project just shows the first page).
