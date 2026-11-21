# EDGE LINKING USING HOUGH TRANSFORM

## AIM:

To write a Python program to detect lines in an image using the Hough Transform.

## SOFTWARE REQUIRED:

- Anaconda – Python 3.7
- OpenCV
- NumPy
- Matplotlib

## ALGORITHM:

**Step 1:** Import all the necessary modules required for the program.

**Step 2:** Load an image using the `imread()` function from the OpenCV (`cv2`) module.

**Step 3:** Convert the input image into a grayscale image using `cvtColor()` or `cv2.IMREAD_GRAYSCALE`.

**Step 4:** Apply Gaussian Blur to reduce noise in the image.

**Step 5:** Use the Canny edge detector to identify the edges in the image.

**Step 6:** Apply the `HoughLinesP()` function to detect straight lines and obtain their coordinates.

**Step 7:** Use a for loop to draw the detected lines on the original image.

**Step 8:** Display the original image, grayscale image, Canny edge output, and final Hough Transform result using Matplotlib.

## PROGRAM:

```
# Developed by: Lorena Avelyn R
# Reg No: 212224040174


import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('Ip2.jpg')  # Replace 'image.jpg' with your image path

# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')

plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150

# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')

# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)

# Step 6: Using a for loop, draw the lines on the original image using the detected coordinates
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line  # Unpack directly from 'line'
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)


# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')




```

## OUTPUT:

**1. Input Image and Grayscale Image:** 


<img width="582" height="480" alt="Screenshot 2026-11-21 160612" src="https://github.com/user-attachments/assets/ef9e14e0-00e9-48b8-96d6-848e32a0a4a9" />


<img width="627" height="460" alt="Screenshot 2026-11-21 160735" src="https://github.com/user-attachments/assets/f09d8fdd-f351-48a7-a9ce-0456f758ea7c" />

**2. Canny Edge Detector Output:** Displays the edges identified in the image using the Canny edge detection technique.


<img width="740" height="470" alt="Screenshot 2026-11-21 160809" src="https://github.com/user-attachments/assets/6c9f27b8-1e00-4c25-8963-637c035fb166" />



**3. Hough Transform Output:** Displays the detected straight lines drawn on the original image.



<img width="672" height="490" alt="Screenshot 2026-11-21 160913" src="https://github.com/user-attachments/assets/8df1ab6e-7627-4350-b414-11bee6f9cf5e" />



## RESULT:
Thus, the straight lines in the given image were successfully detected using the Hough Transform technique.the given image were successfully detected using the Hough Transform technique.
