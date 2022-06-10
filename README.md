# Autonomous Vehicle Object Detector
bject Detector using Darknet and YOLOv4 to detect traffic signs, traffic lights, and other vehicles.



## Process
I was referred to an open source Google Colab notebook by the AI Guy and used that to help springboard my modeling. To create the model I would be using the Darknet open-source neural network and YOLO object detector. To explain the power of YOLO, lets first compare it to a traditional object tracker which utilizes a sliding window.

## Traditional Object Detection
![sliding_window](/images/sliding_window.gif)    

- [Source](https://towardsdatascience.com/how-do-self-driving-cars-see-13054aee2503)
    
As you can observe, the window goes over every part of the image until it detects the actual object, in this case the car. There are two boxes: a Ground Truth Box which was was placed in the picture manually prior to modeling and the other is the Predicted Box which is where the model predicts where the object is. These two boxes are used to calculate the Intersection of Union (IoU) which calculates the Mean Average Precision (mAP). Overall, this process is very computer intensive and inefficient for object detection. In terms of autonomous vehicles.

## YOLO

![yoloimage](/images/yoloimage.png)      

- [Source](https://towardsdatascience.com/how-do-self-driving-cars-see-13054aee2503)

What happens in YOLO differently than the above are these three steps: Grid segmentation, Classification, and Image Localization. In this method the model needs to go over an image/video frame one time. Grid segmentation breaks down the picture into evenly sized grid-blocks so every part of the picture is accounted for. Then the model will identify the different classes of the image, in this case dog, bike, and truck. Finally, the objects are located using bounding boxes, as mentioned above, which locate where the objects are within the image, hence the name Image Localization. Putting all that together, you have your model that has successfully identified a dog, bike, and truck and the locations of all of them within an image.

## Image Collection and Pretrained Weights
- used all my images of cars, traffic lights, traffic signs, and stop signs from Google Open Images. 
- used YOLOv4 Pre-trained weights which are trained on Microsoft's COCO Dataset of 80 classes. In those 80 classes you have cars, traffic lights, and stop signs.

## Results
As you can see it picks up all the traffic lights, cars, and traffic signs! Good.
![yolomodel](/images/yolomodel.gif)


### Mean Accuracy Precision 

- Cars: 80.70%
- Stop Signs: 98.20%
- Traffic Lights: 75.06%
- Traffic Signs: 42.49%
- Overall mAP: 74.11%

Note: The Traffic Signs have the lowest mAP since it did not have any pre-trained weights to train on.


