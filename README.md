# ncnn-android-yolov8 detection demo

The yolov8 object detection

This is a sample ncnn android project, it depends on ncnn library and opencv

https://github.com/Tencent/ncnn

https://github.com/nihui/opencv-mobile

## build custom yolov8 model on Android and run

### yolov8 model export ncnn by pnnx 

### **environment of OpenCV and ncnn **:

step1

<https://github.com/Tencent/ncnn/releases>

- Download ncnn-YYYYMMDD-android-vulkan.zip or build ncnn for android yourself
- Extract ncnn-YYYYMMDD-android-vulkan.zip into **app/src/main/jni** and change the **ncnn_DIR** path to yours in **app/src/main/jni/CMakeLists.txt**

step2

<https://github.com/nihui/opencv-mobile>

- Download opencv-mobile-XYZ-android.zip

- Extract opencv-mobile-XYZ-android.zip into **app/src/main/jni** and change the **OpenCV_DIR** path to yours in **app/src/main/jni/CMakeLists.txt**

  ### **how can we get ncnn model**：

- install pnnx ncnn

  ```
  pip3 install -U ultralytics pnnx ncnn
  ```

- export ncnn by pnnx

  ```
  yolo export model=yolov8s.pt format=ncnn  imgsz=320
  ```

![1739878886425](img\1739878886425.png)

### load ncnn model

- ncnn model get,  copy `model.ncnn.bin` and `model.ncnn.param` paste to project and change name like `yolov8s.bin` and `yolov8s.param`

- Open this project with Android Studio, build it and enjoy!

  ![1739880726335](img\1739880726335.png)

## yolov8 custom model export ncnn by pnnx 

- export ncnn by pnnx

  ```
  yolo export model=best.pt format=ncnn  imgsz=320
  ```

- ncnn model get,  copy `model.ncnn.bin` and `model.ncnn.param` paste to project and change name like `testpaper.bin` and `testpaper.param`

- change name of model match ncnn model  in `yolov8ncnn.cpp`

  ![1739879792770](img\1739879792770.png)

- change input and output for your model

  ![1739879919621](img\1739879919621.png)

- change number of class for your model

  ![1739880064896](img\1739880064896.png)

- change labels of class for your model

![1739880359204](img\1739880359204.png)

- rebuild this project with Android Studio!

  ![1739883134988](img\1739883134988.png)

## some notes

- Android ndk camera is used for best efficiency
- Crash may happen on very old devices for lacking HAL3 camera interface
- All models are manually modified to accept dynamic input shape
- Most small models run slower on GPU than on CPU, this is common
- FPS may be lower in dark environment because of longer camera exposure time

## screenshot

![1739880726335](img\1739880726335.png)

![1739883118862](img\1739883118862.png)

## Reference：  

https://github.com/nihui/ncnn-android-nanodet  

https://github.com/Tencent/ncnn  

https://github.com/ultralytics/assets/releases/tag/v0.0.0

https://github.com/FeiGeChuanShu/ncnn-android-yolov8

https://github.com/Abandon-ht/ncnn-android-yolo11
