# python-video-face-detection
#pip install opencv-python
import cv2

# to detect the face using this xml file
# to link the file in CascadeClassifier function
data = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')

# get the video or reading the video from the local storage
#save video name in face.detect.mp4 
video = cv2.VideoCapture('face.detect.mp4')  # for webcam detect use (0)

# infinity loop
while True:
    # video is collection of frame
    # read the frame using in bulit-in function
    # got two output,so using two variables
    success, frame = video.read()

    if success == True:
        # convert grayscale
        # cvtcolour built-in function
        # cvtColor - covert the color
        gray_image = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        # detectMultiScale given the coordinates from the image
        faces = data.detectMultiScale(gray_image)

        # get the image coordinates
        # multiple face detect using for loop
        for x, y, w, h in faces:
            # add x+Width and y+Height
            # rectangular colour - (0, 0, 550) -(red)
            # and 2 is thickness of rectangular
            # rectangle function is detect the face and givin output like a Box
            cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 0, 550), 2)

        # show the video
        cv2.imshow('video', frame)
        # for the window waiting
        cv2.waitKey(1)

    else:
        print("video played completed")
        break
