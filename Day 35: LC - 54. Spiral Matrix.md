Given an m x n matrix, return all elements of the matrix in spiral order.

 

Example 1:


Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]
Example 2:


Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
 

Constraints:

m == matrix.length
n == matrix[i].length
1 <= m, n <= 10
-100 <= matrix[i][j] <= 100


```cpp
class Solution{
  public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
    vector<int> result; // Initialize an empty vector to store the elements of the matrix in spiral order.
    if (matrix.empty()) { // Check if the matrix is empty, in which case we simply return the empty result vector.
        return result;
    }
    int m = matrix.size(); // Get the number of rows in the matrix.
    int n = matrix[0].size(); // Get the number of columns in the matrix.
    int rowBegin = 0; // Initialize the starting row index.
    int rowEnd = m - 1; // Initialize the ending row index.
    int colBegin = 0; // Initialize the starting column index.
    int colEnd = n - 1; // Initialize the ending column index.
    while (rowBegin <= rowEnd && colBegin <= colEnd) { // Traverse the matrix in a clockwise spiral order while the submatrix we're traversing is non-empty.
        for (int i = colBegin; i <= colEnd; i++) { // Traverse the top row from left to right.
            result.push_back(matrix[rowBegin][i]); // Add each element in the top row to the result vector.
        }
        rowBegin++; // Increment the starting row index since we've finished traversing the top row.
        for (int i = rowBegin; i <= rowEnd; i++) { // Traverse the right column from top to bottom.
            result.push_back(matrix[i][colEnd]); // Add each element in the right column to the result vector.
        }
        colEnd--; // Decrement the ending column index since we've finished traversing the right column.
        if (rowBegin <= rowEnd) { // Check if there are still rows left to traverse.
            for (int i = colEnd; i >= colBegin; i--) { // Traverse the bottom row from right to left.
                result.push_back(matrix[rowEnd][i]); // Add each element in the bottom row to the result vector.
            }
        }
        rowEnd--; // Decrement the ending row index since we've finished traversing the bottom row.
        if (colBegin <= colEnd) { // Check if there are still columns left to traverse.
            for (int i = rowEnd; i >= rowBegin; i--) { // Traverse the left column from bottom to top.
                result.push_back(matrix[i][colBegin]); // Add each element in the left column to the result vector.
            }
        }
        colBegin++; // Increment the starting column index since we've finished traversing the left column.
    }
    return result; // Return the vector containing the matrix elements in spiral order.
  }
};
