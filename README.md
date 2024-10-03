# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## Program:
### Developed by: Vinush.CV
### Reg no: 212222230176
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Input image and grayscale image
```python
image = cv2.imread('badminton.jpg')  
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/87e0e852-b83b-471e-9025-8b82dc771117)

![image](https://github.com/user-attachments/assets/8741d8d8-3993-462e-b62a-4133dd2dd952)


### Canny Edge detector 
```python
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)

plt.subplot(2, 2, 3)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/081100f6-ba5a-4181-9d96-6caa0d579afb)


### Detect lines using the probabilistic Hough transform
```python

lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)
```
### Draw the lines on the original image
```python
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
```

### Hough Transform Result
```python
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/1cea566c-57f4-4fd2-8669-b100b5e817bc)

## Result:
Thus, the program to detect the lines using Hough Transform implemented successfully.

