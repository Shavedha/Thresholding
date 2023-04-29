# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm
### Step 1:
Load the necessary packages.

### Step 2:
Read the Image and convert to grayscale.

### Step 3:
Use Global thresholding to segment the image.

### Step 4:
Use Adaptive thresholding to segment the image.

### Step 5:
Use Otsu's method to segment the image.

### Step 6:
Display the results.
## Program

```python
# Load the necessary packages
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale
image = cv2.imread("hya.jpg",1)
image = cv2.cvtColor(image,cv2.COLOR_BGR2RGB)
image_gray = cv2.imread("hya.jpg",0)

# Use Global thresholding to segment the image
ret,thresh_img1 = cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY)
ret,thresh_img2=cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY_INV)
ret,thresh_img3=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO)
ret,thresh_img4=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO_INV)
ret,thresh_img5=cv2.threshold(image_gray,100,255,cv2.THRESH_TRUNC)

# Use Adaptive thresholding to segment the image
thresh_img7=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
thresh_img8=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)

# Use Otsu's method to segment the image 
ret,thresh_img6=cv2.threshold(image_gray,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Display the results
titles=["Gray Image","Threshold Image (Binary)","Threshold Image (Binary Inverse)","Threshold Image (To Zero)"
       ,"Threshold Image (To Zero-Inverse)","Threshold Image (Truncate)","Otsu","Adaptive Threshold (Mean)","Adaptive Threshold (Gaussian)"]
images=[image_gray,thresh_img1,thresh_img2,thresh_img3,thresh_img4,thresh_img5,thresh_img6,thresh_img7,thresh_img8]
for i in range(0,9):
    plt.figure(figsize=(5,5))
    plt.subplot(1,2,1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis("off")
    plt.subplot(1,2,2)
    plt.title(titles[i])
    plt.imshow(cv2.cvtColor(images[i],cv2.COLOR_BGR2RGB))
    plt.axis("off")
    plt.show()

```
## Output

### Original Image
<img width="312" alt="image" src="https://user-images.githubusercontent.com/93427376/235286602-e07bfa3f-a814-429a-ac96-e77499b32933.png">

### Global Thresholding
<img width="314" alt="image" src="https://user-images.githubusercontent.com/93427376/235286710-be0f801f-3ae2-45a7-b39a-2094e50b2ba7.png">
<img width="338" alt="image" src="https://user-images.githubusercontent.com/93427376/235286722-ae35f8bc-d3fd-42f7-9725-c3defad8cfe1.png">
<img width="318" alt="image" src="https://user-images.githubusercontent.com/93427376/235286728-c0464696-b643-4647-a821-2076f4a0de48.png">
<img width="337" alt="image" src="https://user-images.githubusercontent.com/93427376/235286742-2f3205cd-9ecd-4d16-9411-15b00c544401.png">
<img width="319" alt="image" src="https://user-images.githubusercontent.com/93427376/235286760-01721d10-9cfe-4c89-94b4-fbe1431252c4.png">

### Adaptive Thresholding
<img width="320" alt="image" src="https://user-images.githubusercontent.com/93427376/235286773-c790a88c-cfae-41d3-bafb-9d1a94a079a7.png">
<img width="330" alt="image" src="https://user-images.githubusercontent.com/93427376/235286777-75e159d8-093a-41c8-a728-73807a749768.png">


### Optimum Global Thesholding using Otsu's Method
<img width="300" alt="image" src="https://user-images.githubusercontent.com/93427376/235286768-2ae83951-2a6e-4b03-9329-d0b6d5a3202c.png">


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

