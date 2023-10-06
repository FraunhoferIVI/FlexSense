The dataset consists of 29 recorded sequences using an infrared camera and a 3D radar sensor. 
The sensors work at 20Hz. 
In total 9730 frames are recorded.
24998 3D bounding boxes are provided.

### Content of Dataset

```---
  ├── IVI_Dataset_V1.0_FlexSense
    ├── calib
    ├── image
    ├── label
    ├── tracking
    └── radar
```

*calib* contains the intrinsic calibration results of the IR camera and the extrinsic transformation between the camera and the radar.

Images are stored in the *image* folder. 

*label* contains the label for 3D object detection.

*tracking* contains the label for 3D object tracking.

The bin files in folder *radar* contain the point cloud from the Continental ARS548 imaging radar. 

The labeling is done using the [3D-BAT tool](https://github.com/walzimmer/bat-3d). In the labeling process, we tried our best to place the bounding box to match object extend in both 2D image plane and 3D point cloud world. If some of the 3D points don't perfectly fall into the bounding box, due to the sparsity of the point cloud, we have to consider them to be outlier. 


### Data Split

Training set 6937 frames, Validation set 2793 frames.

|Sequences| Length (Frames) | Train/Val    | Accumulated | 
|---|---|---|---|
|Intersection sequence 1   | 374  | Train  | |
|Intersection sequence 2   | 338  | Train  | |  
|Intersection sequence 3   | 374  | Train  |  | 
|Intersection sequence 4   | 393  | Train  |  | 
|Intersection sequence 5   | 392  | Train  |  | 
|Intersection sequence 6   | 319  | Train  |  | 
|Intersection sequence 7   | 393  | Train  |   
|Intersection sequence 8   | 391  | Train  |   
|Intersection sequence 9   | 391  | Train  |   
|Intersection sequence 10   | 346  | Train  |  3711 
|Road sequence 1   | 292  | Train  |   
|Road sequence 2   | 366  | Train  |   
|Road sequence 3   | 237  | Train  |   
|Road sequence 4   | 242  | Train  |   
|Road sequence 5   | 289  | Train  |   
|Road sequence 6   | 305  | Train  |   
|Road sequence 7   | 353  | Train  |   
|Road sequence 8   | 228  | Train  |   
|Road sequence 9   | 238  | Train  |   
|Road sequence 10   | 320  | Train  |   
|Road sequence 11   | 356  | Train  |   6937
|Intersection sequence 11  | 375  | Val  |   
|Intersection sequence 12  | 384  | Val  |   
|Intersection sequence 13   | 388  | Val  |   
|Intersection sequence 14   | 385  | Val  |  8469 
|Road sequence 12  | 342  | Val  |  
|Road sequence 13  | 284  | Val  |   
|Road sequence 14   | 371  | Val  | 
|Road sequence 15   | 264  | Val  | 9730



### Detection Labels (kitti)

|Values  |  Name     | Description|
|-|-|-|
|   1   | type   |      Describes the type of object: 'Car', 'Van', 'Truck','Pedestrian', 'Person_sitting', 'Cyclist', 'Tram','Misc' or 'DontCare'|
|   1  |  truncated  |  Float from 0 (non-truncated) to 1 (truncated), where truncated refers to the object leaving image boundaries|
|   1   | occluded   |  Integer (0,1,2,3) indicating occlusion state: 0 = fully visible, 1 = partly occluded, 2 = largely occluded, 3 = unknown |
|   1   | alpha  |      Observation angle of object, ranging [-pi..pi]|
|   4   | bbox   |      2D bounding box of object in the image (0-based index):contains left, top, right, bottom pixel coordinates|
|   3   | dimensions |  3D object dimensions: height, width, length (in meters)|
|   3  |  location |    3D object location x,y,z in camera coordinates (in meters)|
|   1   | rotation_y |  Rotation ry around Y-axis in camera coordinates [-pi..pi]|
| (1)   | score  |      Only for results: Float, indicating confidence in detection, needed for p/r curves, higher is better.|
  
### Tracking Labels (kitti)

|Values |   Name   |   Description|
|-|-|-|
|   1   | frame    |    Frame within the sequence where the object appearers|
|   1   | track id  |   Unique tracking id of this object within this sequence|
|   1   | type       |  Describes the type of object: 'Car', 'Van', 'Truck', 'Pedestrian', 'Person_sitting', 'Cyclist', 'Tram','Misc' or 'DontCare'|
|   1   | truncated  |  Float from 0 (non-truncated) to 1 (truncated), where truncated refers to the object leaving image boundaries. Truncation 2 indicates an ignored object (in particular in the beginning or end of a track) introduced by manual labeling.|
|   1    |occluded  |   Integer (0,1,2,3) indicating occlusion state: 0 = fully visible, 1 = partly occluded 2 = largely occluded, 3 = unknown|
|   1   | alpha     |   Observation angle of object, ranging [-pi..pi]|
|   4   | bbox       |  2D bounding box of object in the image (0-based index):contains left, top, right, bottom pixel coordinates|
|   3   | dimensions  | 3D object dimensions: height, width, length (in meters)|
|   3   | location   |  3D object location x,y,z in camera coordinates (in meters)|
|   1   | rotation_y |  Rotation ry around Y-axis in camera coordinates [-pi..pi]|
|   (1)   | score     |   Only for results: Float, indicating confidence in detection, needed for p/r curves, higher is better.|
