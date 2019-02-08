# YOLOv3-real-time-parking-lot-car-recognition

## Instroduction

This project is do identify cars parked in a certain parking spot. To achieve this goal, the main steps are as following:

- Download the video files and extract the first frame as input image

- Use YOLOv3 to detect objects in an image

- Use SIFT (Scale-Invariant Feature Transform) algorithm to find keypoints and descriptors from an image, then we can match local features to each other and therefore compare images to each other

## Dependencies

- Python 3.6
- opencv 3.4.2 (lastest version doesn't support SIFT detector)
- yolov3.weights
- coco.names

## Implementation

### 1 Download 

Use OpenCV bulid-in function VideoCapture() to read the video, save the first frame in a file named image
- I didn't process all the video files. I choose the 2000th video as start point and sample every 60 videos to 8000th and get the first frame.

### 2 Extract the car in the box

- Detection Using YOLOv3 Model

    - Install Darknet
```
git clone https://github.com/pjreddie/darknet
cd darknet
make
```

    - Download the pre-trained YOLO v3 weights file
```
wget https://pjreddie.com/media/files/yolov3.weights
```
- Extract the detected car or truck in the certain spot

### 3 Compute the similarity between two cars

- find the keypoints and descriptors with SIFT
- FLANN based matcher to match the keypoints found in last step
    - FLANN stands for Fast Library for Approximate Nearest Neighbors. It contains a collection of algorithms optimized for fast nearest neighbor search in large datasets and for high dimensional features. 
