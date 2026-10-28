# Image Stitching

## Description
In this homework, I used OpenCV to stitch multiple photos together into panoramas.

The task was to create three panoramas from the `building1`, `building2`, and `building3` image sets.

## Approach
I used ORB to find keypoints, BFMatcher to match them, and RANSAC to calculate the homography. Then I aligned the images and blended them to make the transitions smoother.

## Results
Three panoramas were created and saved in the `panorama_results` folder.