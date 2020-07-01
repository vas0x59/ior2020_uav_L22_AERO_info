

### ROS

#### Messages
 - ColorMarker
```cpp
string color
int16 cx_img
int16 cy_img
float32 cx_cam
float32 cy_cam
float32 cz_cam
float32 size1
float32 size2
int16 type
```
 - ColorMarkerArray
```cpp
std_msgs/Header header
l22_aero_vision/ColorMarker[] markers
```
#### Services
 - SetParameters
```
float32 rect_s1
float32 rect_s2
float32 circle_r
int32 obj_s_th
int32 offset_w
int32 offset_h
---
```

#### Nodes

#### Topics


#### 