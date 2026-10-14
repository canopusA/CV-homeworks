# Circle Detection Using Hough Transform

## Overview
This project focuses on detecting and counting circles in images using the Hough Circle Transform implemented in OpenCV.

The dataset contains images of logs and pipes with different sizes and backgrounds.

## Method
1. Load images in grayscale.
2. Apply noise reduction using Gaussian or bilateral filtering.
3. Detect circles using `cv.HoughCircles()`.
4. Tune detection parameters for each image.
5. Remove duplicate detections and count circles.
6. Visualize the results.

## Conclusion

In this project, the Hough Circle Transform was used to detect and count circular objects in seven images. Different parameters and preprocessing techniques were applied to improve detection accuracy.

**Successful results:**
- **logs-1 and logs-2:** Most log ends were detected successfully, although some false detections and missed logs remained.
- **pipes-4:** The algorithm performed well, detecting most circular pipe openings with relatively few errors.
- **pipes-5:** Both small and large pipes were detected. However, some pipes were counted more than once because of their inner and outer edges.

**Less successful results:**
- **logs-3:** Detection was more difficult because the logs appeared very small in the image. Some circles were missed or detected inside the logs instead of along their boundaries.
- **logs-4:** This was one of the most challenging images. Irregular log shapes, overlapping objects, and a complex background caused many missed and false detections.
- **pipes-6:** Many pipes were detected, but some small openings were missed, while several large circles were incorrectly positioned or overlapped.

**Overall**, the Hough Circle Transform worked best on images with clear, well-defined circular boundaries. Individual parameter tuning, noise reduction, regions of interest (ROI), and duplicate filtering improved the results, but did not completely eliminate errors.

The experiments demonstrated that detection accuracy strongly depends on object size, shape, image quality, and background complexity.
