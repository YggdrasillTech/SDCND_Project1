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
Now that we have the HLS Color Space of our original image we can filter it by color. Since roads use two different color to separate lines we're going to filter these colors. Yellow and White, for Yellow the Hue typically lies around a value of 40, in the case of White the election is 0 to 255 but with a maximum Lightness between 200 and 255.
After filtering both color the next step is to combine and generate a single binary mask.

---
### **3. Masking original image with Yellow/White Mask and Gray Scale Image conversion**


---
### **4. Blur Image Filtering and Canny Edge Operator**


---
### **5. Extract Regions Of Interest over the Canny Edges Image result**


---
### **6. Obtain the Hough Lines of the image and Draw them**


---
### **7. Finally combine the original image and the Hough Lines image**


--
## **Potential shortcomings**

---
## **Potential Improvements**
