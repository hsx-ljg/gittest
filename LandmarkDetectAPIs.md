# LandmarkDetect APIs Documentation

#### Table of Contents
* [About LandmarkDetect](#About_LandmarkDetect)
* [Interface Design](#Interface_Design)
   * [LandmarkDetect](#LandmarkDetect)
      * [readBinModel](#readBinModel)
      * [getMeanShape](#getMeanShape)
      * [getNumLandmarks](#getNumLandmarks)
      * [detect49](#detect49)
      * [track49](#track49)
* [How to use LandmarkDetect Library on Windows](#How_to_use)
* [How to use LandmarkDetect Library on Linux](#How_to_use_Linux)
* [How to run LandmarkDetect Demo on Windows](#How_to)
* [How to run LandmarkDetect Demo on Linux](#How_to_Linux)

<h2 id="About_LandmarkDetect" >About LandmarkDetect</h2>
LandmarkDetect can detect and track faces from camera, video or image. the output is the landmark points of faces.

<h2 id="Interface_Design" >Interface Design</h2>


* <h4 id="LandmarkDetect"> LandmarkDetect</h4>  
LandmarkDetect is a interface class which provide read model,get meanShape,get Landmark points number, detect and track  functions.

* <h4 id="readBinModel"> readBinModel</h4>  
Read binary model
  ```C++
  bool LandmarkDetect::readBinModel(string filename)
  ```
     * `filename` binary model path
     * `return value` if true succeed, else failed

* <h4 id="getMeanShape"> getMeanShape</h4>   
Get mean landmark number
  ```C++
cv::Mat LandmarkDetect::getMeanShape() const
  ```
     * `return value` a clone cv::Mat of mean landmark

* <h4 id="getNumLandmarks"> getNumLandmarks</h4>   
Get landmark point number
 ```C++
int LandmarkDetect::getNumLandmarks() const
 ```
    * `return value` the number of landmark point

* <h4 id="detect49"> detect49</h4>   
detect 49 landmark points
```C++
bool LandmarkDetect::detect49(cv::Mat& meanShape, cv::Mat& image, cv::Rect faceBox, float& score)
```
  * `meanShape` a cv::Mat which can be from `getMeanShape`
  * `image` a cv::Mat which can be from input image or video frame
  * `faceBox` face boundbox
  * `score` it is a ouput, calculate detect quailty
  * `return value` if true succeed, else failed

* <h4 id="track49"> track49</h4>   
track 49 landmark points
```C++
void LandmarkDetect::track49(cv::Mat& meanShape, cv::Mat& modelShape,  cv::Mat& image, float& score)
```
  * `meanShape` a cv::Mat which can be from `getMeanShape`
  * `modelShape` a cv::Mat which is from detected face Mat
  * `image` a cv::Mat which can be from input image or video frame
  * `score` it is a ouput, calculate track quailty

<h2 id="How_to_use">How to use LandmarkDetect Library on Windows</h2>
1. In `Visual Studio 2015`, create a empty project
2. Configure project build mode as `X64` `Release`
3. It depends `OpenCV 3.1`, import OpenCV firstly
4. Configure include path ,Configuration Page -> C/C++ -> Additional Include Path -> `\LandmarkDetect\src`
5. Configure dependency Library ,Configuration Page ->Linker -> Input -> Additional dependency -> `LandmarkDetect.lib`
6. Configure dependency Library directory ,Configuration Page ->Linker -> General -> Additional dependency directory-> `LandmarkDetect/lib/x64`
7. Follow `LandmarkDetect/src/main.cpp` example, call APIs

<h2 id="How_to_use_Linux">How to use LandmarkDetect Library on Linux</h2>
1. LandmarkDetect Library is compiled under `Ubuntu 14.04` `X64`
2. configure Header  `LandmarkDetect/src/` in MakeFile
3. configure Library `-L./LandmarkDetect/lib/ -lLandmarkDetect` in MakeFile
4. Follow `LandmarkDetect/src/main.cpp` example, call APIs


<h2 id="How_to">How to run LandmarkDetect Demo on Windows</h2>
1. Enter `LandmarkDetect\bin\x64\Release` directory
2. Check script and update argument
     * test_input_camera.bat, the input is from camera  

      ```
      $ cat test_input_camera.bat
      @set sDataPath=..\..\..\..\..\Data
      LandmarkDetectTest.exe %sDataPath%\49New.bin
      ```
        * `sDataPath` it is binary model directory

  * test_input_image.bat, the input is from image path

    ```
    $ cat test_input_image.bat
    @set sDataPath=..\..\..\..\..\Data
    @set sDataTestPath=..\..\..\..\..\DataTest\comm
    LandmarkDetectTest.exe %sDataPath%\49New.bin -i %sDataTestPath%\CMU_small\100_1885.JPG
    ```
        * `sDataPath` it is binary model directory
        * `-i` input image path

  * test_videocapture_image.bat, the input is from image path

    ```
    $ cat test_videocapture_image.bat
    @set sDataPath=..\..\..\..\..\Data
    @set sDataTestPath=..\..\..\..\..\DataTest\comm
    LandmarkDetectTest.exe %sDataPath%\49New.bin -v %sDataTestPath%\voiceofchina.avi
    ```
      * `sDataPath` it is binary model directory
      * `-v` input video path
3. Double click test_input_camera.bat, test_input_image.bat or test_videocapture_image.bat

<h2 id="How_to_Linux">How to run LandmarkDetect Demo on Linux</h2>
1. Enter `LandmarkDetect/bin` directory on terminal
2. Check script and update argument ,like [on Windows](#How_to)
2. run test_input_camera.sh, test_input_image.sh or test_videocapture_image.sh
```
$ ./test_input_camera.sh
$ ./test_input_image.sh
$ ./test_videocapture_image.sh
```
