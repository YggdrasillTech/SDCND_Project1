# **Finding Lane Lines on the Road**
This **README** file serve as write-up for the Udacity SDCND Project1

---
## **Description of the Pipeline**
The pipeline for the Finding Lane Lines consist of 7 mayor steps:

1. Color Space conversion to **HLS**.
2. **Color Filtering**, Yellow/White.
3. **Masking** original image with Yellow/White Mask and **Gray Scale** Image conversion.
4. **Blur Image Filtering** and **Canny Edge Operator**.
5. Extract **Regions Of Interest** over the Canny Edges Image result.
6. Obtain the **Hough Lines** of the image and **Draw** them.
7. Finally **combine** the original image and the Hough Lines image.

---
### **1. Color Space conversion to HLS**
Typically, an image is represented in a color space that we call RGB. But this color space is not suitable to filter images by color (apart from Red, Green, Blue).
There are other color spaces more suitable for this case such as HLS and HSV. For this pipeline the choice was HLS (Hue, Lightness, Saturation). HLS Color Space permit us to choose a Hue and separate the different color in the complete spectrum.

---
### **2. Color Filtering, Yellow/White**
Now that the pipeline has the HLS Color Space of our original image we can filter it by color. Since roads use two different color to separate lines program's going to filter these colors. Yellow and White, for Yellow the Hue typically lies around a value of 40, in the case of White the election is 0 to 255 but with a maximum Lightness between 200 and 255.
After filtering both color the next step is to combine and generate a single binary mask.

---
### **3. Masking original image with Yellow/White Mask and Gray Scale Image conversion**
In order to generate an image with high contrast (Ideal for Canny Operator) the program is going to mask the original image using the Yellow/White binary mask. For this, the use of bitwise operation with OpenCV is perform.
Additionally, the pipeline performs a conversion to Gray Scale image, in which next step is going to operate.

---
### **4. Blur Image Filtering and Canny Edge Operator**
Before applying Canny Edge Detector a Blur filter should be applied. For this pipeline the kernel size is equal to 15. The reason is because since images may have compression artifacts and also are taken from real situations that means some noise is within each frame.
After applying Blur to the image the pipeline applies the Canny Operator.

---
### **5. Extract Regions Of Interest over the Canny Edges Image result**
This step in the pipeline is straightforward, using image shape, the program calculates a Region Of Interest and with the use of fillPoly creates al binary mask in which after applied over the Canny Image, only the pixels within the ROI area are going to get to the next step.

---
### **6. Obtain the Hough Lines of the image and Draw them**
Using the masked Canny Image as input for this step, the pipeline calculates an draws the Hough Lines in a black image.
To do this first the OpenCV built-in function for Hough Lines is used, this function return a list of lines consisting of start-end points.
With the use of these points, the program calculates all the b, m and length of each of these lines. These parameters are going to be average using the length as weights (a large line contributes more than a shorter one).
At the end only two lines (maximum) should be detected and drawn.

---
### **7. Finally combine the original image and the Hough Lines image**
The last step in the pipeline is the easiest one, with the Hough Lines Image and the original one the function weighted_img combines both of them and outputs it as result.

---
## **Potential shortcomings**
Even though this simple model could be robust in most situations, it is not suitable for the bet of the challenges for example:

* Curve Lines
* Weather conditions with low visibility
* Lanes with poor conditions in the painting
* Rapid Changes in Lightness of the scene
* Line gaps greater than expected

---
## **Potential Improvements**
Some thoughts about possible improvements:

* Use of the Canny Edges points to fit a curve (quadratic possibly?)
* Regularization and equalization may improve image
* Camera with a different perspective of the road
