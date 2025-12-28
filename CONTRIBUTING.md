# Contributing to Chess Dojo

Thank you for your interest in contributing to Chess Dojo! This document provides guidelines and workflows for team collaboration.

---

## 🚀 Getting Started

### 1. Initial Setup
```bash
# Fork and clone the repository
git clone https://github.com/yourusername/chess-dojo.git
cd chess-dojo

# Add upstream remote
git remote add upstream https://github.com/original/chess-dojo.git

# Install dependencies
cd frontend && npm install
cd ../backend && pip install -r requirements.txt
```

### 2. Environment Setup

Create `.env` files in both frontend and backend:

**Frontend `.env`:**
```
REACT_APP_API_URL=http://localhost:8000
REACT_APP_STOCKFISH_PATH=/path/to/stockfish
```

**Backend `.env`:**
```
DATABASE_URL=postgresql://user:password@localhost:5432/chess_dojo
REDIS_URL=redis://localhost:6379
SECRET_KEY=your-secret-key-here
STOCKFISH_PATH=/path/to/stockfish
```

---

## 📋 Development Workflow

### Branch Naming Convention

- `feature/feature-name` - New features
- `bugfix/bug-description` - Bug fixes
- `hotfix/critical-fix` - Urgent production fixes
- `docs/documentation-update` - Documentation changes
- `refactor/code-improvement` - Code refactoring

**Examples:**
- `feature/belt-progression-system`
- `bugfix/puzzle-rating-calculation`
- `docs/api-endpoint-documentation`

### Standard Workflow

1. **Create a new branch from main**
```bash
   git checkout main
   git pull upstream main
   git checkout -b feature/your-feature-name
```

2. **Make your changes**
   - Write clean, readable code
   - Follow code style guides (see below)
   - Add comments for complex logic
   - Write tests for new features

3. **Commit your changes**
```bash
   git add .
   git commit -m "Add feature: brief description"
```

4. **Push to your fork**
```bash
   git push origin feature/your-feature-name
```

5. **Create a Pull Request**
   - Go to GitHub and create a PR
   - Fill out the PR template
   - Request review from team member
   - Address any feedback

6. **Merge after approval**
   - Squash and merge for clean history
   - Delete branch after merge

---

## 💻 Code Style Guidelines

### Python (Backend)

- Follow PEP 8 style guide
- Use type hints
- Maximum line length: 100 characters
- Use meaningful variable names
```python
# Good
def calculate_centipawn_loss(engine_eval: float, player_eval: float) -> float:
    """Calculate centipawn loss for a move."""
    return abs(engine_eval - player_eval)

# Avoid
def calc(e, p):
    return abs(e - p)
```

**Tools:**
- `black` for formatting
- `pylint` for linting
- `mypy` for type checking

### JavaScript/React (Frontend)

- Use ES6+ features
- Functional components with hooks
- Destructuring when possible
- Meaningful component and variable names
```javascript
// Good
const ChessBoard = ({ position, onMove }) => {
  const [selectedSquare, setSelectedSquare] = useState(null);
  
  const handleSquareClick = (square) => {
    // Handle click
  };
  
  return <Board position={position} />;
};

// Avoid
const CB = (props) => {
  const [s, setS] = useState(null);
  return <Board {...props} />;
};
```

**Tools:**
- `prettier` for formatting
- `eslint` for linting

### File Organization

**Frontend:**
```
src/
├── components/
│   ├── common/          # Reusable components (Button, Card, etc.)
│   ├── chess/           # Chess-specific components
│   ├── lessons/         # Lesson components
│   └── dashboard/       # Dashboard components
├── pages/               # Page-level components
├── hooks/               # Custom React hooks
├── services/            # API calls
├── utils/               # Utility functions
├── contexts/            # React contexts
└── styles/              # Global styles
```

**Backend:**
```
src/
├── api/
│   ├── routes/          # API endpoints
│   └── schemas/         # Pydantic models
├── models/              # Database models
├── services/            # Business logic
├── utils/               # Helper functions
└── tests/               # Test files
```

---

## 🧪 Testing

### Running Tests
```bash
# Frontend
cd frontend
npm test

# Backend
cd backend
pytest
```

### Writing Tests

- Write tests for all new features
- Aim for 80%+ code coverage
- Test edge cases and error handling

**Example (Python):**
```python
def test_calculate_accuracy():
    # Arrange
    moves = [{"eval": 0.5}, {"eval": -0.3}]
    
    # Act
    accuracy = calculate_game_accuracy(moves)
    
    # Assert
    assert 0 <= accuracy <= 100
```

**Example (JavaScript):**
```javascript
describe('ChessBoard', () => {
  it('should render 64 squares', () => {
    render(<ChessBoard />);
    const squares = screen.getAllByTestId('square');
    expect(squares).toHaveLength(64);
  });
});
```

---

## 📝 Commit Message Guidelines

Use conventional commits format:
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples:**
```
feat(puzzles): add puzzle difficulty rating system

Implemented algorithm to calculate puzzle difficulty based on
solve rate and user ratings.

Closes #42
```
```
fix(analysis): correct centipawn loss calculation

Previous calculation didn't account for mate scores.
```

---

## 🔍 Pull Request Guidelines

### PR Template

When creating a PR, include:

1. **Description**: What does this PR do?
2. **Motivation**: Why is this change needed?
3. **Changes**: List of specific changes
4. **Testing**: How was this tested?
5. **Screenshots**: If UI changes, include before/after
6. **Related Issues**: Link to relevant issues

### PR Checklist

- [ ] Code follows style guidelines
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] No console errors
- [ ] Responsive design (for UI changes)
- [ ] Tested on different browsers (for UI)

### Review Process

1. At least one approval required
2. All CI checks must pass
3. No merge conflicts
4. Comments addressed

---

## 🐛 Bug Reports

When reporting bugs, include:

1. **Description**: Clear description of the bug
2. **Steps to Reproduce**: Detailed steps
3. **Expected Behavior**: What should happen
4. **Actual Behavior**: What actually happens
5. **Screenshots**: If applicable
6. **Environment**: Browser, OS, etc.

**Template:**
```markdown
**Bug Description:**
Puzzle rating doesn't update after solving

**Steps to Reproduce:**
1. Go to Puzzle Trainer
2. Solve a puzzle correctly
3. Check puzzle rating

**Expected:** Rating increases by ~10 points
**Actual:** Rating stays the same

**Environment:** Chrome 120, Windows 11
```

---

## 🎯 Feature Requests

When suggesting features:

1. **Description**: What feature do you want?
2. **Use Case**: Why is it useful?
3. **Proposed Solution**: How might it work?
4. **Alternatives**: Other approaches considered
5. **Priority**: How important is this?

---

## 📚 Documentation

### Code Documentation

- Add JSDoc comments for complex functions
- Document API endpoints with examples
- Keep README.md up to date

**Example:**
```javascript
/**
 * Calculates the accuracy percentage for a chess game
 * @param {Array<Object>} moves - Array of move objects with evaluations
 * @param {string} userColor - 'white' or 'black'
 * @returns {number} Accuracy percentage (0-100)
 */
function calculateGameAccuracy(moves, userColor) {
  // Implementation
}
```

### Documentation Updates

When adding features, update:
- README.md (if user-facing)
- FEATURES.md (detailed specs)
- API documentation (if backend changes)
- Comments in code

---

## 🤝 Communication

### Team Channels

- **GitHub Issues**: Bug reports, feature requests
- **GitHub Discussions**: General questions, ideas
- **Pull Requests**: Code review, technical discussion
- **[Your Team Chat]**: Quick questions, daily sync

### Asking for Help

Don't hesitate to ask questions! Use:
- GitHub Discussions for general questions
- Issue comments for specific bugs
- PR comments for code review questions

---

## 🎨 Design Guidelines

### UI/UX Principles

- **Consistency**: Use design system components
- **Accessibility**: WCAG 2.1 AA compliance
- **Responsive**: Mobile-first approach
- **Performance**: Optimize images, lazy load

### Color Scheme
```
Belt Colors (for reference):
- White: #FFFFFF
- Yellow: #FFD700
- Orange: #FF8C00
- Green: #32CD32
- Blue: #1E90FF
- Purple: #9370DB
- Brown: #8B4513
- Black: #000000
```

---

## 🚨 Security

### Security Practices

- Never commit secrets or API keys
- Use environment variables
- Sanitize user input
- Follow OWASP guidelines

### Reporting Security Issues

Email security concerns to: [security-email@example.com]

Do NOT create public GitHub issues for security vulnerabilities.

---

## 📋 Task Management

### Issue Labels

- `bug` - Something isn't working
- `feature` - New feature request
- `enhancement` - Improve existing feature
- `documentation` - Documentation improvements
- `good first issue` - Good for newcomers
- `help wanted` - Extra attention needed
- `priority: high/medium/low`
- `status: in-progress/blocked/review`

### Project Board

We use GitHub Projects for task tracking:
- **Backlog**: Future work
- **To Do**: Ready to start
- **In Progress**: Currently working on
- **Review**: Awaiting code review
- **Done**: Completed

---

## ✅ Definition of Done

A feature is "done" when:

- [ ] Code is written and tested
- [ ] All tests pass
- [ ] Code reviewed and approved
- [ ] Documentation updated
- [ ] Merged to main branch
- [ ] Deployed (if applicable)
- [ ] Issue/ticket closed

---

## 🎓 Learning Resources

### Chess Programming
- [Chess Programming Wiki](https://www.chessprogramming.org/)
- [Stockfish Documentation](https://stockfishchess.org/)

### React/Frontend
- [React Documentation](https://react.dev/)
- [React Chess Board Library](https://github.com/Clariity/react-chessboard)

### FastAPI/Backend
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [SQLAlchemy Documentation](https://docs.sqlalchemy.org/)

---

**Questions?** Open a GitHub Discussion or reach out to the team!

**Happy Coding! 🚀♟️**
