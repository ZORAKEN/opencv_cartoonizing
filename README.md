# opencv_cartoonizing using webcam

Convert the image to grayscale for edge detection,applied median blur to remove noise.
Uses adaptive thresholding to detect edges.
Apply a bilateral filter to smooth the image while preserving edges.
Combine the smoothed image with edges to produce the cartoon effect.

 Live webcam processing
- Cartoon-style edge + color smoothing
- Lightweight OpenCV pipeline
