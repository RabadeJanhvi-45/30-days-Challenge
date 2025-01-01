# Image Smoother

## Problem Description
An **Image Smoother** applies a 3x3 filter to each cell of an `m x n` integer matrix representing the grayscale of an image. The filter computes the average of the cell and its surrounding cells, rounding down to the nearest integer. If any surrounding cells are missing (on the edges or corners of the matrix), only the existing cells are considered in the average.

### Input and Output Examples
#### Example 1:
**Input:**  
`img = [[1,1,1], [1,0,1], [1,1,1]]`  
**Output:**  
`[[0,0,0], [0,0,0], [0,0,0]]`

**Explanation:**  
- For corner points like (0,0): Average = `floor((1+1+1+0)/4) = floor(0.75) = 0`
- For edge points like (0,1): Average = `floor((1+1+1+0+1)/6) = floor(0.833) = 0`
- For center point (1,1): Average = `floor((1+1+1+1+1+1+0+1+1)/9) = floor(0.888) = 0`

#### Example 2:
**Input:**  
`img = [[100,200,100], [200,50,200], [100,200,100]]`  
**Output:**  
`[[137,141,137], [141,138,141], [137,141,137]]`

**Explanation:**  
- For corner points like (0,0): Average = `floor((100+200+200+50)/4) = floor(137.5) = 137`
- For edge points like (0,1): Average = `floor((100+200+50+200+200+100)/6) = floor(141.667) = 141`
- For center point (1,1): Average = `floor((50+200+200+200+200+100+100+100+100)/9) = floor(138.889) = 138`

---

## Approach
1. Define a list of directions representing the 8 surrounding cells and the current cell.
2. Traverse the matrix cell by cell.
3. For each cell:
   - Sum the values of valid surrounding cells.
   - Count the number of valid cells considered.
4. Compute the average by dividing the sum by the count and store it in the result matrix.
5. Return the resulting smoothed image.

### Complexity
- **Time Complexity:** `O(m * n * 9)` (Iterating over the matrix and its neighbors)
- **Space Complexity:** `O(m * n)` (Resultant matrix)
