

# OpenCV_photo-to_cartoon  .   
 
 
 
 ### This time, we are going to create an image cartoon effect using Python.. Here we're using openCV and numpy to create cartoon effects using  Python.


## Source code blocks can be created as follows.



~~~python



import cv2
import numpy as np
from tkinter.filedialog import *


photo = askopenfilename()
img = cv2.imread(photo)


grey = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
grey = cv2.medianBlur(grey, 5)
edges = cv2.adaptiveThreshold(grey, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 9, 9)


#cartoonize
color = cv2.bilateralFilter(img, 9, 250, 250)
cartoon = cv2.bitwise_and(color, color, mask = edges)


cv2.imshow("Image", img)
cv2.imshow("Cartoon", cartoon)


#save
cv2.imwrite("cartoon.jpg", cartoon)
cv2.waitKey(0)
cv2.destroyAllWindows()


~~~


# Result

<img width="1440" alt="스크린샷 2023-03-26 오후 10 07 58" src="https://user-images.githubusercontent.com/119654152/227978790-40f1b46b-4dad-4a29-b5a3-32e8e57e4e58.png">
. 


