# Add-ons For the Gomoku game

- Move history like in chess.
- Undo and redo moves using a moveHistory stack and a redoHistory stack.
- 19x19 Game mode, 15x15 Game mode, normal and overline mode (6 or more in a row are also accounted for).
  - Consequently, change the ranking system and the game logic accordingly.
- Add a timer for each player??.

```java 
  public void makeMove(int x, int y, Player player) {
    board[x][y] = player; // Assuming board is your 2D array
    moveHistory.push(new Move(x, y, player));
}
```

```java 
public void undoMove() {
    if (!moveHistory.isEmpty()) {
        Move lastMove = moveHistory.pop();
        board[lastMove.x][lastMove.y] = null; // Or whatever represents an empty cell
    }
}
```

```kotlin
fun checkWinCondition(board: Map<Position, Color>, lastMove: Position, color: Color): Boolean {
    val directions = listOf(
        Pair(1, 0),    // Horizontal
        Pair(0, 1),    // Vertical
        Pair(1, 1),    // Diagonal from top-left to bottom-right
        Pair(1, -1)    // Diagonal from bottom-left to top-right
    )

    for (direction in directions) {
        var count = 1  // Include the last move
        // Check one direction
        count += countConsecutive(board, lastMove, color, direction.first, direction.second)
        // Check the opposite direction
        count += countConsecutive(board, lastMove, color, -direction.first, -direction.second)

        if (count >= 5) return true
    }
    return false
}

//CAN ALSO BE USED TO CHECK FOR OVERLINE MODE
fun countConsecutive(board: Map<Position, Color>, start: Position, color: Color, dx: Int, dy: Int): Int {
    var count = 0
    var x = start.x + dx
    var y = start.y + dy

    while (board[Position(x, y)] == color) {
        count++
        x += dx
        y += dy
    }
    return count
}
```