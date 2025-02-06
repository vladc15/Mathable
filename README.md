# Mathable

## Overview
This project focuses on analyzing Mathable games by extracting information from images provided after each move. The project is divided into three main tasks:

1. Finding the position where the piece was placed.

2. Identifying the placed piece.

3. Calculating the score for each player.

The first two tasks involve Computer Vision techniques, while the third task relies on the information obtained from the previous tasks.

## Project Structure
The project is structured into several steps to achieve the objectives:

1. Extracting the Large Board: Removing the table from the images to isolate the game board.

2. Extracting the Small Board: Removing the border of the large board to focus on the playable area.

3. Dividing the Small Board into a 14x14 Grid: Creating a grid to identify the squares where pieces are placed.

4. Finding the Position of the Added Piece: Comparing consecutive images to detect the position of the newly placed piece.

5. Identifying the Added Piece: Using template matching to determine which piece was placed.

6. Calculating the Score: Retaining the score for each move and calculating the total score for each player.

## Detailed Steps

### 1. Extracting the Large Board

Approach:

- Use HSV representation to generate a mask and highlight the large board.

- Apply sharpening, thresholding, and erosion to remove noise.

- Use Canny Edge Detection and findContours to detect the board's contour.

- Extract the large board using perspective transformation.

### 2. Extracting the Small Board

Approach:

- Use OpenCV functions to accurately extract the small board, avoiding manual cropping errors.

### 3. Dividing the Small Board into a 14x14 Grid

Approach:

- Manually delimit the grid lines at a fixed distance of 104 pixels.

### 4. Finding the Position of the Added Piece

Approach:

- Compare consecutive images to find the difference.

- Transform images to grayscale, apply thresholding, and calculate the absolute difference.

- Identify the patch with the maximum difference, which corresponds to the new piece's position.

### 5. Identifying the Added Piece

Approach:

- Obtain templates for each piece from the templates folder.

- Transform the patch and templates to grayscale and apply thresholding.

- Use OpenCV's matchTemplate function to find the best match.

### 6. Calculating the Score

Approach:

- Retain the score for each move in a matrix.

- Check equations according to the game rules, considering bonuses and conditions.

- Sum the scores for each player's moves and write the results to the score files.


## Results
The project outputs the following:

- Position of the Added Piece: The coordinates of the newly placed piece on the grid.

- Identified Piece: The number of the piece that was placed.

- Player Scores: The total score for each player after each round.

On the test data, this approach achieved an accuracy of 98% in correctly solving the three tasks.

## Conclusion
This project successfully analyzes Mathable games by extracting and processing information from images. It accurately identifies the position and type of the placed pieces and calculates the scores for each player. The use of Computer Vision techniques and template matching ensures precise results, making it a robust solution for the given tasks.