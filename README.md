# The 8Bits Hangman 🎮

A retro pixel-art Hangman game with a React + TypeScript frontend and a Go + Gin REST API.

## Features ✨

- Pixel-art retro style with 8-bit aesthetics
- Responsive design that works on desktop and mobile
- Keyboard support for letter input
- Visual hangman display that updates with each wrong guess
- Game state management (win/lose conditions)
- Animated UI elements for a more engaging experience
- REST API for game logic, scoring, and leaderboard

## Tech Stack 🖥️

**Frontend** (`front/`)

- React 19 + TypeScript
- Vite 7 (Fast Refresh + HMR)
- Tailwind CSS 4 for styling
- Class Variance Authority for component variants
- Radix UI for accessible dialog components
- Custom pixel-art animations

**Backend** (`back/`)

- Go — fast and efficient programming language
- Gin — high-performance HTTP web framework
- PostgreSQL — optional database for leaderboard and persistent storage
- Go Testing — comprehensive test suite with the standard Go `testing` package

## Getting Started 🚀

### Prerequisites

- [Bun](https://bun.sh)
- Go 1.16 or higher
- Git

### Clone

```bash
git clone https://github.com/N95Ryan/the-8bits-hangman.git
cd the-8bits-hangman
```

### Frontend

```bash
cd front
cp .env.example .env
bun install
bun dev
```

### Backend

```bash
cd back
cp .env.example .env
go mod tidy
go run main.go
```

The API is available at `http://localhost:8080` by default.

## Project Structure

```
├── front/          # React + Vite application
├── back/           # Go + Gin API
│   ├── main.go     # Application entry point
│   ├── game/       # Game logic and word management
│   ├── handlers/   # HTTP request handlers
│   ├── models/     # Data structures
│   └── utils/      # Helper functions
└── README.md
```

## Deployment 🌐

The frontend can be deployed to Vercel, Netlify, or any other static site hosting:

```bash
cd front
bun run build
bun run preview
```

## API Endpoints

### Game Management

- `POST /api/games` — Create a new game session
- `GET /api/games/:id` — Retrieve current game state
- `POST /api/games/:id/guess` — Submit a letter guess
- `DELETE /api/games/:id` — Abandon a game

### User Management

- `POST /api/users/register` — Register a new user
- `POST /api/users/login` — Authenticate a user

### Leaderboard

- `GET /api/leaderboard` — Get top scores
- `POST /api/leaderboard` — Submit a score

### ID Format

All IDs in the system (games, users, tokens) follow a standardized format:

- 3 digits followed by 3 uppercase letters (e.g., `123ABC`, `789XYZ`)
- This format provides ~17.5 million unique combinations
- Easy to read, communicate, and remember

### Example Response

```json
{
  "id": "755XRK",
  "status": "in_progress",
  "remaining": 8,
  "word": "_______",
  "guesses": ["A", "E"],
  "score": 0
}
```

## Development

### Running Tests

```bash
cd back
go test ./... -v
```

### API Testing

You can use Postman or any other API testing tool to interact with the endpoints.
For example, to create a new game:

```
POST http://localhost:8080/api/games
Content-Type: application/json

{
  "player_name": "Player1"
}
```
