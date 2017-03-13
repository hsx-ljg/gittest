# FaceDetect APIs Documentation

#### Table of Contents
* [About FaceDetect](#About_FaceDetect)
* [Interface Design](#Interface_Design)
   * [HPFaceDetectorWarpper](#HPFaceDetectorWarpper)
      * [Init](#Init)
      * [DetectFaces](#DetectFaces)
* [How to use FaceDetect Library on Windows](#How_to_use)
* [How to run FaceDetect Demo](#How_to)

<h2 id="About_FaceDetect" >About FaceDetect</h2>
FaceDetect can detect faces from camera, video or image. the output is the boundbox of faces.

<h2 id="Interface_Design" >Interface Design</h2>
HPFaceDetectorWarpper is a class which provide Init and DetectFaces functions.

* <span id="HPFaceDetectorWarpper"> HPFaceDetectorWarpper constructor</span>  
construct HPFaceDetectorWarpper
```C++
HPFaceDetectorWarpper::HPFaceDetectorWarpper(bool bMode = true);
```
   * `bMode` if true,will Init with video mode, if false, Init with normal mode,default true


* <span id="Init"> Init</span>  
Init HPFaceDetectorWarpper
```C++
int HPFaceDetectorWarpper::Init(bool bHalfProfile = true, bool bProfile = false, bool bRot = true)
```
   * `bHalfProfile` if true,will xxxx, if false, xxx , default true
   * `bProfile` if true,will xxxx, if false, xxx , default false
   * `bRot` if true,will xxxx, if false, xxx , default false
   * `return value` if 0 succeed, else failed

* <span id="DetectFaces"> DetectFaces</span>   
Begin to detect faces
```C++
int DetectFaces(unsigned char* ucImgData, const int nImgWidth, const int nImgHeight, FaceArray& faceArray)
```
   * `ucImgData` image buffer,it is from `cv::Mat`
   * `nImgWidth` image's width
   * `nImgHeight` image's height
   * `faceArray` output face information array

<h2 id="How_to_use">How to use FaceDetect Library on Windows</h2>
1. In `Visual Studio 2015`, create a empty project
2. Configure project build mode as `X64` `Release`
3. If use `cv::Mat`,import OpenCV firstly
4. Configure include path ,Configuration Page -> C/C++ -> Additional Include Path -> `FaceDetect\src`
5. Configure dependency Library ,Configuration Page ->Linker -> Input -> Additional dependency -> `FaceDetect.lib`
6. Configure dependency Library directory ,Configuration Page ->Linker -> General -> Additional dependency directory-> `..\lib\x64`

<h2 id="How_to">How to run FaceDetect Demo</h2>
1. Enter `FaceDetect\bin\x64\Release` directory
2. Double click test.bat or FaceDetectTest.exe
