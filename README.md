# Report

### 1. Taking photos

I have taken 40 photos of my enviornment, specifically  focusing on taking photos of chairs and radiators, as those two are the objects that I will try to rpedict with the help of my models.
![image](https://user-images.githubusercontent.com/63430051/223190510-ff19540c-01d2-43a7-9de2-407cb0b35a26.png)

### 2. Annotating photos

All 40 images were annotated into 2 classes: chairs and radiators, more than 100 objects were taken in total.
![image](https://user-images.githubusercontent.com/63430051/223190810-00622961-be8c-48a9-81ea-5ea23830ae0b.png)

### 3. Train a faster RCNN model using detectron2

An RCNN model was trained on detectron2 with the following hyperparameters (with the exception of number of epochs, which was set to 50, just like in Yolo):
![image](https://user-images.githubusercontent.com/63430051/223205984-48787c2e-7229-4f08-9aeb-4ea912c0c260.png)
![image](https://user-images.githubusercontent.com/63430051/223212835-f9a8bfbf-d677-4379-b55d-a2b951d8e03b.png)

Unfortunately, I cannot show the results of the training inside the notebook, as I was forcefully disconnected from Google Collab runtime, lost all outputs and values, and after restarting the notebook, I could never again load the dataset from roboflow, which eventually gets stuck at approximately 50%.
![image](https://user-images.githubusercontent.com/63430051/223213443-279f9cb7-8bc1-41c7-a9b9-a22b23cbed25.png)
Clearing out all the loaded files, restarting the notebook and restarting the runtime did not help, so I failed to re-run the code to its completion, though it did work before and I was able to recieve AP values.

### 4. Train Yolov4/5/6/7/8 (only one of them of choice) the smallest size

I have made the decision to train with Yolov8 (small size) with 25 epochs. Following results were achieved:
![image](https://user-images.githubusercontent.com/63430051/223214135-16e78e7a-d302-4c95-a8cb-78700d3792e4.png)

### 5. Evaluate both models based on mAP and speed and size.

Unfortunately, I cannot provide current mAPs for the Detectron model, as I am currently incapable to reproduce its results. However, I can restore from memory that it gave values in range of 0.15-0.19, thereby having a significantly smaller accuracy than the Yolov8 model, which averages at 0.379, and predicts chair slightly more successfully than a radiator. 
![image](https://user-images.githubusercontent.com/63430051/223214796-3713a5da-9ccf-4a70-859f-7f41dc486a29.png)
I found Yolov8 significantly faster than Detectron2 model, while remaining significantly smaller.
![image](https://user-images.githubusercontent.com/63430051/223214937-0a166ee1-a6cb-4fbf-a502-ec342b6c879e.png)
Thus, I found no redeeming qualities for Detectron2's Faster R-CNN, and Yolov8 one-stage object detection model performed better in all respects. 
