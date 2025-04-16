# ♟️ ChessOOP - A Java-Based Chess Game



> 🎯 **OOP Project-3 | Java | DSA | GUI | Chess Game**

---

## 📌 Introduction

Welcome to **ChessOOP**, a fully interactive chess game built with **Java Swing** and guided by **Object-Oriented Programming principles**. This project is built for learners, coders, and enthusiasts who want to:

- Understand how OOP works in practice 👨‍💻
- Build GUI-based applications using Java 🧱
- Develop strategic games with real-time logic ♜



---

## ✨ Key Features

- ✅ Two-player chess game (White vs Black)
- ✅ Clean, intuitive Java Swing GUI
- ✅ Valid move highlighting & capturing
- ✅ Player-based timer ⏱️
- ✅ Modular OOP design (extendable!)
- ✅ Java JAR executable for one-click play 🧩

---

## 📂 Folder Structure

```
ChessOOP/
├── Chess/                     # Contains core logic and main gameplay management
│   ├── Main.java              # Entry point of the program; sets up the board and starts the game
│   ├── Cell.java              # Represents each square on the board, manages selection and highlighting
│   ├── Time.java              # Manages the countdown timer for each player
│   ├── Player.java            # Holds player information: name, color, captured pieces, etc.
│
├── Pieces/                   # Abstract and concrete classes for each chess piece
│   ├── Piece.java             # Abstract base class for all pieces; defines shared behaviors and properties
│   ├── Pawn.java              # Implements pawn-specific move logic and promotion handling
│   ├── King.java              # Implements king movement and check/checkmate logic
│   ├── Rook.java              # Handles linear horizontal/vertical movement logic
│   ├── Bishop.java            # Handles diagonal movement logic
│   ├── Knight.java            # Handles L-shaped movement logic
│   ├── Queen.java             # Combines logic of rook and bishop
│
├── Executable JAR/           # Contains precompiled JAR file for quick execution of the game
│   └── Chess.jar              # Double-clickable runnable file to launch the application
│
├── Screenshots/              # Visual references used in documentation and the README
│   ├── gameboard.png          # Screenshot of the board UI in action
│   └── checkmate.png          # Screenshot showing checkmate popup or endgame screen
│
├── Class Diagram/            # UML diagrams representing class structure and relationships
│   └── chess-uml.png          # Visual representation of core class interactions and inheritance
│
├── docs/                     # Contains all formal documentation files
│   ├── Project Documentation.docx      # Final project report with code and UI walkthrough
│   └── Software Requirement Specification.docx  # Describes system design, scope, and requirements
│
├── README.md                 # This file – main presentation file for project documentation
├── LICENSE                   # MIT License file for open-source sharing
```



---

## 🧠 Concept Overview

**Data Structures Used in the Game:**

To manage the logic and GUI for ChessOOP, several core data structures have been utilized:

- **2D Array (********`Piece[][] board`********\*\*\*\*)**: The chessboard is implemented using a two-dimensional array where each cell contains a `Piece` or `null`. This makes it easy to map board coordinates to piece positions.
- **ArrayList**: Used to store active pieces for each player, captured pieces, and to dynamically track legal moves.
- **HashMap** (optional depending on implementation): Can be used to associate positions with specific logic (e.g., highlighting, move history).
- **Stack** (recommended for future): Ideal for implementing undo/redo functionality by tracking move history.

These data structures were chosen to keep time complexity low, simplify the management of GUI updates, and allow real-time interaction.

**Design Principles Used:**

- ✅ Abstraction
- ✅ Inheritance
- ✅ Polymorphism
- ✅ Encapsulation
- ✅ MVC-like separation

Each piece, cell, and player is modeled with real-world behaviors, creating a smooth, extendable backend.



---

## 🕹️ How to Play

### 🎮 Launching the Game

- Clone or download the repository
- Run the `Chess.jar` file from `Executable JAR/`
- OR open `Main.java` in your IDE and run the project

### ♟️ Game Rules Supported

- All standard chess moves
- Capturing
- Check and Checkmate detection
- Turn-based logic



---

## 🛠️ Tech Stack

| Purpose         | Technology         |
| --------------- | ------------------ |
| Language        | Java               |
| GUI Framework   | Java Swing         |
| IDE             | IntelliJ / Eclipse |
| Version Control | Git + GitHub       |
| UML Diagrams    | Draw\.io           |
| File Packaging  | JAR Executable     |

---

## 🧩 Module Breakdown

### 🔹 Main.java (The Heart of the Game)

This is the **core controller class** that manages the entire game experience.

- **Extends**: `JFrame` → Provides the main game window
- **Implements**: `MouseListener` → Allows interaction with chessboard cells

**Key Responsibilities:**
- Initializes and lays out the GUI components
- Creates and positions all chess pieces on the board
- Handles all user interactions (clicks, player selection, game start)
- Implements the timer and countdown using the `Time` class
- Switches turns after valid moves
- Highlights valid moves and enforces rules (like check and checkmate)
- Ends the game with stats update and winner announcement

**Important Functions:**
- `mouseClicked()` – Main game loop, controls selection and moves
- `changechance()` – Toggles turn between players
- `checkmate()` – Verifies if the opponent has any valid moves
- `gameend()` – Ends the match, announces winner, and resets board

### 🔹 Chess

- `Main.java`: The main controller class that handles the GUI, event listeners, board initialization, move validation, turn switching, game end, and player interactions. It manages the full gameplay lifecycle.

- `Cell.java`: This class represents a **single square on the chessboard**. Since the board has 8×8 squares, you'll have 64 `Cell` objects.
  
  **Key Responsibilities:**
  - Holds a `Piece` (or is empty)
  - Tracks whether the cell is selected, under check, or a possible move destination
  - Changes background and borders based on the game state
  - Can be cloned to simulate future moves (used in check/checkmate logic)

  **Important Methods:**
  - `setPiece()` / `removePiece()` – Add or remove a chess piece from this cell  
  - `select()` / `deselect()` – Handles visual highlighting when clicked  
  - `setcheck()` / `removecheck()` – Marks a cell red when a king is under attack  
  - `setpossibledestination()` – Highlights legal moves in blue  
  - Implements `Cloneable` for deep-copying the board

  This class is the **visual + interactive core** of your game — without it, there would be no GUI response to the user’s clicks.

- `Time.java`: This class manages the **move timer** for each player.

  **Key Responsibilities:**
  - Uses `javax.swing.Timer` to update a clock every second
  - Displays time in `mm:ss` format on the GUI
  - Triggers a turn switch when time runs out
  - Resets time automatically at the start of each move

  **Important Methods:**
  - `start()` – Starts the countdown
  - `reset()` – Resets to the initial time (set by the slider)
  - `CountdownTimerListener` – Inner class that runs every second

  This class adds **real pressure and realism** to the game, turning it from casual play to competitive chess.

- `Player.java`: This class tracks **player statistics** and handles reading/writing player data.

  **Key Responsibilities:**
  - Stores name, games played, and games won
  - Calculates win percentage
  - Saves and loads player stats from `chessgamedata.dat` using Java Serialization
  - Updates existing players or creates new ones
  - Provides data for the UI (dropdowns, stat panels)

  **Important Methods:**
  - `fetch_players()` – Loads all saved players from file
  - `Update_Player()` – Updates the player’s record (or creates one)
  - `updateGamesPlayed()` / `updateGamesWon()` – Increments stats

  It provides long-term persistence, so your chess app feels like a **real application with user profiles**. The main controller class that handles the GUI, event listeners, board initialization, move validation, turn switching, game end, and player interactions. It manages the full gameplay lifecycle.
- `Cell.java`: Represents each square of the chessboard (64 in total). Holds a piece, visual state (highlight, check, selection), and reacts to user interaction. It connects GUI actions to game logic.
- `Time.java`: Manages the countdown timer using Swing’s `Timer`. Updates the display every second, enforces timeouts, and switches turns when time runs out.
- `Player.java`: Manages player information like name, games played/won. Handles serialization to store/retrieve stats from `chessgamedata.dat`. Also used to populate player stats in the UI. The game entry point.
- `Cell.java`: Represents individual squares.
- `Time.java`: Controls timers for each player.
- `Player.java`: Stores player info.

### 🔹 Pieces

- `Piece.java`: Abstract class
- `Pawn.java`, `Rook.java`, `Queen.java`, etc.
  - Each piece knows how it moves!

### 🔹 GUI

- Rendered using `JFrame` and `JPanel`
- Event listeners for clicking, selection, and movement

---

## 🔄 Comparison with Other Games

To highlight the uniqueness and learning scope of ChessOOP, here’s a comparison with another popular Java-based game project: **Tetris**.

🎯 **Why ChessOOP is Harder to Build:**

- Requires implementation of complex piece-specific movement logic (e.g., check, checkmate).
- Demands strict rule validation and turn management.
- Game state tracking is more advanced (e.g., win condition, move legality).
- Involves more object-oriented planning and abstraction (inheritance, polymorphism).

---

---






---

## 📄 Project Documentation

- 📁 `Project Documentation.docx` – Overview of design, problems solved, learning outcomes
- 📁 `Software Requirement Specification.docx` – Functional + non-functional needs
- 📁 `Class Diagram/` – Includes complete UML for explanation
- 📁 `Screenshots/` – Present-worthy visuals

---

## 👨‍💻 Developers

| Name          | Role               |
| ------------- | ------------------ |
| Ashish Kedia  | Developer & Leader |
| Adarsh Mohata | Co-Developer       |

---

## 🎓 Viva Questions & Answers

### ❓ What is the main objective of this project?

**Answer**: To develop a fully functional two-player chess game using Java that demonstrates strong object-oriented programming principles like inheritance, encapsulation, and polymorphism along with GUI handling via Java Swing.

### ❓ Why did you choose Chess over other games?

**Answer**: Chess provides a challenging structure involving unique movement logic for each piece, real-time rule enforcement, and complex state management (like check/checkmate), which makes it ideal for showcasing OOP design and implementation.

### ❓ What OOP concepts have you used in this project?

**Answer**:

- **Inheritance**: All pieces inherit from a base `Piece` class.
- **Polymorphism**: Different pieces override movement logic.
- **Encapsulation**: Each class handles its internal data privately.
- **Abstraction**: Piece logic is abstracted and reused through design.

### ❓ How is move validation implemented?

**Answer**: Each piece class (like `Pawn.java`, `Rook.java`) has its own `isValidMove()` method that checks whether a selected move follows chess rules. The game also prevents invalid moves using event-driven checks.

### ❓ What challenges did you face?

**Answer**: Implementing advanced features like move validation, managing state (e.g., turns, checkmate), and ensuring piece behaviors matched the rules of chess. GUI syncing and debugging were also significant challenges.

### ❓ What can be improved in the future?

**Answer**: Adding AI for single-player mode, multiplayer network support, saving/loading games, better GUI themes, and support for rule extensions like en passant and pawn promotion.

### ❓ How is this project better than simpler games like Tetris or Snake?

**Answer**: ChessOOP requires deeper planning in object design, logic handling, and interaction. Unlike Tetris, where you mainly manage falling pieces, Chess needs enforcement of turn-based logic, piece rules, and complex win conditions—all of which involve much more sophisticated code architecture.

---

## 📜 License

Licensed under the [MIT License](LICENSE).

---

