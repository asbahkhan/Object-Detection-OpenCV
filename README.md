
# Object Detection and Surface Area Calculation

## Overview

The goal of this script is to perform the following tasks on an image:

1. Object Detection: Identify and isolate the object present in the image. Currently supports rectangular and circular objects.
2. Surface Area Calculation: Calculate the surface area of the detected object based on its shape: \
     a. For a rectangular object: Area = width * height \
     b. For a circular object: Area = pi * radius * radius 



## Approach Explanation

1. Loading the image: We use cv2.imread() to load the image specified by image_path. If the image cannot be loaded, an error message is displayed.

2. Preprocessing: \
   a.Grayscale Conversion: Convert the loaded image to grayscale using cv2.cvtColor(). \
   b.Noise Reduction: Apply Gaussian blur (cv2.GaussianBlur()) to the grayscale image to reduce noise and prepare it for edge detection. \
   c.Edge Detection: Use Canny edge detection (cv2.Canny()) to detect edges in the blurred grayscale image. This helps in identifying potential contours of objects. \

3. Contour Detection: \
   Finding Contours: Use cv2.findContours() to detect contours in the edge-detected image. The cv2.RETR_EXTERNAL retrieval mode retrieves only the external contours, which are typically the outlines of objects in the image.

4. Object Detection: \
   a.Approximating Contours: Approximate each contour to a polygon using cv2.approxPolyDP() to simplify its shape. \
   b.Identifying Rectangles: Check if the approximated contour has four vertices (len(approx) == 4). If true, it is likely a rectangle. \
   c.Bounding Box: Use cv2.minAreaRect() to find the rotated bounding box of the contour, which provides the rectangle's dimensions and orientation. \
   d.Calculating Surface Area: Calculate the surface area of the rectangle using the dimensions obtained from the bounding box (width * height). 

5. Visualizing and Output: \
   a.Drawing and Labeling: Draw the detected rectangle on the original image using cv2.drawContours() and label it with its calculated surface area using cv2.putText(). \
   b.Displaying the Image: Convert the annotated image from BGR to RGB format (cv2.cvtColor()) and display it using matplotlib.pyplot.


    
