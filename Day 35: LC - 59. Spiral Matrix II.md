Given a positive integer n, generate an n x n matrix filled with elements from 1 to n2 in spiral order.

 

Example 1:


Input: n = 3
Output: [[1,2,3],[8,9,4],[7,6,5]]
Example 2:

Input: n = 1
Output: [[1]]
 

Constraints:

1 <= n <= 20

```cpp
class Solution{
  public:
    vector<vector<int>> generateMatrix(int n) {
    vector<vector<int>> matrix(n, vector<int>(n)); // Create an n x n matrix filled with zeros.
    int num = 1; // Initialize the starting number.
    int rowBegin = 0; // Initialize the starting row index.
    int rowEnd = n - 1; // Initialize the ending row index.
    int colBegin = 0; // Initialize the starting column index.
    int colEnd = n - 1; // Initialize the ending column index.
    while (rowBegin <= rowEnd && colBegin <= colEnd) { // Traverse the matrix in a clockwise spiral order while the submatrix we're traversing is non-empty.
        for (int i = colBegin; i <= colEnd; i++) { // Traverse the top row from left to right.
            matrix[rowBegin][i] = num++; // Assign the current number to the current element in the matrix, and then increment the number.
        }
        rowBegin++; // Increment the starting row index since we've finished traversing the top row.
        for (int i = rowBegin; i <= rowEnd; i++) { // Traverse the right column from top to bottom.
            matrix[i][colEnd] = num++; // Assign the current number to the current element in the matrix, and then increment the number.
        }
        colEnd--; // Decrement the ending column index since we've finished traversing the right column.
        if (rowBegin <= rowEnd) { // Check if there are still rows left to traverse.
            for (int i = colEnd; i >= colBegin; i--) { // Traverse the bottom row from right to left.
                matrix[rowEnd][i] = num++; // Assign the current number to the current element in the matrix, and then increment the number.
            }
        }
        rowEnd--; // Decrement the ending row index since we've finished traversing the bottom row.
        if (colBegin <= colEnd) { // Check if there are still columns left to traverse.
            for (int i = rowEnd; i >= rowBegin; i--) { // Traverse the left column from bottom to top.
                matrix[i][colBegin] = num++; // Assign the current number to the current element in the matrix, and then increment the number.
            }
        }
        colBegin++; // Increment the starting column index since we've finished traversing the left column.
    }
    return matrix; // Return the generated matrix.
  }
};
