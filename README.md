# 🟡 Pac-Man: A Java-Based Game Engine

This project is a complete, self-contained implementation of the classic *Pac-Man* game, built entirely in *Java* using *Swing* and *AWT*.  
It serves as a simple but powerful introduction to game development principles such as:

- Event-driven programming
- Fixed-timestep game loops
- Collision detection
- Object-oriented design

The goal of this project is to provide a fully functional Pac-Man clone while keeping the architecture clean, readable, and extensible — perfect for students, hobbyists, and anyone learning Java game programming.

---

## ⚙ Architecture Overview

The project follows a clear *separation of concerns* for maintainability and scalability:

- *Game Model*  
  Stores the state of the game — Pac-Man’s position, ghost positions, scores, and remaining pellets.

- *Game Logic*  
  Handled inside the PacMan class. It determines how characters move, checks for collisions, updates the score, and handles game-over events.

- *Rendering*  
  Implemented in the paintComponent() method. This draws the maze, Pac-Man, ghosts, pellets, and score on every frame.

- *Input Handling*  
  Managed using the KeyListener interface. Keyboard inputs (arrow keys or WASD) are mapped to velocity changes that update Pac-Man’s direction.

This approach cleanly separates *what the game is* (model) from *how it looks* (view) and *how it behaves* (controller).

---

## 💻 Technical Implementation Details

### 1. *Game Window (App.java)*  
The App.java file is the entry point of the program. It:
- Defines the *board size* using rowCount, columnCount, and tileSize.
- Creates a JFrame window titled "Pac Man".
- Adds the PacMan panel to the frame and displays it.

### 2. *Block Class: Core Game Entity*  
The Block class represents *all objects in the game* (walls, pellets, Pac-Man, ghosts) with:
- *Position and Dimensions*: x, y, width, height
- *Velocity*: velocityX, velocityY
- *Image (Optional)*: For walls, ghosts, Pac-Man sprites  
- *Behavior*: updateVelocity() maps movement directions to velocity vectors.

This *data-driven polymorphism* eliminates the need for separate classes for each entity type.

### 3. *Game Loop*  
Implemented using javax.swing.Timer:
- Fires every *50ms* (20 frames per second).
- Calls move() to update game state.
- Calls repaint() to redraw the screen.
  
This fixed timestep ensures *consistent gameplay speed* on different machines.

### 4. *Collision Detection*  
Uses *AABB (Axis-Aligned Bounding Box)* collision:
```java
if (a.x < b.x + b.width && 
    a.x + a.width > b.x && 
    a.y < b.y + b.height && 
    a.y + a.height > b.y) {
    // Collision detected
}
