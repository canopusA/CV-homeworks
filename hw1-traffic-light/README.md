# Traffic Light Color Classification

## Description

The goal of this project is to classify traffic light images into three classes:

- Red
- Yellow
- Green

The solution is based on basic image processing techniques introduced in the first laboratory work.

The program processes all images from the input folder, determines the active traffic light color and saves the filenames into three output files:

- `red.txt`
- `yellow.txt`
- `green.txt`

Each file contains the names of images classified into the corresponding class.


## Approach

The classification is based on the HSV color space.

OpenCV reads images in BGR format, so each image is converted to HSV for color analysis and to RGB for visualization.

The HSV representation is convenient because it separates:

- **Hue (H)** — color;
- **Saturation (S)** — color intensity;
- **Value (V)** — brightness.

For every image, three binary masks are created for red, yellow and green colors using selected HSV ranges.

The following ranges are used:

### Red

- H: 0–15 or 170–179
- S > 90
- V > 120

### Yellow

- H: 15–35
- S > 90
- V > 120

### Green

- H: 35–90
- S > 80
- V > 100

The HSV thresholds were selected experimentally based on the provided set of images.


## Signal Position

Color information alone is not always sufficient because the background or the traffic light housing may contain similar colors.

Therefore, the approximate position of the active signal is also taken into account.

For a standard vertical traffic light:

- red is expected in the upper part;
- yellow is expected in the middle part;
- green is expected in the lower part.

For each color, only the corresponding area of the image is analyzed.

The concentration of matching pixels is calculated for every class, and the class with the highest score is selected as the prediction.


## Visualization

For checking the results, the notebook can display three images:

1. **Original** — the original image;
2. **Selected mask** — the binary mask of the predicted color;
3. **Detected** — the pixels selected by the mask.

The visualization is used to analyze the behavior of the classifier and identify difficult cases.


## Output

After processing all images, the program creates three text files:

```text
red.txt
yellow.txt
green.txt
```

Each file contains the filenames assigned to the corresponding class.


## Limitations

The classifier is based on fixed HSV ranges and approximate signal positions, so some difficult images may be classified incorrectly.

The main sources of errors are:

- changes in lighting conditions;
- differences in camera color reproduction;
- orange, yellow or red traffic light housings;
- background objects with similar colors;
- unusual viewing angles.

For example, a large orange traffic light housing can produce many red or yellow pixels even when the active signal is green.

A yellow signal can also appear more orange or reddish under certain lighting conditions and therefore partially fall into the red HSV range.

These cases demonstrate the limitations of color classification based only on fixed HSV thresholds and approximate signal position.

The result could be improved further by more accurately locating the traffic light signal before performing color classification.



## Conclusion

A traffic light color classifier was implemented using HSV color segmentation, binary masks and approximate signal positions.

The implementation follows the basic image processing approach introduced in the first laboratory work.

The method provides a simple and interpretable solution for traffic light color classification. Some difficult cases remain due to lighting, background colors and the appearance of the traffic light housing, but they also demonstrate the practical limitations of fixed color-based segmentation.