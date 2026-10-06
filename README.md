# Kidney Edge Detection

This project compares several edge detection methods for kidney images from ultrasound and CT scans.

For each image, two preprocessing filters were applied:

- Median filter
- Gaussian filter

Then four edge detection operators were tested:

- Sobel
- Scharr
- Prewitt
- Canny

This gives 8 processing combinations for each image.

OpenCV functions `cv.medianBlur()` and `cv.GaussianBlur()` were used for the final preprocessing. Custom implementations of these filters were also created for demonstration.

## Results

Overall, none of the tested combinations produced a perfectly clear kidney contour, especially on the ultrasound images.

Sobel, Scharr, and Prewitt produced very similar results. Among these methods, the combination of the **Gaussian filter (5×5, σ = 1.4) and the Scharr operator** showed slightly clearer kidney boundaries in the visual comparison.

Canny produced thinner but more fragmented edges and often highlighted unrelated structures.


