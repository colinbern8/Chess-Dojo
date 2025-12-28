# 🥋 Chess Dojo

**Learn chess through personalized analysis and belt progression**

Chess Dojo is a chess training platform that analyzes your games, identifies your weaknesses, and helps you improve through a martial arts-inspired belt ranking system.

---

## 🎯 What is Chess Dojo?

Chess Dojo helps you become a better chess player by:
- **Analyzing your games** with AI-powered feedback
- **Tracking your progress** through a belt ranking system
- **Identifying patterns** in your play to focus your improvement

Think of it as your personal chess coach that learns from every game you play.

---

## 🥋 Belt System

Progress through 8 belt ranks based on your chess rating:

| Belt | Rating Range | Skill Level |
|------|--------------|-------------|
| ⚪ White | 0-800 | Beginner |
| 🟡 Yellow | 800-1200 | Novice |
| 🟠 Orange | 1200-1600 | Intermediate |
| 🟢 Green | 1600-2000 | Advanced |
| 🔵 Blue | 2000-2200 | Expert |
| 🟣 Purple | 2200-2400 | Master |
| 🟤 Brown | 2400-2600 | International Master |
| ⚫ Black | 2600+ | Grandmaster |

---

## ✨ MVP Features (Version 1.0)

### 📊 Game Analysis
- Upload or paste your chess games (PGN format)
- AI engine (Stockfish) evaluates every move
- See your mistakes categorized:
  - **Blunders** - Major mistakes that lose significant advantage
  - **Mistakes** - Errors that worsen your position
  - **Inaccuracies** - Suboptimal moves
- Get an accuracy score for each game

### 🔍 Pattern Recognition
- Automatic detection of recurring mistakes:
  - Hanging pieces (leaving pieces undefended)
  - Weak back rank
  - Moving into pins
  - King safety issues
- View your top 3 weaknesses with examples

### 📈 Progress Tracking
- Current rating and belt level
- Rating history graph
- Game statistics (wins/losses/draws)
- Accuracy trends over time
- Track improvement week-by-week

### 🎮 Simple Interface
- Clean, easy-to-use chess board
- Navigate through your analyzed games move-by-move
- Visual indicators for good moves and mistakes

---

## 🛠️ Tech Stack

**Frontend:**
- React - User interface
- Chess.js - Chess game logic
- react-chessboard - Visual chess board

**Backend:**
- Python FastAPI - API server
- PostgreSQL - Database
- Stockfish - Chess engine for analysis

---
