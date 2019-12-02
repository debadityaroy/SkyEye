# SkyEye dataset
<h2>Dataset for analyzing lane-less traffic behavior at intersections </h2>

Part of the [M2Smart project!](http://m2smart.org/en/)  

<img src="images/m2smart.png" width="200"> <img src="images/nihon.jpg" width="100"> <img src="images/iith.png" width="100">



The SkyEye dataset is the first aerial dataset for monitoring intersections with mixed traffic and lane-less behavior. Around 1 hour of video each from 4 intersections, namely, Paldi (P), Nehru bridge - Ashram road (N), Swami Vivekananda bridge - Ashram road (V), and APMC market (A) in the city of Ahmedabad, India.

**Paldi (P)**         | **Nehru Bridge Ashram Road (N)** 
----------------|--------------
![](images/paldi.png) |![](images/nehru.png)
4-way signalized intersection | 4-way signalized intersection
**Swami Vivekananda bridge - Ashram road (V)** | **APMC market (A)**
![](images/vivek.png) |![](images/apmc.png)
7-way signalized intersection | 3-way unsignalized intersection

These intersections were considered because of the diverse
traffic conditions they present. 

The videos were captured using a DJI Phantom 4 Pro drone at 50 frames per
second in 4K resolution (4096x2160). 

<h1> Annotation </h1>
There are 50,000 frames in total with 4,021 distinct road user tracks
are annotated. A detailed breakdown is below:

**Number of unique road users**

Intersection | car | bus | motorbike (includes all two-wheelers) | auto-rickshaw | truck | van | pedestrains
-|-|-|-|-|-|-|-
P | 175 | 54 | 881 | 494 | 45 | 16 | 226
V | 132 | 9 | 627 | 195 | 7 | 0 | 9 | 9
N | 41 | 8 | 275 | 99 | 12 | 6 | 33
A | 73 | 6 | 402 | 135 | 43 | 0 | 81
**Total** | **421** | **77** | **2185** | **971** | **129** | **349**

<h2> Downloads </h2>
There are two versions of the same dataset available for either multi-class multi-object tracking or multi-class multi-object detection.
<h3> Multi-class Multi-object Detection </h3>

* Dataset consists of 49,652 images. [Google drive link for download]()
* Annotations (in Pascal VOC XML format) [Google drive link for download]()

<h3> Multi-class Multi-vehicle Tracking </h3>

* Dataset consists of 11 videos. [Google drive link for download]()
* Annotations (in MOT format). [Google drive link for download]() 

`frame_number, object_id, top_left_x, top_left_y, width, height, road_user_type`


Road User type | Name
-|-
1 | car
2 | bus  
3 | motorbike (includes all two-wheelers)
4 | autorickshaw
5 | truck
6 | van
7 | pedestrian 


<h2> Vehicle localization and type detection</h3>
The [Retinanet](https://github.com/fizyr/keras-retinanet) architecure is trained for vehicle localization and type detection.

* The images and annotations are divided into 1920x1080 tiles using the (scripts/slice_images_with_annotations.py) script.
* The sliced XML annotations are then grouped as 3 CSV files - train_annotations, test_annotations, and val_annotations using the (scripts/xml_to_csv.py) script.
  * An example of train_annotations, test_annotations, and val_annotations is uploaded [here](). 
* The trained weights for our Retinanet model are uploaded [here](). We started with the [resnet50_coco_best_v2.1.0.h5](https://github.com/fizyr/keras-retinanet/releases/download/0.5.1/resnet50_coco_best_v2.1.0.h5) model.
* For replicating the results shown here, follow the training procedure given in [keras-retinanet](https://github.com/fizyr/keras-retinanet) repo.

<h3> Results </h3>

The **meanAP**  for the trained model is **0.8154**.

Road user type | Average Precision (AP)
-|-
car | 0.9752
bus | 0.9848
motorbike | 0.6109
autorickshaw | 0.9793
truck | 0.935
van | 0.9678
pedestrian | 0.2364


<h2> Multi-object Tracking </h2>


<h2> Acknowledgment </h2>
This work has been conducted as the part of SATREPS project entitled on “Smart Cities development for Emerging Countries by Multimodal Transport System based on Sensing, Network and Big Data Analysis of Regional Transportation” (JPMJSA1606) funded by JST and JICA. 
