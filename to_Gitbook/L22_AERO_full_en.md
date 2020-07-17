# Innopolis Open 2020 - L22_ÆRO team

## Team

* [Yuryev Vasily](https://vk.com/vasily_0x59).
* [Оконешников Дмитрий](https://vk.com/okoneshdmitriy).

## Final task description

New technologies are being implemented into various sectors of the economy including agricultural industry. Drones or UAV are no exception. Thanks to their usage, assessment of agricultural territories' states and analysis of landscape components became more effective and accessible.

<img src="../assets/photo_2020-06-18_18-54-23.jpg" width="300" title="One of the field options">

The final task of Innopolis Open 2020 was dedicated to monitoring agricultural territories and consisted of the following elements:

* Takeoff (from QR-code) and landing (onto a small colored marker).
* QR-code recognition.
* Colored objects recognition (Colored markers were used to show "agricultural territories").
* Determination of their coordinates (their locations change).
* Making a report using the gathered data.

## Code

Code on GitHub: https://github.com/vas0x59/ior2020_uav_L22_AERO.

## Main programm

При реализации кода в первоначальной концепции использовались свои типы сообщений, множество нод и других возможностей ROS, для обеспечения этого функционала необходимо создавать пакет и компилировать его, но из-за специфики соревнований (использование одной SD-карты для все команд) весь код был объединен в один файл. Данный подход усложнил отладку, но упростил запуск на площадке.

Elements of the program:

1. Takeoff.
2. QR code recognition.
3. Color markers recognition.
4. Landing.
5. Generate report and video.

The final coordinates of markers are automatically grouped and averaged data from the recognition system received for the entire flight. The "Zig-zag" trajectory was chosen to cover the entire territory. The Gazebo simulator is used for debugging.

## Color markers

`l22_aero_vision/src/color_r_c.py`

For image processing and object detection, we used functions from the OpenCV library.

Algorithm:

1. Receiving the image and camera parameters.
2. Building a mask based on a specific color range (in HSV format).
3. Detection of contours of colored objects.
4. Determining the type of an object, getting the key points of the object in the image.
5. Определение положения маркеров и зон посадок с помощью solvePnP основываясь на реальных размерах объектов и точках на изображении ([OpenCV Docs](https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html#ga549c2075fac14829ff4a58bc931c033d)).
6. Sending results to topics `/l22_aero_color/markers`  and  `/l22_aero_color/circles` (coordinates relative to `main_camera_optical` frame).

Во время разработки были созданы свои типы сообщений, а также сервис для настройки параметров детектора во время посадки. (`ColorMarker`, `ColorMarkerArray`, `SetParameters`).

To convert the position of colored objects into `aruco_map` frame TF library was used ([http://wiki.ros.org/tf](http://wiki.ros.org/tf))

Из-за искажений по краям изображения от fisheye-объектива все распознанные контуры находящийся рядом с краем изображения игнорируются. This filter is disabled during landing. Определение типа объекта производиться с помощью функций анализа контуров (`approxPolyDP` - кол-во вершин; `minAreaRect`, `contourArea` - соотношение площади описанного квадрата и площади контура + соотношение сторон).

<img src="../assets/5_D1_2.jpg" height="355">

Examples of marker recognition:

<iframe width="600" height="360" src="https://www.youtube.com/embed/kCW87RTA838" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Visualization in RViz

`l22_aero_vision/src/viz.py`

To debug object recognition, a script has been created that visualizes the coordinates of markers in the RViz utility.

<iframe width="560" height="315" src="https://www.youtube.com/embed/6xJ33UD-NfE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## QR-code

<img src="../assets/qr.jpg" width="400" title="A QR-code is being recognized during one of the attempts">

The PyZbar library was used to perform the QR-code recognition. In order to improve the accuracy of QR-code recognition, flights around the QR-code were performed at low altitude.

## Landing

Landing is performed in 3 stages:

1. Flight to the intended landing zone and hovering at an altitude of 1.5 m.
2. Descent to a height of 0.85 m with 3 adjustments to the marker coordinates relative to `aruco_map` frame.
3. Descent within a few seconds with adjustments based on the coordinates of the landing marker in `body` coordinate system (since ArUco-markers may no longer be visible), instead of `navigate`,` set_position` is used.

<iframe width="560" height="315" src="https://www.youtube.com/embed/8nVGoWkdYcA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Gazebo

По причине отсутствия возможности тестирования кода на своем реальном дроне было принято решение воспользоваться симулятором Gazebo.

To run the Clover software package in the simulator, you can use [this set of scripts](https://github.com/vas0x59/clever_sim) or [original instruction from PX4](https://dev.px4.io/v1.9.0/en/simulation/ros_interface.html).

Для Innopolis Open было создано несколько тестовых сцен. [ior2020_uav_L22_AERO_sim](https://github.com/vas0x59/ior2020_uav_L22_AERO_sim).

Также использование симулятора ускорило отладку полного выполнения кода, так как запуск производился с real time factor=2.5.

<img src="../assets/real_map.jpg" height="250">

<img src="../assets/big_map.jpg" height="250">

При тестировании выявлены некоторые проблемы (некорректное положение `aruco_map`) с использованием дисторсии в плагине камеры, поэтому в симуляторе использовалась камера типа Pinhole (без искажений от объектива).

## ROS

Created nodes, topics, messages and services.

### Nodes

* `l22_aero_vision/color_r_c.py` - recognition of colored objects.
* `l22_aero_vision/viz.py` - visualization in RViz
* `l22_aero_code/full_task.py` - main code.

### Topics

* `/l22_aero_color/markers` (`l22_aero_vision/ColorMarkerArray`) - list of rectangular markers.
* `/l22_aero_color/circles` (`l22_aero_vision/ColorMarkerArray`) - list of round markers.
* `/l22_aero_color/debug_img` (`sensor_msgs/Image`) - image for debugging.
* `/qr_debug` (`sensor_msgs/Image`) - image for debugging.

### Messages

#### `ColorMarker`

```
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

#### `ColorMarkerArray`

```
std_msgs/Header header
l22_aero_vision/ColorMarker[] markers
```

### Services

#### `SetParameters`

```
float32 rect_s1
float32 rect_s2
float32 circle_r
int32 obj_s_th
int32 offset_w
int32 offset_h
---
```
