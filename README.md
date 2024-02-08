# Python-Face-Detection-From-Image

## Code

```python
pip install opencv-python
```

1. Choose the image for detection
2. Create cascade classsifier object using thee Haar Cascade Classifier Algorithm
3. Read image file and create the image object
4. Convert the read image to Greyscale
5. Perform face detection and get the array of the detected faces in the greyscale image
6. For each detected face
    
        a. Draw the rectangle to indicate the detected faces in the image
        b. Display the image with the detected face indication for 2 seconds

7. Wait until "q" is pressed the close the window

```python
import cv2

imagePath = "people.jpg"
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades+"haarcascade_frontalface_default.xml")
image = cv2.imread(imagePath)
greyScaleImage = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
detectedFace = face_cascade.detectMultiScale(greyScaleImage)

for x,y,w,h in detectedFace:
    image = cv2.rectangle(image, (x,y), (x+w, y+h), (0,255,0), 2)
    cv2.imshow("Face Detection", image)
    cv2.waitKey(2000)
    
while True:
    if cv2.waitKey(1) & 0xFF == ord("q"): #check if q is press
        break
cv2.destroyAllWindows()
quit()
```

### Face Detection for video capture (real-time) or video clip

1. Choose the video source for detection (webcam or clip) and create a video capture object
2. Create cascade classifier object using thee Haar Cascade Classifier Algorithn
3. Use infinity while loop to keep the window appeared until 'q' is pressed
4. While the window is appreared:
    
        a. Capture each frame in the video capture object
        
        b. Convert each frame to Greyscale
        
        c. Perform face detection and get the array of the detected faces in each grayscale frame
        
        d. For each detected face:
        
            a. Draw the rectangle to indicate the detected faces in each frame
            
            b. Display each frame with the detected face indication
            
        e. If "q" is pressed then release the video capture and clost the window

### From Camera

```python
import cv2

videoCapture = cv2.VideoCapture(0) #### 0 to use camera #### #### change 0 to video fiel path ####
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades+"haarcascade_frontalface_default.xml")

while True:
    ret, frames = videoCapture.read()
    greyScaleFrame = cv2.cvtColor(frames, cv2.COLOR_BGR2GRAY)
    detectedFace = face_cascade.detectMultiScale(greyScaleFrame)
    for x,y,w,h in detectedFace:
        cv2.rectangle(frames, (x,y), (x+w,y+h), (0,255,0), 2 )
    cv2.imshow("Video Face Detection", frames)
    if cv2.waitKey(1) & 0xFF == ord("q"):
        break
videoCapture.release()
cv2.destroyAllWindows()
quit()
```

### From video path

```pyhton
import cv2

videoCapture = cv2.VideoCapture(people.mp4) 
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades+"haarcascade_frontalface_default.xml")

while True:
    ret, frames = videoCapture.read()
    greyScaleFrame = cv2.cvtColor(frames, cv2.COLOR_BGR2GRAY)
    detectedFace = face_cascade.detectMultiScale(greyScaleFrame)
    for x,y,w,h in detectedFace:
        cv2.rectangle(frames, (x,y), (x+w,y+h), (0,255,0), 2 )
    cv2.imshow("Video Face Detection", frames)
    if cv2.waitKey(1) & 0xFF == ord("q"):
        break
videoCapture.release()
cv2.destroyAllWindows()
quit()
```

## Result

![Fig01](https://github.com/psungg/Python-Face-Detection-From-Image/blob/main/Images/Fig01.png)
