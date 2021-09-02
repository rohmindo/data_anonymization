## Before
<img src = "https://user-images.githubusercontent.com/63469069/131832965-a010c023-edf3-4886-b64a-891857513124.png" width="40%" height="40%">

## After
<img src = "https://user-images.githubusercontent.com/63469069/131832869-9f987d3f-3aa9-4a71-b490-a8c68d1fb8d1.png" width="40%" height="40%">
 
## Table of Content
1. Introduction
2. Image Anonymization method
3. Results
4. Setup
5. Technologies
6. Sources

## 1. Introduction
### Background
Due to the recent development of SNS and technology, many data are shared. This makes it important to protect data privacy. It also has CAMERA for AI function implementation in many areas. As such, data privacy is becoming important in many fields.
Image anonymization is a technology that has emerged to protect personal information. This technology preserves privacy by removing identifiable personal information from images. Image anonymization technology is gaining more attention over time.
### Goal & Process
Image anonymization is carried out with a total of two goals. First of all, if the model is trained with anonymized dataset, the performance will inevitably be lower than that of the existing model. So the first goal is to minimize performance degradation and maintain ai utilization. The second is to preserve privacy by removing personal information from the image. With these two goals, image anonymization is carried out.
Prepare the original dataset and three anonymized dataset. Learn the deep learning model using each dataset. Compare the accuracy of these models to see which anonymization method is best.

## 2. Image Anonymization method
### Gaussian Blur
<img src = "https://user-images.githubusercontent.com/63469069/131833859-a7623861-6eb0-4c93-902b-90ea7ccf9935.png" width="15%" height="15%">
 
Similar to mosaic processing, images are blurred using adjacent image pixel values to remove personal information.
### Perspective Transformation
![image](https://user-images.githubusercontent.com/63469069/131833704-d80f7154-555a-4e71-8e16-1a884a3c0dba.png)![image](https://user-images.githubusercontent.com/63469069/131833719-3176fd82-317f-4501-aea7-0597504dc820.png)![image](https://user-images.githubusercontent.com/63469069/131833727-fc75f37f-6f6a-4146-a2f5-941f444fe50c.png)![image](https://user-images.githubusercontent.com/63469069/131833776-3538e257-d97b-47da-8a7e-d3bba510f91a.png)



In morphology operations, closed operations were selected as the representative anonymization technique. Closed operation means an erosion operation after a dilation operation. Because closed operations do erosion operations at the end, many pixels corresponding to personal information will be removed. Also, when tested with multiple images, closed was the most appropriate choice.
### Blocking&Merging
![image](https://user-images.githubusercontent.com/63469069/131834198-19d98551-b5b9-4b06-8214-85ede34d5563.png)

There are four stages in total. 

![image](https://user-images.githubusercontent.com/63469069/131834218-6ec65fcd-071c-4dc2-8711-ca8391a76d80.png)![image](https://user-images.githubusercontent.com/63469069/131834224-3747b42b-6670-4dbe-92eb-a9bc54104945.png)![image](https://user-images.githubusercontent.com/63469069/131834229-2a2a8af4-894a-49f8-8026-adc492f1b2bd.png)![image](https://user-images.githubusercontent.com/63469069/131834239-c9c0c14c-0f72-401b-a5d5-ce4b9f136f3d.png)

The first is the blocking phase. The user randomly creates missing parts and separates them into four sets.

![image](https://user-images.githubusercontent.com/63469069/131834353-19e9a07c-e093-47b8-ae5c-7c7090247b18.png)![image](https://user-images.githubusercontent.com/63469069/131834367-c012aa7f-0882-4ce0-b83b-c1b1c5368d7b.png)![image](https://user-images.githubusercontent.com/63469069/131834380-a1bf7e92-1e12-4b1d-bf81-8fca7be70552.png)![image](https://user-images.githubusercontent.com/63469069/131834389-8be347a1-3364-4628-8b47-dbb51af39249.png)

The second step is the process of recovering pixel values using adjacent pixels for missing parts created in blocking as an entering step. 

![image](https://user-images.githubusercontent.com/63469069/131834729-7e377b6f-d554-4fa9-a805-b6d4fd3e1037.png)

The third stage is the process of collecting the inserted pixels. 

![image](https://user-images.githubusercontent.com/63469069/131834746-317610cd-266f-4f36-9873-ccfd459888ca.png)![image](https://user-images.githubusercontent.com/63469069/131834770-6315cec1-70e1-4110-8b36-50b1012ea7bb.png)![image](https://user-images.githubusercontent.com/63469069/131834782-35ca07ff-5ec9-49a3-9ef3-97ded205a5bc.png)![image](https://user-images.githubusercontent.com/63469069/131834794-6b834a93-6632-462f-8c93-520fafd521d4.png)![image](https://user-images.githubusercontent.com/63469069/131834804-a2f983e5-03e5-4c27-8d18-e25f59ae3913.png)

The last step is the Add feature step. An operation that adds pixels corresponding to the feature after feature extension in the original image. If you add feature, ai will be more aware of the image.
## 3. Results

![image](https://user-images.githubusercontent.com/63469069/131835137-5b681420-567b-486b-bbe2-f68bd9ff2998.png)


## 4. SetUp
The dataset you use is imageNet dataset. The model proceeds fine-tuning with the resnet50 model. Each hyper parameter will be tuned by drawing a learning curve. First of all, the source image exists in the source /train,/test folder in mydataset folder. Now run Gaussian_blue, Morphology_blue, Inpainting.ipynb jupyter notebook in turn. Then dataset will be formed in mydataset folder respectively. Then run ResNet50.ipynb notetbook and check the results.
~~~
cd your workspace
git clone https://github.com/rohmindo/data_anonymization.git
// Run the jupyter notebook one by one and create a dataset in mydataset folder.
// Run the ResNet50.ipynb & See the result (You can see the result in Result.exel file)
~~~
~~~
// mydataset folder hierarchy
//mydataset
 /train
 /test
~~~

## 5. Technologies
### Dependency & Library
- Google Colab pro
- Python 3.7.11
- OpenCV 4.4.0
- Tensorflow 2.5.0
- Keras 2.5.0
- Numpy 1.19.5
- Pandas 1.1.5
- ORB Algorithm

## 6. Sources
- [ORB](https://docs.opencv.org/3.4/d1/d89/tutorial_py_orb.html)
- [Colab](https://colab.research.google.com/notebooks/welcome.ipynb?hl=ko)
- [OpenCV](https://opencv.org/)
