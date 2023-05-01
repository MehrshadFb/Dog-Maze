package PE1;

import java.util.ArrayList;
import java.util.List;

/**
 * This class is Maze solver and it includes several algorithms to find right
 * path from entrance gate to exit gate in a maze.
 * 
 * @author Mehrshad Farahbakhsh.
 * @version 1.0
 */
public class PE1 {
	Maze dogMaze;

	/**
	 * This method sets up the maze using the given input argument
	 * 
	 * @param maze is a maze that is used to construct the dogMaze
	 */
	public void setup(String[][] maze) {
		/*
		 * insert your code here to create the dogMaze using the input argument.
		 */
		this.dogMaze = new Maze(maze);
	}

	/**
	 * This method returns true if the number of gates in dogMaze >= 2.
	 * 
	 * @return it returns true, if enough gate exists (at least 2), otherwise false.
	 */
	public boolean enoughGate() {
		// insert your code here. Change the return value to fit your purpose. \
		int sumCount = 0;
		sumCount = topSide(0, 0) + leftSide(0, 0) + bottomSide(0, 0) + rightSide(0, 0);
		if (sumCount >= 2) {
			return true;
		} else {
			return false;
		}
	}

	/**
	 * This method counts the number of gates that they are open from the top in the
	 * first row
	 * 
	 * @param column is the index of column in the maze
	 * @param count  is the number of gates that they are open from the top
	 * @return it returns an integer that is the number of gates that they are open
	 *         from the top in the first row
	 */
	public int topSide(int column, int count) {
		if (column == this.dogMaze.getMaze()[0].length) {
			return count;
		} else if (this.dogMaze.getMaze()[0][column].charAt(0) == '0') {
			return topSide(column + 1, count + 1);
		} else {
			return topSide(column + 1, count);
		}
	}

	/**
	 * This method counts the number of gates that they are open from the bottom in
	 * the last row
	 * 
	 * @param column is the index of column in the maze
	 * @param count  is the number of gates that they are open from the bottom
	 * @return it returns an integer that is the number of gates that they are open
	 *         from the bottom in the last row
	 */
	public int bottomSide(int column, int count) {
		if (column == this.dogMaze.getMaze()[0].length) {
			return count;
		} else if (this.dogMaze.getMaze()[this.dogMaze.getMaze().length - 1][column].charAt(2) == '0') {
			return bottomSide(column + 1, count + 1);
		} else {
			return bottomSide(column + 1, count);
		}
	}

	/**
	 * This method counts the number of gates that they are open from the left in
	 * the first column
	 * 
	 * @param row   is the index of row in the maze
	 * @param count is the number of gates that they are open from the left
	 * @return it returns an integer that is the number of gates that they are open
	 *         from the left in the first column
	 */
	public int leftSide(int row, int count) {
		if (row == this.dogMaze.getMaze().length) {
			return count;
		} else if (this.dogMaze.getMaze()[row][0].charAt(1) == '0') {
			return leftSide(row + 1, count + 1);
		} else {
			return leftSide(row + 1, count);
		}
	}

	/**
	 * This method counts the number of gates that they are open from the right in
	 * the last column
	 * 
	 * @param row   is the index of row in the maze
	 * @param count is the number of gates that they are open from the right
	 * @return it returns an integer that is the number of gates that they are open
	 *         from the right in the last row
	 */
	public int rightSide(int row, int count) {
		if (row == this.dogMaze.getMaze().length) {
			return count;
		} else if (this.dogMaze.getMaze()[row][this.dogMaze.getMaze()[0].length - 1].charAt(3) == '0') {
			return rightSide(row + 1, count + 1);
		} else {
			return rightSide(row + 1, count);
		}
	}

	/**
	 * This method finds a path from the entrance gate to the exit gate.
	 * 
	 * @param row    is the index of the row, where the entrance is.
	 * @param column is the index of the column, where the entrance is.
	 * @return it returns a string that contains the path from the start to the end.
	 *         The return value should have a pattern like this (i,j)(k,l),... The
	 *         first pair of the output must show the entrance given as the input
	 *         parameter (i.e. (row,column) No whitespace is allowed in the output.
	 */
	public String findPath(int row, int column) {
		// insert your code here. Change the return value to fit your purpose.

		// this arraylist is used to store the correct gates
		ArrayList<String> pathList = new ArrayList<String>();
		String entrance = "(" + row + "," + column + ")";
		this.searchRoute(row, column, pathList, entrance);
		String path = String.join("", pathList);
		return path;

	}

	/**
	 * This method searches the path and check the open sides of the gate and find
	 * the correct gates which are heading to the exit gate
	 * 
	 * @param row is the index of the row, where the current gate is.
	 * @param column is the index of the column, where the current gate is.
	 * @param pathList is the list to store row and column of the correct gates that they
	 *                 are heading to exit gate (row,column)
	 * @param position is string of (row,column)
	 * @return it returns boolean, if it gets the right path and it is open, it returns true and if
	 *         it gets the wrong path and it is stock it returns false
	 */
	public Boolean searchRoute(int row, int column, ArrayList<String> pathList, String position) {
		// add the position to visited list
		pathList.add("(" + row + "," + column + ")");
		String gate = this.dogMaze.getMaze()[row][column];
		// Check the gate can go up
		if (gate.charAt(0) == '0') {
			String nextPosition = "(" + (row - 1) + "," + column + ")";
			// Check the next gate is not out of the maze
			if (row - 1 < 0) {
				// Check current gate reaches exit gate
				if (!position.equals("(" + row + "," + column + ")")) {
					return true;
				}
				// Check the next gate is not visited
			} else if (!pathList.contains(nextPosition)) {
				// recursive - call the next gate
				if (this.searchRoute(row - 1, column, pathList, position)) {
					return true;
				}
			}
		}
		// Check the gate can go down
		if (gate.charAt(2) == '0') {
			String nextPosition = "(" + (row + 1) + "," + column + ")";
			// Check the next gate is not out of the maze
			if (row + 1 > this.dogMaze.getMaze().length - 1) {
				// Check current gate reaches exit gate
				if (!position.equals("(" + row + "," + column + ")")) {
					return true;
				}
				// Check the next gate is not visited
			} else if (!pathList.contains(nextPosition)) {
				// recursive - call the next gate
				if (this.searchRoute(row + 1, column, pathList, position)) {
					return true;
				}
			}
		}
		// Check the gate can go left
		if (gate.charAt(1) == '0') {
			String nextPosition = "(" + row + "," + (column - 1) + ")";
			// Check the next gate is not out of the maze
			if (column - 1 < 0) {
				// Check current gate reaches exit gate
				if (!position.equals("(" + row + "," + column + ")")) {
					return true;
				}
				// Check the next gate is not in visited
			} else if (!pathList.contains(nextPosition)) {
				// recursive - call the next gate
				if (this.searchRoute(row, column - 1, pathList, position)) {
					return true;
				}
			}
		}
		// Check the gate can go right
		if (gate.charAt(3) == '0') {
			String nextPosition = "(" + row + "," + (column + 1) + ")";
			// Check the next gate is not out of the maze
			if (column + 1 > this.dogMaze.getMaze()[0].length - 1) {
				// Check current gate reaches exit gate
				if (!position.equals("(" + row + "," + column + ")")) {
					return true;
				}
				// Check the next gate is not visited
			} else if (!pathList.contains(nextPosition)) {
				// recursive - call the next gate
				if (this.searchRoute(row, column + 1, pathList, position)) {
					return true;
				}
			}
		}
		// Otherwise remove the current position
		pathList.remove(pathList.size() - 1);
		return false;

	}

}

/**
 * This class defines a <code> maze </code> using a 2D array. To complete the
 * code, you should not change the method signatures (header).
 *
 */

class Maze {
	private String[][] maze;

	/**
	 * This constructor makes the maze.
	 * 
	 * @param maze is a 2D array that contains information on how each cell of the
	 *             array looks like.
	 */
	public Maze(String[][] maze) {
		/*
		 * complete the constructor so that the maze is a deep copy of the input
		 * parameter.
		 */
		this.maze = new String[maze.length][];
		for (int i = 0; i < maze.length; i++) {
			this.maze[i] = new String[maze[i].length];
			for (int j = 0; j < maze[i].length; j++) {
				this.maze[i][j] = maze[i][j];
			}
		}
	}

	/**
	 * This accessor (getter) method returns a 2D array that represents the maze
	 * 
	 * @return it returns a reference to the maze
	 */
	public String[][] getMaze() {
		/*
		 * complete this method providing that a clone of the maze should be returned.
		 * you may want to change the return value to fit your purpose.
		 */

		// i used nested loops to get elements form the maze because maze is 2D and to
		// get the elements in 2D array we need 2 for loops which first one is for row
		// and the second for loop is for column
		// also to create a clone of the maze we need to reserve a new space in memory

		String[][] mazeCopy = new String[this.maze.length][];
		for (int i = 0; i < this.maze.length; i++) {
			mazeCopy[i] = new String[this.maze[i].length];
			for (int j = 0; j < this.maze[i].length; j++) {
				mazeCopy[i][j] = this.maze[i][j];
			}
		}
		return mazeCopy;
	}

	/**
	 * This method is for representation of an object
	 * 
	 * @return it returns a string which represents of the maze
	 */
	@Override
	public String toString() {
		// insert your code here. Change the return value to fit your purpose.

		// i used nested loops for getting the gates of the maze because the maze is 2D
		// array and to get an element in 2D array we should use nested loops that the
		// first loop is for row and the second loop is for column
		// then it gets each element of the maze and put it in the string

		String result = "[";
		for (int i = 0; i < this.maze.length; i++) {
			for (int j = 0; j < this.maze[i].length; j++) {
				result = result + this.maze[i][j] + " ";
			}
			result = result.substring(0, result.length() - 1) + "] \n" + "[";
		}
		return result.substring(0, result.length() - 2);
	}

}// end of class Maze
