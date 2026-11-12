# Project proposal

* Name: Tatchi Feudjio Willy Junior
* Project title: Board Game Collection
* Pitch (one sentence): A shared board-game shelf for cataloguing games and tracking play sessions, winners, and scores.
* Target users: Board-game enthusiasts and local game groups who want to manage a shared collection and play history.

## Pages

| URL | Content | Dynamic segment? | Rendering strategy and why |
|---|---|---|---|
| / | Game Shelf (Home): public catalog of owned games, quick filters (player count and complexity), and summary stats (total games and plays) | No | Server-rendered with static generation and revalidation so the catalog is SEO-friendly while updates appear periodically. |
| /games/[slug] | Game Details & Play History: game metadata, complexity, play-session history, and a way to delete old sessions | Yes — `[slug]` identifies the game | Server-rendered so individual game pages are crawlable and show current play history. |
| /games/new | Add a Game: form for title, player range, playtime, complexity, and cover image URL | No | Client Component form with loading and error states; the page itself can be static because the form is shared. |
| /games/[slug]/edit | Edit Game Details: pre-filled form to update or delete a game | Yes — `[slug]` identifies the game | Client Component fetches the current game details and submits updates or deletion. |
| /sessions | Global Play Log: chronological feed of play sessions, recent winners, and scores | No | Server-rendered so recent activity is visible when the page loads. |
| /sessions/new | Log a Play Session: form to choose a game and enter the date, player count, winner, and notes; may preselect a game from a query parameter | No | Client Component form with loading and error states; a `?game=...` query parameter can preselect the game. |

## Data

Entities (2 to 4), their main fields, and how they are related:

* **BoardGame**: `id`, `slug`, `title`, `description`, `minPlayers`, `maxPlayers`, `playTimeMinutes`, `complexity`, `coverImageUrl`.
* **PlaySession**: `id`, `playedAt`, `playerCount`, `winnerName`, `scores`, `notes`, `boardGameId`.
* A board game can have many play sessions; each play session belongs to one board game.

## Write actions

What users can create, update or delete:

* Add, update, and delete board games in the shared shelf.
* Log and delete play sessions for a board game.
* No login is required; the shelf and play history are shared.

## Repository

GitHub URL: [Add repository URL]