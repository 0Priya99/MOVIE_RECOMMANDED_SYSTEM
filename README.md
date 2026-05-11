# 🎬 Movie Recommendation System

A smart, personalized movie recommendation engine that suggests films based on user preferences, viewing history, and collaborative filtering techniques.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Recommendation Algorithms](#recommendation-algorithms)
- [Dataset](#dataset)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 🧠 Overview

The **Movie Recommendation System** is a full-stack application that delivers personalized movie suggestions to users. It combines **Content-Based Filtering**, **Collaborative Filtering**, and a **Hybrid Model** to provide highly accurate recommendations based on:

- User watch history
- Genre and actor preferences
- Ratings and reviews
- Trending and popular movies
- Similar user behavior patterns

---

## ✨ Features

- 🔐 **User Authentication** — Secure sign-up, login, and session management
- 🎯 **Personalized Recommendations** — AI-driven suggestions tailored to each user
- 🔍 **Advanced Search** — Search movies by title, genre, cast, director, or year
- ⭐ **Ratings & Reviews** — Rate movies and read community reviews
- 📋 **Watchlist** — Save movies to watch later
- 📈 **Trending Section** — Discover what's popular right now
- 🌐 **Movie Details Page** — Full info including synopsis, cast, trailer, and ratings
- 🧩 **Similar Movies** — See related movies on every detail page
- 📱 **Responsive Design** — Works seamlessly on desktop, tablet, and mobile
- 🌙 **Dark Mode** — Easy on the eyes for late-night browsing

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| React.js | UI Framework |
| Redux Toolkit | State Management |
| Tailwind CSS | Styling |
| Axios | HTTP Requests |

### Backend
| Technology | Purpose |
|---|---|
| Python / FastAPI | REST API Server |
| SQLAlchemy | ORM |
| PostgreSQL | Relational Database |
| Redis | Caching & Sessions |
| JWT | Authentication Tokens |

### ML / Recommendation Engine
| Technology | Purpose |
|---|---|
| scikit-learn | Machine Learning Models |
| Pandas / NumPy | Data Processing |
| Surprise (SVD) | Collaborative Filtering |
| NLTK / spaCy | NLP for Content Filtering |

### DevOps
| Technology | Purpose |
|---|---|
| Docker & Docker Compose | Containerization |
| GitHub Actions | CI/CD Pipeline |
| AWS / Render | Cloud Deployment |

---

## 📁 Project Structure

```
movie-recommendation-system/
│
├── backend/
│   ├── app/
│   │   ├── api/
│   │   │   ├── routes/
│   │   │   │   ├── auth.py
│   │   │   │   ├── movies.py
│   │   │   │   ├── recommendations.py
│   │   │   │   └── users.py
│   │   ├── core/
│   │   │   ├── config.py
│   │   │   └── security.py
│   │   ├── models/
│   │   │   ├── movie.py
│   │   │   └── user.py
│   │   ├── services/
│   │   │   ├── recommender.py
│   │   │   └── movie_service.py
│   │   └── main.py
│   ├── ml/
│   │   ├── collaborative_filtering.py
│   │   ├── content_based.py
│   │   ├── hybrid_model.py
│   │   └── preprocess.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── redux/
│   │   ├── services/
│   │   └── App.jsx
│   ├── package.json
│   └── Dockerfile
│
├── data/
│   ├── movies.csv
│   └── ratings.csv
│
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/) v18+
- [Python](https://www.python.org/) 3.10+
- [PostgreSQL](https://www.postgresql.org/) 14+
- [Redis](https://redis.io/)
- [Docker](https://www.docker.com/) *(optional but recommended)*

---

### Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/your-username/movie-recommendation-system.git
cd movie-recommendation-system
```

#### 2. Backend Setup

```bash
cd backend

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate       # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run database migrations
alembic upgrade head

# Start the server
uvicorn app.main:app --reload --port 8000
```

#### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start the development server
npm run dev
```

#### 4. Run with Docker (Recommended)

```bash
# Build and start all services
docker-compose up --build
```

The app will be available at `http://localhost:3000`.

---

### Configuration

Create a `.env` file in the `backend/` directory based on `.env.example`:

```env
# App
APP_NAME=MovieRecommendSystem
SECRET_KEY=your_secret_key_here
DEBUG=True

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/moviedb

# Redis
REDIS_URL=redis://localhost:6379

# TMDB API (for movie metadata)
TMDB_API_KEY=your_tmdb_api_key_here

# JWT
ACCESS_TOKEN_EXPIRE_MINUTES=60
```

> 🔑 Get your free TMDB API key at [https://www.themoviedb.org/settings/api](https://www.themoviedb.org/settings/api)

---

## 📖 Usage

1. **Register** a new account or **log in** with existing credentials.
2. Complete the **onboarding quiz** to set your initial genre preferences.
3. Browse the **Home** page for personalized recommendations.
4. **Search** for any movie using the search bar.
5. Click a movie to view its **details**, trailer, and similar suggestions.
6. **Rate** movies you've watched to improve future recommendations.
7. Add movies to your **Watchlist** to keep track of what to watch next.

---

## 🔌 API Endpoints

### Authentication
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Login and receive JWT token |
| POST | `/api/auth/logout` | Logout and invalidate token |

### Movies
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/movies` | Get paginated list of movies |
| GET | `/api/movies/{id}` | Get movie details by ID |
| GET | `/api/movies/search?q=` | Search movies by query |
| GET | `/api/movies/trending` | Get trending movies |

### Recommendations
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/recommendations` | Get personalized recommendations |
| GET | `/api/recommendations/similar/{id}` | Get movies similar to a given movie |
| GET | `/api/recommendations/genre/{genre}` | Get recommendations by genre |

### User
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/users/me` | Get current user profile |
| POST | `/api/users/rate` | Submit a movie rating |
| GET | `/api/users/watchlist` | Get user's watchlist |
| POST | `/api/users/watchlist/{id}` | Add movie to watchlist |
| DELETE | `/api/users/watchlist/{id}` | Remove movie from watchlist |

Full API documentation is available at `http://localhost:8000/docs` (Swagger UI).

---

## 🤖 Recommendation Algorithms

### 1. Content-Based Filtering
Recommends movies similar to ones the user has enjoyed, based on:
- Genre tags
- Director and cast
- Plot keywords (TF-IDF on synopsis)
- Release year and language

### 2. Collaborative Filtering (SVD)
Analyzes patterns from many users to find similar users and recommend what they liked using **Matrix Factorization (SVD)** via the `Surprise` library.

### 3. Hybrid Model
Combines both approaches with a weighted scoring system:

```
final_score = (α × content_score) + (β × collaborative_score)
```

Where `α` and `β` are tunable weights (default: `0.4` and `0.6`).

---

## 📊 Dataset

This project uses the [MovieLens Dataset](https://grouplens.org/datasets/movielens/) and enriches it with live metadata from the **TMDB API**.

| Dataset | Records |
|---|---|
| Movies | 45,000+ |
| Ratings | 26,000,000+ |
| Users | 270,000+ |

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. **Fork** this repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and **commit**: `git commit -m "Add your feature"`
4. **Push** to your branch: `git push origin feature/your-feature-name`
5. Open a **Pull Request**

Please follow the [Code of Conduct](CODE_OF_CONDUCT.md) and ensure all tests pass before submitting.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 📬 Contact

**Your Name**
- GitHub: [@your-username](https://github.com/your-username)
- Email: your.email@example.com
- LinkedIn: [linkedin.com/in/your-profile](https://linkedin.com/in/your-profile)

---

> ⭐ If you found this project helpful, please consider giving it a star on GitHub!
