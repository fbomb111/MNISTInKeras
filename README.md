Welcome!  If you've stumbled here and notice something wrong please open an issue or PR.  Much to learn in ML and Python I still have.  Thanks!

# MLDemos

### Housing classification with sklearn Decision Tree

Tutorial: http://www.r2d3.us/visual-intro-to-machine-learning-part-1/

Dataset: https://github.com/jadeyee/r2d3-part-1-data/blob/master/part_1_data.csv


### MNIST CNN with Keras

https://github.com/fbomb111/MLDemos/blob/master/MNISTInKeras/MNIST%20in%20Keras.ipynb

A detailed look into CNN's with Keras and final output to Apple's CoreML `.mlmodel`


### iOS Sentiment Analysis with AWSComprehend

https://github.com/fbomb111/MLDemos/tree/master/AWSComprehend

Both a python notebook and iOS application to give a quick and simple sentiment analysis based on user-entered text using AWSComprehend


### Image Classifier with CreateML

https://github.com/fbomb111/MLDemos/blob/master/CreateML/Image%20Classification%20with%20CreateML%20a%20la%20code.md

Walkthrough using Apple's [CreateML](https://developer.apple.com/documentation/createml) framework to do some basic image classification programatically, plus some variations and explanations along the way.


### Object Detection with AWS SageMaker

https://github.com/fbomb111/MLDemos/blob/master/AWSSageMakerObjectDetection.ipynb

Use the tools and converters below along with the above notebook to help make your way through [this difficult documentation from AWS](https://docs.aws.amazon.com/sagemaker/latest/dg/object-detection.html).


## Converters (object detection)


### [OIDV4ToCreateMLJSONConverter.py](https://github.com/fbomb111/MLDemos/blob/master/Converters/OIDV4ToCreateMLJSONConverter.py)

Converts from [Google's Open Images Database](https://storage.googleapis.com/openimages/web/index.html), using the [OIDV4 tool](https://github.com/EscVM/OIDv4_ToolKit)), to a JSON format that can be used with [Apple's Create ML Object Detector](https://developer.apple.com/documentation/createml/mlobjectdetector/datasource).

### [SimpleAnnotatorCSVToCreateMLJSONConverter.py](https://github.com/fbomb111/MLDemos/blob/master/Converters/SimpleAnnotatorCSVToCreateMLJSONConverter.py)

Converts the CSV output from the [Simple Annotator Tool](https://github.com/sgp715/simple_image_annotator), to a JSON format that can be used with [Apple's Create ML Object Detector](https://developer.apple.com/documentation/createml/mlobjectdetector/datasource).

### [SimpleAnnotatorCSVToRecordIOLST.py](https://github.com/fbomb111/MLDemos/blob/master/Converters/SimpleAnnotatorCSVToRecordIOLST.py)

Converts the CSV output from the [Simple Annotator Tool](https://github.com/sgp715/simple_image_annotator), to the LST format required before conversion to REC format. [MXNet format details here](https://mxnet.apache.org/api/python/image/image.html#image-iterator-for-object-detection). 

More to come when I get this working with [AWS SageMaker Object Detection Algorithm](https://docs.aws.amazon.com/sagemaker/latest/dg/object-detection.html)

### Other helpful commands
```python
# create lst file

python ~/SimpleAnnotatorCSVToRecordIOLSTConverter.py --csv ~/path/myAnnotationsCSV.csv --images ~/path/mySourceImagesFolder --output ~/path/myOutputLocation

# create rec file

python ~/incubator-mxnet/tools/im2rec.py ~/my_train.lst ~/path/mySourceImagesFolder --recursive --pass-through --pack-label --num-thread 8

# upload to s3

aws s3 cp ~/my_train.rec 's3://my-bucket/train/train.rec'
```
