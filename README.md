# Chess Journey: Python Chess Game with Custom GUI and AI

*A completely reworked school project, originally based on the tutorial series ["Chess Engine in Python" by Eddie Sharick](https://www.youtube.com/watch?v=EnYui0e73Rs&list=PLBwF487qi8MGU81nDGaeNE1EnNEPYWKY_).*

> [!WARNING]
> **Project Archived**
> 
> This project is no longer actively maintained.
> 
> **Context:**  
> This repository holds a special place in my history as my very first serious programming project from school. Years later, upon rediscovering the original source code, I faced a dilemma: it was too valuable as a personal milestone to simply delete, yet I was hesitant to publish it on GitHub in its original, beginner-level state. 
> 
> To resolve this, I decided to completely reimagine and rebuild the idea from scratch, applying modern Python practices, robust architecture, and the tools I have mastered since. This repository now serves as a unique time capsule, presenting the modernized rewrite alongside the original `legacy` code to document my growth as a developer.
> 
> **Reason for Archiving:**  
> Having successfully served its purpose as a comprehensive learning milestone and architectural exercise, I no longer have an interest in further maintaining this codebase. For a detailed explanation of the project's scope, deliberate design choices, and known limitations, please refer to the [End of Journey](#end-of-journey) section below.

## Brief Overview

This project implements complete chess rules logic using the [python-chess](https://github.com/niklasf/python-chess) library, paired with a custom graphical user interface built on [pygame-ce](https://github.com/pygame-community/pygame-ce) and [pygame-gui](https://github.com/MyreMylar/pygame_gui). Configuration is cleanly managed via [Pydantic Settings](https://github.com/pydantic/pydantic-settings). Additionally, it features deep integration with the powerful [Stockfish](https://stockfishchess.org/) engine, allowing you to play either against the computer or locally with a friend.

## Available Documentation

- [English Documentation](README.md) (current document).
- [Документация на русском языке](README_RU.md).

## Project Structure

```bash
chess-journey/
├── docs/
│   ├── architecture_en.md      # Detailed system architecture documentation (in English)
│   ├── architecture_ru.md      # Detailed system architecture documentation (in Russian)
│   └── journey-learnings.md    # Key learnings obtained during development (Russian only)
└── src/
    ├── chess_game/             # Source code of the fully reworked chess game
    └── legacy/                 # Original tutorial code for memory
```

## Quick Start

### I. Prerequisites

| Component            | Requirement                               |
| :------------------- | :---------------------------------------- |
| **Package Manager**  | [`Pixi`](https://pixi.prefix.dev/latest/) |
| **Operating System** | GNU/Linux-based system                    |
| **Architecture**     | `x86_64`                                  |

> **Note:**  
> These are not strict requirements, but rather the baseline environment where the code is 
guaranteed to run out of the box. Alternative setups are possible but may require manual 
configuration.

### II. Setup

1. **Clone the repository**

    ```bash
    git clone https://github.com/snegoviol/chess-journey.git
    cd chess-journey
    ```

2. **Install dependencies and configure environment**

    ```bash
    pixi install
    pixi run copy-env
    ```

3. **Set up Stockfish**
   - Download the appropriate [Stockfish binary](https://stockfishchess.org/download/) for your platform.
   - Place the executable file in the `src/chess_game/assets/stockfish/` directory.
   - Verify or update the file path in your `.env` configuration file if necessary.

### III. Launch

Once the setup is complete, the chess game can be started with a single command:

```bash
pixi run launch-chess-game
```

> **Want to understand the system better?**  
> If you are interested in the underlying architecture, check out the detailed [architecture documentation](docs/architecture_en.md).

### IV. Legacy Version (Optional)

If you wish to explore or run the original version of the codebase, you can set it up and launch it using the following commands:

```bash
pixi run setup-legacy-images
pixi run launch-legacy-code
```

## License

Each file in this repository is licensed under the [MIT No Attribution License](LICENSE.txt).

## Known Issues

- **Castling in Chess960**  
Castling in Chess960 variants does not work due to input handling conflicts in the graphical interface. Chess960 castling requires moving the king to the rook's square, but the current mouse click handler selects the rook piece on that square instead of processing it as a valid destination square for the king's move, preventing castling from occurring. However, when the AI makes a castling move, it works correctly since the AI uses the python-chess library directly.

- **GameScreen.update()**  
The `update()` method is never explicitly called in the code, but for some reason it is necessary for proper timer display. Removing this unused method breaks the timer's ability to properly display current time values.

- **AI Settings**  
Text input fields can be clicked when AI settings are active (visual bug, text input does not occur).

## Possible Improvements

- **Enhanced Slider Interface**  
Sliders currently do not display their current numeric values. It would be great to add visual feedback showing the current value, and ideally update the displayed value in real-time while dragging the slider, providing immediate feedback on parameter adjustments.

- **Move Logging**  
Implement proper game move logging and display in standard chess notation. The original tutorial code had basic move display functionality, but this feature was intentionally omitted in the rework to focus on core architectural improvements. Adding this functionality would restore the full game history for users.

- **Robust Error Handling**  
Add proper validation of user settings and implement comprehensive `None` checking throughout the code to improve application stability.

- **Full Pawn Promotion**  
Expand pawn promotion to support all piece types in addition to the queen.

- **Proper UI Layout Management**  
Replace hardcoded positions, sizes, and margins with a proper layout system for widgets and screens.

- **PyGame GUI Themes**  
Add PyGame GUI themes to enhance visual design and user experience.

## End of Journey

This project was never intended to be a finished chess application. It was created as an educational project, with the goal of learning through practice. The project initially aimed to create a minimal viable product (MVP) demonstrating modern Python development practices, object-oriented architecture, and integration with modern libraries such as `python-chess`, `pygame-ce`, and `pygame_gui`.

The [Known Issues](#known-issues) and [Possible Improvements](#possible-improvements) described above were deliberately left unfixed as conscious decisions made in the spirit of rapid development. Moreover, creating a full-featured game in PyGame implies using Python, and choosing Python for games is questionable when specialized high-performance alternatives like [Godot](https://github.com/godotengine/godot) exist for serious game development.
