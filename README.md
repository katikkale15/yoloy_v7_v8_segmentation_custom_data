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
