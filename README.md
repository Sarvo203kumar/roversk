public class Rover {
    private int x, y;
    private Direction direction;
    private Grid grid;

    public Rover(int x, int y, Direction direction, Grid grid) {
        this.x = x;
        this.y = y;
        this.direction = direction;
        this.grid = grid;
    }

    public void move() {
        int newX = x, newY = y;
        switch (direction) {
            case N: newY++; break;
            case E: newX++; break;
            case S: newY--; break;
            case W: newX--; break;
        }
        if (newX >= 0 && newX < grid.getWidth() && newY >= 0 && newY < grid.getHeight() && !grid.hasObstacle(newX, newY)) {
            x = newX;
            y = newY;
        } else {
            System.out.println("Obstacle detected or out of bounds. Can't move.");
        }
    }

    public void turnLeft() {
        direction = direction.left();
    }

    public void turnRight() {
        direction = direction.right();
    }

    public String getStatus() {
        String obstacleStatus = grid.hasObstacle(x, y) ? "Obstacle detected." : "No Obstacles detected.";
        return "Rover is at (" + x + ", " + y + ") facing " + direction + ". " + obstacleStatus;
    }
}
