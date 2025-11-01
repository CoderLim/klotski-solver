# Klotski Solver

<div align="center">

![Klotski](https://img.shields.io/badge/Klotski-Puzzle%20Game-orange?style=for-the-badge)
![Next.js](https://img.shields.io/badge/Next.js-15+-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5+-blue?style=for-the-badge&logo=typescript)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

A modern, interactive Klotski puzzle game with AI solver capabilities built with Next.js 15 and TypeScript

[🌐 Live Demo](https://klotski.org/klotski-solver) | [🚀 Quick Start](#-quick-start) | [🎮 Game Rules](#-game-rules)

</div>

---

## ✨ Features

- 🎮 **Interactive Gameplay** - Drag & drop, touch support, and keyboard controls
- 🧩 **40+ Classic Layouts** - Traditional Chinese Klotski puzzles with varying difficulty
- 🤖 **AI Solver** - Intelligent puzzle solving with step-by-step demonstration
- 🎯 **Smart Detection** - Real-time collision detection, boundary constraints, and win conditions
- ⏱️ **Progress Tracking** - Move counter, timer, and game history
- 🔄 **Undo/Redo** - Complete operation history management
- 💾 **Auto Save** - LocalStorage persistence for game progress
- 🎨 **Modern UI** - Beautiful gradient design with smooth animations
- 📱 **Responsive** - Works perfectly on desktop and mobile devices
- 🎵 **Sound Effects** - Audio feedback for moves, wins, and errors (mutable)
- ♿ **Accessibility** - ARIA labels, keyboard navigation, and high contrast focus

## 🚀 Quick Start

### Prerequisites

- Node.js 18+
- npm / pnpm / yarn

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/CoderLim/klotski-solver.git
cd klotski-solver

# 2. Install dependencies
npm install
# or
pnpm install

# 3. Run development server
npm run dev
# or
pnpm dev

# 4. Open your browser
# http://localhost:3000
```

### Build for Production

```bash
npm run build
npm start
```

### Run Tests

```bash
# Run unit tests
npm test

# Test coverage
npm run test:coverage
```

## 🎮 Game Rules

### Objective
Move the red **Cao Cao block (2×2)** to the exit position at the bottom center of the board.

### Controls

#### Mouse/Touch
- Drag blocks directly to move them

#### Keyboard Controls
- `Tab` / `Shift+Tab` - Navigate between blocks
- `Arrow Keys` - Move selected block (1 step)
- `Enter` - Select/deselect block
- `U` - Undo last move
- `R` - Redo
- `Ctrl+R` - Reset puzzle
- `ESC` - Close dialogs

### Block Types

| Block | Size | Color | Description |
|-------|------|-------|-------------|
| Cao Cao | 2×2 | Red | Target block, must reach exit |
| Vertical General | 2×1 | Blue | Vertical rectangular block |
| Horizontal General | 1×2 | Green | Horizontal rectangular block |
| Soldier | 1×1 | Gray | Small square block |

## 🤖 AI Solver

The game features an intelligent AI solver that can:

- **Analyze** any puzzle configuration
- **Find optimal solutions** using advanced algorithms
- **Demonstrate solutions** step-by-step with auto-play
- **Show statistics** including total moves and solve time
- **Control playback** with play, pause, stop, and step controls

### Solver Features

- 🧠 **Smart Algorithm** - Uses efficient search algorithms
- ⚡ **Fast Solving** - Optimized for performance
- 📊 **Detailed Stats** - Move count, solve time, states explored
- 🎬 **Auto Demo** - Watch the AI solve puzzles automatically
- ⏯️ **Playback Controls** - Full control over solution demonstration

## 📂 Project Structure

```
klotski-solver/
├── app/                      # Next.js App Router
│   ├── page.tsx             # Main game page
│   ├── layout.tsx           # Root layout
│   └── globals.css          # Global styles
├── components/              # React components
│   ├── game/
│   │   ├── Board.tsx        # Game board
│   │   ├── Block.tsx        # Draggable blocks
│   │   └── PuzzlePreview.tsx # Puzzle preview
│   └── ui/
│       ├── SolverControl.tsx # AI solver controls
│       ├── Modal.tsx        # Modal dialogs
│       └── ConfirmDialog.tsx # Confirmation dialogs
├── lib/                     # Core logic
│   ├── puzzles/
│   │   ├── types.ts         # Type definitions
│   │   └── index.ts         # Puzzle database (40+ puzzles)
│   ├── engine/
│   │   ├── collision.ts     # Collision detection
│   │   ├── movement.ts      # Movement logic
│   │   ├── validation.ts    # Boundary validation
│   │   └── win.ts           # Win condition checking
│   ├── solver/
│   │   ├── index.ts         # AI solver interface
│   │   ├── types.ts         # Solver types
│   │   └── klotski-wrapper.ts # External solver integration
│   ├── store/
│   │   └── useGameStore.ts  # Zustand state management
│   └── utils/
│       ├── grid.ts          # Grid calculations
│       ├── colors.ts        # Color mapping
│       └── sound.ts         # Audio management
├── __tests__/               # Unit tests
│   └── engine.test.ts
├── public/                  # Static assets
└── package.json
```

## 🧩 Puzzle Database

The game includes **40+ classic Klotski puzzles** with varying difficulty:

### Difficulty Distribution
- 🟢 **Easy**: 2 puzzles
- 🟡 **Medium**: 12 puzzles  
- 🟠 **Hard**: 20 puzzles
- 🔴 **Expert**: 6 puzzles

### Popular Puzzles
- **Heng Dao Li Ma** (横刀立马) - Classic hard puzzle
- **Jin Zai Zhi Chi** (近在咫尺) - Easy beginner puzzle
- **Ceng Ceng She Fang** (层层设防) - Multi-layered defense
- **Shui Xie Bu Tong** (水泄不通) - Expert level challenge

## 🛠️ Technology Stack

- **Framework**: Next.js 15 (App Router)
- **Language**: TypeScript 5
- **State Management**: Zustand + Immer
- **Styling**: Tailwind CSS 4
- **Animations**: Framer Motion
- **AI Solver**: Custom klotski library integration
- **Testing**: Vitest + Testing Library
- **Code Quality**: ESLint + TypeScript

## 🎯 Performance

- ⚡ **First Load**: < 1s
- 🎯 **Drag Response**: 60 FPS
- 💾 **State Persistence**: Real-time
- 📦 **Bundle Size**: < 500KB (gzipped)
- 🧠 **AI Solving**: < 5s for most puzzles

## 🧪 Adding New Puzzles

### Step 1: Define Puzzle Configuration

Add new puzzle configuration in `lib/puzzles/index.ts`:

```typescript
const myPuzzleConfig: PuzzleConfig = {
  name: 'My Puzzle',
  slug: 'my-puzzle',
  difficulty: 'medium', // 'easy' | 'medium' | 'hard' | 'expert'
  blocks: [
    { shape: [2, 2], position: [0, 1] }, // Cao Cao (must have one)
    { shape: [2, 1], position: [0, 0] }, // Vertical general
    { shape: [1, 2], position: [2, 1] }, // Horizontal general
    { shape: [1, 1], position: [3, 1] }, // Soldier
    // ... more blocks
  ],
};
```

### Step 2: Register to Puzzle Map

```typescript
export const PUZZLES: Record<string, PuzzleConfig> = {
  // ... existing puzzles
  'my-puzzle': myPuzzleConfig,
};
```

### Step 3: Validation

The configuration is automatically validated:
- Board size: 5×4
- No overlapping blocks
- All blocks within boundaries
- Must contain exactly one 2×2 red block

## 🤝 Contributing

We welcome contributions! Please follow these steps:

### Development Workflow

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Standards

- Follow TypeScript strict mode
- Use ESLint configuration
- Write tests for new features
- Use functional components with Hooks
- Add proper type annotations

## 📊 Game Statistics

### Classic Layouts Performance

| Puzzle | Difficulty | Avg. Moves | Avg. Time |
|--------|------------|------------|-----------|
| Heng Dao Li Ma | Hard | 80+ | 5-10 min |
| Jin Zai Zhi Chi | Easy | 60+ | 2-5 min |
| Ceng Ceng She Fang | Hard | 100+ | 8-15 min |
| Shui Xie Bu Tong | Expert | 120+ | 15-30 min |

## 🎯 Roadmap

- [x] Core gameplay mechanics
- [x] AI solver integration
- [x] 40+ classic puzzles
- [x] Responsive design
- [ ] Multiplayer mode
- [ ] Custom puzzle editor
- [ ] Leaderboards
- [ ] PWA support
- [ ] Hint system
- [ ] More puzzle variations

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Klotski puzzle inspiration from traditional Chinese puzzle games
- Classic layouts referenced from historical literature and online resources
- UI design inspired by modern arcade games
- AI solver powered by the klotski library

---

<div align="center">

**If you find this project useful, please give it a ⭐ Star!**

Made with ❤️ by [Your Name]

[🐛 Report Bug](https://github.com/CoderLim/klotski-solver/issues) · [💡 Request Feature](https://github.com/CoderLim/klotski-solver/issues)

</div>
