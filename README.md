This repository has 2 notebooks that display segmentation code for yolo algorithms, i.e. v7 and v8. The data was obtained from roboflow which has the bounding segments.
The code for directly importing the segmented dataset into the notebook is:
```
!pip install roboflow

from roboflow import Roboflow
rf = Roboflow(api_key="mBEsgz8WVaKY7RkG2fqU")
project = rf.workspace("moin-mawsb").project("potholesdetectionandsegmentation")
dataset = project.version(2).download("yolov7")
```

* After importing the dataset, just make sure to change the file path of the train, test, and val in the data.yaml file. Failing to do so, will result in the model not being able to train and test on the particular custom data.
![image](https://github.com/katikkale15/yoloy_v7_v8_segmentation_custom_data/assets/98995391/2acfb080-4412-4416-91d2-072d6f3791d8)
The above image shows the performance criteria of different yolo v8 models.

The v8 code in this given notebook is done in command line form. To do the same code in python it will be:
Importing the yolo from ultralytics:
```
from ultralytics import YOLO
```
Yolo code for image:
```
#Initialize YOLO with the model name
model = YOLO("yolov8m-seg.pt")
#Predict Method Takes all the parameters of the Command Line Interface
model.predict(source='/content/image1.jpg',  save=True, conf=0.5,save_txt=True)
```
Yolo code for Video:
```
#Initialize YOLO with the model name
model = YOLO("yolov8m-seg.pt")
#Predict Method Takes all the parameters of the Command Line Interface
model.predict(source='/content/demo.mp4',  save=True, conf=0.5, save_txt = False)
```
Yolo code to export in onnx format:
```
#Initialize YOLO with the model name
model = YOLO("yolov8m-seg.pt")
#Export the Model in the onnx format
model.export(format="onnx")
```


Hope this helps!
